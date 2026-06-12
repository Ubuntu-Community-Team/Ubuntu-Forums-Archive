---
title: "Ruby on Rails with postgres error while loading"
date: 2009-08-10
forum: Programming Talk
---

### Post by brijith on 2009-08-10
Hai All,

I am trying to build a rails application from a legacy database which is in postgres. I could connect rails to me legacy application with out any error.I could access a data in the table through **./script/console **. But when I just created a controller (didn't added a single line of code in any of the generated file ) and tried to access the page like *user/index * i got the following error..

```
 MissingSourceFile in UserController#index

no such file to load -- postgres

RAILS_ROOT: /home/brijith/Desktop/traacs
Application Trace | Framework Trace | Full Trace

/usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:31:in `gem_original_require'
/usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:31:in `require'
vendor/rails/activesupport/lib/active_support/dependencies.rb:496:in `require'
vendor/rails/activesupport/lib/active_support/dependencies.rb:342:in `new_constants_in'
vendor/rails/activesupport/lib/active_support/dependencies.rb:496:in `require'
vendor/rails/activesupport/lib/active_support/core_ext/kernel/requires.rb:7:in `require_library_or_gem'
vendor/rails/activesupport/lib/active_support/core_ext/kernel/reporting.rb:11:in `silence_warnings'
vendor/rails/activesupport/lib/active_support/core_ext/kernel/requires.rb:5:in `require_library_or_gem'
vendor/rails/activerecord/lib/active_record/connection_adapters/postgresql_adapter.rb:7:in `postgresql_connection'
vendor/rails/activerecord/lib/active_record/connection_adapters/abstract/connection_specification.rb:291:in `send'
vendor/rails/activerecord/lib/active_record/connection_adapters/abstract/connection_specification.rb:291:in `connection='
vendor/rails/activerecord/lib/active_record/connection_adapters/abstract/connection_specification.rb:259:in `retrieve_connection'
vendor/rails/activerecord/lib/active_record/connection_adapters/abstract/connection_specification.rb:78:in `connection'
vendor/rails/activerecord/lib/active_record/query_cache.rb:8:in `cache'
vendor/rails/actionpack/lib/action_controller/caching.rb:677:in `perform_action'
vendor/rails/actionpack/lib/action_controller/base.rb:524:in `send'
vendor/rails/actionpack/lib/action_controller/base.rb:524:in `process_without_filters'
vendor/rails/actionpack/lib/action_controller/filters.rb:685:in `process_without_session_management_support'
vendor/rails/actionpack/lib/action_controller/session_management.rb:123:in `process'
vendor/rails/actionpack/lib/action_controller/base.rb:388:in `process'
vendor/rails/actionpack/lib/action_controller/dispatcher.rb:171:in `handle_request'
vendor/rails/actionpack/lib/action_controller/dispatcher.rb:115:in `dispatch'
vendor/rails/actionpack/lib/action_controller/dispatcher.rb:126:in `dispatch_cgi'
vendor/rails/actionpack/lib/action_controller/dispatcher.rb:9:in `dispatch'
vendor/rails/railties/lib/webrick_server.rb:112:in `handle_dispatch'
vendor/rails/railties/lib/webrick_server.rb:78:in `service'
/usr/lib/ruby/1.8/webrick/httpserver.rb:104:in `service'
/usr/lib/ruby/1.8/webrick/httpserver.rb:65:in `run'
/usr/lib/ruby/1.8/webrick/server.rb:173:in `start_thread'
/usr/lib/ruby/1.8/webrick/server.rb:162:in `start'
/usr/lib/ruby/1.8/webrick/server.rb:162:in `start_thread'
/usr/lib/ruby/1.8/webrick/server.rb:95:in `start'
/usr/lib/ruby/1.8/webrick/server.rb:92:in `each'
/usr/lib/ruby/1.8/webrick/server.rb:92:in `start'
/usr/lib/ruby/1.8/webrick/server.rb:23:in `start'
/usr/lib/ruby/1.8/webrick/server.rb:82:in `start'
vendor/rails/railties/lib/webrick_server.rb:62:in `dispatch'
vendor/rails/railties/lib/commands/servers/webrick.rb:66
/usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:31:in `gem_original_require'
/usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:31:in `require'
vendor/rails/activesupport/lib/active_support/dependencies.rb:496:in `require'
vendor/rails/activesupport/lib/active_support/dependencies.rb:342:in `new_constants_in'
vendor/rails/activesupport/lib/active_support/dependencies.rb:496:in `require'
vendor/rails/railties/lib/commands/server.rb:39
script/server:3:in `require'
script/server:3

/usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:31:in `gem_original_require'
/usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:31:in `require'
vendor/rails/activesupport/lib/active_support/dependencies.rb:496:in `require'
vendor/rails/activesupport/lib/active_support/dependencies.rb:342:in `new_constants_in'
vendor/rails/activesupport/lib/active_support/dependencies.rb:496:in `require'
vendor/rails/activesupport/lib/active_support/core_ext/kernel/requires.rb:7:in `require_library_or_gem'
vendor/rails/activesupport/lib/active_support/core_ext/kernel/reporting.rb:11:in `silence_warnings'
vendor/rails/activesupport/lib/active_support/core_ext/kernel/requires.rb:5:in `require_library_or_gem'
vendor/rails/activerecord/lib/active_record/connection_adapters/postgresql_adapter.rb:7:in `postgresql_connection'
vendor/rails/activerecord/lib/active_record/connection_adapters/abstract/connection_specification.rb:291:in `send'
vendor/rails/activerecord/lib/active_record/connection_adapters/abstract/connection_specification.rb:291:in `connection='
vendor/rails/activerecord/lib/active_record/connection_adapters/abstract/connection_specification.rb:259:in `retrieve_connection'
vendor/rails/activerecord/lib/active_record/connection_adapters/abstract/connection_specification.rb:78:in `connection'
vendor/rails/activerecord/lib/active_record/query_cache.rb:8:in `cache'
vendor/rails/actionpack/lib/action_controller/caching.rb:677:in `perform_action'
vendor/rails/actionpack/lib/action_controller/base.rb:524:in `send'
vendor/rails/actionpack/lib/action_controller/base.rb:524:in `process_without_filters'
vendor/rails/actionpack/lib/action_controller/filters.rb:685:in `process_without_session_management_support'
vendor/rails/actionpack/lib/action_controller/session_management.rb:123:in `process'
vendor/rails/actionpack/lib/action_controller/base.rb:388:in `process'
vendor/rails/actionpack/lib/action_controller/dispatcher.rb:171:in `handle_request'
vendor/rails/actionpack/lib/action_controller/dispatcher.rb:115:in `dispatch'
vendor/rails/actionpack/lib/action_controller/dispatcher.rb:126:in `dispatch_cgi'
vendor/rails/actionpack/lib/action_controller/dispatcher.rb:9:in `dispatch'
vendor/rails/railties/lib/webrick_server.rb:112:in `handle_dispatch'
vendor/rails/railties/lib/webrick_server.rb:78:in `service'
/usr/lib/ruby/1.8/webrick/httpserver.rb:104:in `service'
/usr/lib/ruby/1.8/webrick/httpserver.rb:65:in `run'
/usr/lib/ruby/1.8/webrick/server.rb:173:in `start_thread'
/usr/lib/ruby/1.8/webrick/server.rb:162:in `start'
/usr/lib/ruby/1.8/webrick/server.rb:162:in `start_thread'
/usr/lib/ruby/1.8/webrick/server.rb:95:in `start'
/usr/lib/ruby/1.8/webrick/server.rb:92:in `each'
/usr/lib/ruby/1.8/webrick/server.rb:92:in `start'
/usr/lib/ruby/1.8/webrick/server.rb:23:in `start'
/usr/lib/ruby/1.8/webrick/server.rb:82:in `start'
vendor/rails/railties/lib/webrick_server.rb:62:in `dispatch'
vendor/rails/railties/lib/commands/servers/webrick.rb:66
/usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:31:in `gem_original_require'
/usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:31:in `require'
vendor/rails/activesupport/lib/active_support/dependencies.rb:496:in `require'
vendor/rails/activesupport/lib/active_support/dependencies.rb:342:in `new_constants_in'
vendor/rails/activesupport/lib/active_support/dependencies.rb:496:in `require'
vendor/rails/railties/lib/commands/server.rb:39
script/server:3:in `require'
script/server:3

This error occurred while loading the following files:
   postgres

Request

Parameters:

None

Show session dump

--- 
flash: !map:ActionController::Flash::FlashHash {}


Response

Headers:

{"cookie"=>[],
 "Cache-Control"=>"no-cache"}
```

Please help me !!!



please see the attached screen shot

When I googled  with this error message many of them says to install ruby_pg or pg-0.8.0.gem. But I have already installed pg-0.8.0.gem

---

