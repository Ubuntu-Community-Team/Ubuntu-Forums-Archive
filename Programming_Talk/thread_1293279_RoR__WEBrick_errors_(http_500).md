---
title: "RoR / WEBrick errors (http: 500)"
date: 2009-10-16
forum: Programming Talk
---

### Post by aosmith on 2009-10-16
WEBrick boots fine, but whenever i try to pull up a an application (ie: localhost:3000/demo/say/hello) i get a slew of errors:
```
alex@ubuntu-server:~/RoR/demo$ ruby script/server
=> Booting WEBrick
=> Rails 2.3.4 application starting on http://0.0.0.0:3000
=> Call with -d to detach
=> Ctrl-C to shutdown server
[2009-10-16 21:05:48] INFO  WEBrick 1.3.1
[2009-10-16 21:05:48] INFO  ruby 1.8.7 (2008-08-11) [i486-linux]
[2009-10-16 21:05:53] INFO  WEBrick::HTTPServer#start: pid=12439 port=3000
/!\ FAILSAFE /!\  Fri Oct 16 21:06:05 -0500 2009
  Status: 500 Internal Server Error
  no such file to load -- sqlite3
    /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:31:in `gem_original_require'
    /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:31:in `require'
    /usr/lib/ruby/gems/1.8/gems/activesupport-2.3.4/lib/active_support/dependencies.rb:156:in `require'
    /usr/lib/ruby/gems/1.8/gems/activesupport-2.3.4/lib/active_support/dependencies.rb:521:in `new_constants_in'
    /usr/lib/ruby/gems/1.8/gems/activesupport-2.3.4/lib/active_support/dependencies.rb:156:in `require'
    /usr/lib/ruby/gems/1.8/gems/activesupport-2.3.4/lib/active_support/core_ext/kernel/requires.rb:7:in `require_library_or_gem'
    /usr/lib/ruby/gems/1.8/gems/activesupport-2.3.4/lib/active_support/core_ext/kernel/reporting.rb:11:in `silence_warnings'
    /usr/lib/ruby/gems/1.8/gems/activesupport-2.3.4/lib/active_support/core_ext/kernel/requires.rb:5:in `require_library_or_gem'
    /usr/lib/ruby/gems/1.8/gems/activerecord-2.3.4/lib/active_record/connection_adapters/sqlite3_adapter.rb:10:in `sqlite3_connection'
    /usr/lib/ruby/gems/1.8/gems/activerecord-2.3.4/lib/active_record/connection_adapters/abstract/connection_pool.rb:223:in `send'
    /usr/lib/ruby/gems/1.8/gems/activerecord-2.3.4/lib/active_record/connection_adapters/abstract/connection_pool.rb:223:in `new_connection'
    /usr/lib/ruby/gems/1.8/gems/activerecord-2.3.4/lib/active_record/connection_adapters/abstract/connection_pool.rb:245:in `checkout_new_connection'
    /usr/lib/ruby/gems/1.8/gems/activerecord-2.3.4/lib/active_record/connection_adapters/abstract/connection_pool.rb:188:in `checkout'
    /usr/lib/ruby/gems/1.8/gems/activerecord-2.3.4/lib/active_record/connection_adapters/abstract/connection_pool.rb:184:in `loop'
    /usr/lib/ruby/gems/1.8/gems/activerecord-2.3.4/lib/active_record/connection_adapters/abstract/connection_pool.rb:184:in `checkout'
    /usr/lib/ruby/1.8/monitor.rb:242:in `synchronize'
    /usr/lib/ruby/gems/1.8/gems/activerecord-2.3.4/lib/active_record/connection_adapters/abstract/connection_pool.rb:183:in `checkout'
    /usr/lib/ruby/gems/1.8/gems/activerecord-2.3.4/lib/active_record/connection_adapters/abstract/connection_pool.rb:98:in `connection'
    /usr/lib/ruby/gems/1.8/gems/activerecord-2.3.4/lib/active_record/connection_adapters/abstract/connection_pool.rb:326:in `retrieve_connection'
    /usr/lib/ruby/gems/1.8/gems/activerecord-2.3.4/lib/active_record/connection_adapters/abstract/connection_specification.rb:123:in `retrieve_connection'
    /usr/lib/ruby/gems/1.8/gems/activerecord-2.3.4/lib/active_record/connection_adapters/abstract/connection_specification.rb:115:in `connection'
    /usr/lib/ruby/gems/1.8/gems/activerecord-2.3.4/lib/active_record/query_cache.rb:9:in `cache'
    /usr/lib/ruby/gems/1.8/gems/activerecord-2.3.4/lib/active_record/query_cache.rb:28:in `call'
    /usr/lib/ruby/gems/1.8/gems/activerecord-2.3.4/lib/active_record/connection_adapters/abstract/connection_pool.rb:361:in `call'
    /usr/lib/ruby/gems/1.8/gems/rack-1.0.0/lib/rack/head.rb:9:in `call'
    /usr/lib/ruby/gems/1.8/gems/rack-1.0.0/lib/rack/methodoverride.rb:24:in `call'
    /usr/lib/ruby/gems/1.8/gems/actionpack-2.3.4/lib/action_controller/params_parser.rb:15:in `call'
    /usr/lib/ruby/gems/1.8/gems/actionpack-2.3.4/lib/action_controller/session/cookie_store.rb:93:in `call'
    /usr/lib/ruby/gems/1.8/gems/actionpack-2.3.4/lib/action_controller/failsafe.rb:26:in `call'
    /usr/lib/ruby/gems/1.8/gems/rack-1.0.0/lib/rack/lock.rb:11:in `call'
    /usr/lib/ruby/gems/1.8/gems/rack-1.0.0/lib/rack/lock.rb:11:in `synchronize'
    /usr/lib/ruby/gems/1.8/gems/rack-1.0.0/lib/rack/lock.rb:11:in `call'
    /usr/lib/ruby/gems/1.8/gems/actionpack-2.3.4/lib/action_controller/dispatcher.rb:114:in `call'
    /usr/lib/ruby/gems/1.8/gems/actionpack-2.3.4/lib/action_controller/reloader.rb:34:in `run'
    /usr/lib/ruby/gems/1.8/gems/actionpack-2.3.4/lib/action_controller/dispatcher.rb:108:in `call'
    /usr/lib/ruby/gems/1.8/gems/rails-2.3.4/lib/rails/rack/static.rb:31:in `call'
    /usr/lib/ruby/gems/1.8/gems/rack-1.0.0/lib/rack/urlmap.rb:46:in `call'
    /usr/lib/ruby/gems/1.8/gems/rack-1.0.0/lib/rack/urlmap.rb:40:in `each'
    /usr/lib/ruby/gems/1.8/gems/rack-1.0.0/lib/rack/urlmap.rb:40:in `call'
    /usr/lib/ruby/gems/1.8/gems/rails-2.3.4/lib/rails/rack/log_tailer.rb:17:in `call'
    /usr/lib/ruby/gems/1.8/gems/rack-1.0.0/lib/rack/content_length.rb:13:in `call'
    /usr/lib/ruby/gems/1.8/gems/rack-1.0.0/lib/rack/handler/webrick.rb:46:in `service'
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
    /usr/lib/ruby/gems/1.8/gems/rack-1.0.0/lib/rack/handler/webrick.rb:13:in `run'
    /usr/lib/ruby/gems/1.8/gems/rails-2.3.4/lib/commands/server.rb:111
    /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:31:in `gem_original_require'
    /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:31:in `require'
    script/server:3

```

any ideas?

---

### Post by crush304 on 2009-10-16
**no such file to load -- sqlite3**

probably need to install ruby sqlite3 libs

might be libsqlite3-ruby

---

