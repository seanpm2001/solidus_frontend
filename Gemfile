# frozen_string_literal: true

source 'https://rubygems.org'
git_source(:github) { |repo| "https://github.com/#{repo}.git" }

gemspec require: false

branch = ENV.fetch('SOLIDUS_BRANCH', 'master')
gem 'solidus_api', github: 'solidusio/solidus', glob: '**/*.gemspec', branch: branch
gem 'solidus_core', github: 'solidusio/solidus', glob: '**/*.gemspec', branch: branch

# Needed to help Bundler figure out how to resolve dependencies,
# otherwise it takes forever to resolve them.
# See https://github.com/bundler/bundler/issues/6677
gem 'rails', '>0.a'

# Temporarily locking sprockets to v3.x
# see https://github.com/solidusio/solidus/issues/3374
# and https://github.com/rails/sprockets-rails/issues/369
gem 'sprockets', '~> 3'

case ENV['DB']
when 'mysql'
  gem 'mysql2'
when 'postgresql'
  gem 'pg'
else
  gem 'sqlite3'
end

gem 'database_cleaner', '~> 1.3', require: false
gem 'rspec-activemodel-mocks', '~> 1.1', require: false
gem 'rspec-rails', '~> 4.0.1', require: false
gem 'simplecov', require: false
gem 'rails-controller-testing', require: false
gem 'puma', require: false

# Ensure the requirement is also updated in core/lib/spree/testing_support/factory_bot.rb
gem 'factory_bot_rails', '>= 4.8', require: false

gem 'capybara', '~> 3.13', require: false
gem 'capybara-screenshot', '>= 1.0.18', require: false
gem 'selenium-webdriver', require: false
gem 'webdrivers', require: false

gem 'generator_spec'

group :utils do
  gem 'pry'
  gem 'launchy', require: false
  gem 'i18n-tasks', '~> 0.9', require: false
  gem 'rubocop', '~> 0.75.0', require: false
  gem 'rubocop-performance', '~> 1.4', require: false
  gem 'rubocop-rails', '~> 2.3', require: false
  gem 'gem-release', require: false
end

gem 'rspec_junit_formatter', require: false, group: :ci

# Documentation
gem 'yard', require: false, group: :docs

custom_gemfile = File.expand_path('Gemfile-custom', __dir__)
eval File.read(custom_gemfile), nil, custom_gemfile, 0 if File.exist?(custom_gemfile)
