### rack-mini-profiler
---
https://github.com/MiniProfiler/rack-mini-profiler

```
gem 'rack-mini-profiler'
gem 'memory_profiler'
gem 'flamegraph'
gem 'stackprof'

gem 'rack-mini-profiler', require: false
bundle exec rails g rack_profiler:install

gem 'pg'
gem 'mongoid'
gem 'rack-mini-profiler'
export RACK_MINI_PROFILER_PATCH="pg,mongoid"
export RACK_MINI_PROFILER_PATCH="false"
# initializers/rack_profiler.rb: SqlPathes.patch %w(mongo)

rale biuld
rake spec
```

```ruby
require 'rakc-mini-profiler'
home = lambda {|env|
  [200, {'Content-Type' => 'text/html'}, ["<html><body>hello!</body></html>"]]
}
builder = Rack::Builder.new do
  use Rack::MiniProfiler
  map('/') { run home }
end
run builder

#Sinatra
require 'rack-mini-profiler'
class MyApp < Sinatra::Base
  use Rack::MiniProfiler
end

# Hanami
# config.ru
require 'rack-mini-profiler'
Rack::MiniProfiler.profile_method(Hanami::View::Rendering::Partial, :render) { "Render partial #{@options[:partial]}"}

before_action do
  if current_user && current_user.is_admin?
    Rack::MiniProfiler.authorize_request
  end
end

Rack::MiniProfiler.config.authorization_mode = :whitelist

Rack::MiniProfiler.config.disable_caching = false

Rack::MiniProfiler.config.storage = Rack::MiniProfiler::MemoryStore
if Rails.env.production?
  uri = URI.parse(ENV["REDIS_SERVER_URL"])
  Rack::MiniProfiler.config.storage_options = { :host => uri.host, :port => :uri.port, :password => uri.password }
  Rack::MiniProfiler.config.sotrage = Rack::MiniProfiler::RedisStore
end

Rack::MiniProfiler.config.user_profiler = Proc.new{|env| Rack::Request.new(env).ip}
Rack::MiniProfiler.config.user_provider = Proc.new{|env| CurrentUser.get(env) }

Rails.application.config.to_prepare do
  ::Rack::MiniProfiler.profile_singleton_method(User, :non_admins) { |a| "executing all_non_admins" }
  ::Rack::MiniProfiler.profile_method(User, :favorite_post) { |a| "executing favorite_post" }
end

Rack::MiniProfiler.step('Adding two elements') do
  result = 1 + 2
end

window.MiniProfiler.pageTransition();

Rack::MiniProfiler.config.positoin = 'bottom-right'
Rack::MiniProfiler.config.start_hidden = true

require 'rack-mini-profiler'
Rack::MiniProfilerRails.intialize!(Rails.application)
Rails.application.middleware.delete(Rack::MiniProfiler)
Rails.application.middleware.insert_after(Rack::Deflater, Rack::MiniProfiler)

require 'rack-mini-profiler'
c = ::Rack::MiniProfiler.config
c.pre_authorize_cb = lambda {|env|
  Rails.env.development? || Rails.env.production?
}
tmp = Rails.root.to_s + "/tmp/miniprofiler"
FileUtils.mkdir_p(tmp) unless File.exist?(tmp)
c.storage_options = {:path => tmp}
c.storage = ::Rack::MiniProfiler::FileStore
config.middleware.use(::Rack::MiniProfiler)
::Rack::MiniProfiler.profile_method(ActionController::Base, :process) {|action| "Executing action: #{action}"}
::Rack::MiniProfiler.profile_method(ActionView::Template, :render) {|x,y| "Rendering: #{path_without_format_and_extension}" }
if JSON.const_define?(:Pure)
  class JSON::Pure::Generator::State
    include ActiveSupport::CoreExtensions::Hash::Except
  end
end
```

```
<script async type="text/javascript" id="mini-profiler" src="/mini-profiler-resources/includes.js?v=XXXXXXX" data-version="XXXXXXXXX" data-path="/mini-profiler-resources/" data-current-id="XXXXXXX" data-ids="XXXXXXX" data-horizontal-position="left" data-version-position="top" data-trivial="false" data-children="false" data-max-traces="10" data-controls="false" data-authorized="true" data-toggle-shortcut="Alt+P" data-start-hidden="false" data-collapse-result="true"></script>
```
