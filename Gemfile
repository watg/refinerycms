source 'https://rubygems.org'

gemspec

# Add i18n support.
gem 'refinerycms-i18n', '~> 2.1.0.dev', github: 'refinery/refinerycms-i18n'

gem 'protected_attributes'
gem 'seo_meta', github: 'parndt/seo_meta', branch: 'master'

# Fixes uniqueness constraint on translated columns.
# See: https://github.com/svenfuchs/globalize3/pull/121
gem 'globalize3', github: 'svenfuchs/globalize3'
gem 'paper_trail', github: 'parndt/paper_trail', branch: 'rails4'
gem 'awesome_nested_set', github: 'collectiveidea/awesome_nested_set', branch: 'rails4'
gem 'orm_adapter', github: 'ugisozols/orm_adapter', branch: 'rails4'
gem 'database_cleaner', github: "ugisozols/database_cleaner", branch: 'rails4'
gem 'routing-filter', github: "svenfuchs/routing-filter"
gem 'friendly_id', github: "FriendlyId/friendly_id", branch: 'rails4'
gem 'rails-observers'
gem 'actionpack-page_caching'

# Add support for refinerycms-acts-as-indexed
gem 'refinerycms-acts-as-indexed', :git => 'git://github.com/refinery/refinerycms-acts-as-indexed.git'

gem 'quiet_assets', :group => :development

# Database Configuration
unless ENV['TRAVIS']
  gem 'activerecord-jdbcsqlite3-adapter', platform: :jruby
  gem 'sqlite3', platform: :ruby
end

if !ENV['TRAVIS'] || ENV['DB'] == 'mysql'
  gem 'activerecord-jdbcmysql-adapter', :platform => :jruby
  gem 'jdbc-mysql', '= 5.1.13', :platform => :jruby
  gem 'mysql2', :platform => :ruby
end

if !ENV['TRAVIS'] || ENV['DB'] == 'postgresql'
  gem 'activerecord-jdbcpostgresql-adapter', :platform => :jruby
  gem 'pg', :platform => :ruby
end

gem 'jruby-openssl', platform: :jruby

group :test do
  gem 'refinerycms-testing', '~> 2.1.0.dev'
  gem 'generator_spec', '~> 0.9'

  platforms :mswin, :mingw do
    gem 'win32console', '~> 1.3.0'
    gem 'rb-fchange', '~> 0.0.5'
    gem 'rb-notifu', '~> 0.0.4'
  end

  platforms :ruby do
    unless ENV['TRAVIS']
      require 'rbconfig'
      if /darwin/i === RbConfig::CONFIG['target_os']
        gem 'rb-fsevent', '~> 0.9.0'
        gem 'ruby_gntp', '~> 0.3.4'
      end
      if /linux/i === RbConfig::CONFIG['target_os']
        gem 'rb-inotify', '~> 0.8.8'
        gem 'libnotify',  '~> 0.7.2'
        gem 'therubyracer', '~> 0.10.0'
      end
    end
  end

  platforms :jruby do
    unless ENV['TRAVIS']
      require 'rbconfig'
      if /darwin/i === RbConfig::CONFIG['target_os']
        gem 'ruby_gntp', '~> 0.3.4'
      end
      if /linux/i === RbConfig::CONFIG['target_os']
        gem 'rb-inotify', '~> 0.8.8'
        gem 'libnotify',  '~> 0.7.2'
      end
    end
  end
end

# Gems used only for assets and not required
# in production environments by default.
group :assets do
  gem 'sass-rails', '4.0.0'
  gem 'coffee-rails', '4.0.0'
  gem 'uglifier', '>= 1.0.3', require: false
end

gem 'jquery-rails', '~> 2.0.0'

# To use debugger
# gem 'ruby-debug', platform: :mri_18
# or in 1.9.x:
# gem 'debugger', :platform => :mri_19

# For Heroku/s3:
# gem 'fog'

# Bundle edge Rails instead:
gem 'rails', '~> 4.0.0'

# gem 'rack', github: 'rack/rack'
# gem 'arel', github: 'rails/arel'

# Load local gems according to Refinery developer preference.
if File.exist? local_gemfile = File.expand_path('../.gemfile', __FILE__)
  eval File.read(local_gemfile)
end
