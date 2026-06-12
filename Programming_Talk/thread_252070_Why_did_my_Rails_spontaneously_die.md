---
title: "Why did my Rails spontaneously die?"
date: 2006-09-06
forum: Programming Talk
---

### Post by meatbites on 2006-09-06
I am using Ubuntu 6.06 LTS.

Basically, I had Rails working just swimmingly a few weeks ago. Then the infamous security scare came, along with a patch, and I can no longer use Rails.

Suffice it to say, I can't seem to fix this problem. I have repeatedly removed and newly installed the ruby and rails suite, yet I'm getting nowhere.

I am only just coming out from learning Ruby though, so by 'use Rails' I mean I clicked on the 'About your application's environment' link on a newly generated scaffolding(?) -- i.e.: rails generate/new/site/here. Regardless of how I have set up Rails -- even on a clean install of Dapper -- this link returns an error when I access it via localhost:3000.

Dare I say it -- is this link now not supposed to function? I have not done anything different on my system, other than install the updates as they come down.

When run in super user mode (su ruby path/to/script/server):
```

Routing Error

Recognition failed for "/rails/info/properties"
```

Ordinary user:
```

Application error

Change this error message for exceptions thrown outside of an action (like in Dispatcher setups or broken Ruby code) in public/500.html

```

All permissions look fine, as far as I can tell. I did have it running fine with Apache, however I am using WEBrick to try and bring it back up.

Speaking of which, in the console it just throws a 404 error in SU mode:
```
su ruby /var/www/dev/test/script/server
=> Booting WEBrick...
=> Rails application started on http://0.0.0.0:3000
=> Ctrl-C to shutdown server; call with --help for options
[2006-09-07 00:45:46] INFO  WEBrick 1.3.1
[2006-09-07 00:45:46] INFO  ruby 1.8.4 (2005-12-24) [i486-linux]
[2006-09-07 00:45:46] INFO  WEBrick::HTTPServer#start: pid=8094 port=3000
127.0.0.1 - - [07/Sep/2006:00:45:49 EST] "GET / HTTP/1.1" 304 0
- -> /
127.0.0.1 - - [07/Sep/2006:00:45:49 EST] "GET /javascripts/prototype.js HTTP/1.1" 304 0
http://localhost:3000/ -> /javascripts/prototype.js
127.0.0.1 - - [07/Sep/2006:00:45:49 EST] "GET /javascripts/effects.js HTTP/1.1" 304 0
http://localhost:3000/ -> /javascripts/effects.js
127.0.0.1 - - [07/Sep/2006:00:45:50 EST] "GET /images/rails.png HTTP/1.1" 304 0
http://localhost:3000/ -> /images/rails.png

## Click ##

127.0.0.1 - - [07/Sep/2006:00:45:51 EST] "GET /rails/info/properties HTTP/1.1" 404 610
- -> /rails/info/properties

```

Or a 500 error when just a standard user:
```
ruby /var/www/dev/test/script/server
=> Booting WEBrick...
=> Rails application started on http://0.0.0.0:3000
=> Ctrl-C to shutdown server; call with --help for options
[2006-09-07 00:44:18] INFO  WEBrick 1.3.1
[2006-09-07 00:44:18] INFO  ruby 1.8.4 (2005-12-24) [i486-linux]
[2006-09-07 00:44:18] INFO  WEBrick::HTTPServer#start: pid=8090 port=3000
127.0.0.1 - - [07/Sep/2006:00:44:21 EST] "GET / HTTP/1.1" 304 0
- -> /
127.0.0.1 - - [07/Sep/2006:00:44:21 EST] "GET /javascripts/prototype.js HTTP/1.1" 304 0
http://localhost:3000/ -> /javascripts/prototype.js
127.0.0.1 - - [07/Sep/2006:00:44:21 EST] "GET /javascripts/effects.js HTTP/1.1" 304 0
http://localhost:3000/ -> /javascripts/effects.js
127.0.0.1 - - [07/Sep/2006:00:44:21 EST] "GET /images/rails.png HTTP/1.1" 304 0
http://localhost:3000/ -> /images/rails.png

## Click ##

127.0.0.1 - - [07/Sep/2006:00:44:23 EST] "GET /rails/info/properties HTTP/1.1" 500 309
- -> /rails/info/properties

```

Thoughts on this sudden error? Any help will be greatly appreciated. Even if I can be pointed to an easy to follow guide on gettings Rails running on Dapper.

---

### Post by meatbites on 2006-09-06
Just as an update, I seem to have been inadvertently running the original scaffolding creation as super user, so here follows the two errors that probably mean a little more (everything created and run as a standard user).

localhost:3000
```
Not Found
`/rails/info/properties' not found.
WEBrick/1.3.1 (Ruby/1.8.4/2005-12-24) at localhost:3000
```

Terminal
```
ruby test/script/server
=> Booting WEBrick...
=> Rails application started on http://0.0.0.0:3000
=> Ctrl-C to shutdown server; call with --help for options
[2006-09-07 01:05:50] INFO  WEBrick 1.3.1
[2006-09-07 01:05:50] INFO  ruby 1.8.4 (2005-12-24) [i486-linux]
[2006-09-07 01:05:50] INFO  WEBrick::HTTPServer#start: pid=8190 port=3000
127.0.0.1 - - [07/Sep/2006:01:05:51 EST] "GET / HTTP/1.1" 304 0
- -> /
127.0.0.1 - - [07/Sep/2006:01:05:51 EST] "GET /javascripts/prototype.js HTTP/1.1" 304 0
http://localhost:3000/ -> /javascripts/prototype.js
127.0.0.1 - - [07/Sep/2006:01:05:51 EST] "GET /javascripts/effects.js HTTP/1.1" 304 0
http://localhost:3000/ -> /javascripts/effects.js
127.0.0.1 - - [07/Sep/2006:01:05:51 EST] "GET /images/rails.png HTTP/1.1" 304 0
http://localhost:3000/ -> /images/rails.png
#<NameError: uninitialized constant Breakpoint>
["./test/script/../config/../vendor/rails/activesupport/lib/active_support/dependencies.rb:123:in `const_missing'", "./test/script/. ./config/../vendor/rails/activesupport/lib/active_support/dependencies.rb:131:in `const_missing'", "./test/script/../config/../vendo r/rails/activesupport/lib/active_support/dependencies.rb:133:in `const_missing'", "./test/script/../config/../vendor/rails/railties/ lib/dispatcher.rb:75:in `reset_after_dispatch'", "./test/script/../config/../vendor/rails/railties/lib/dispatcher.rb:46:in `dispatch '", "./test/script/../config/../vendor/rails/railties/lib/webrick_server.rb:115:in `handle_dispatch'", "./test/script/../config/../v endor/rails/railties/lib/webrick_server.rb:81:in `service'", "/usr/lib/ruby/1.8/webrick/httpserver.rb:104:in `service'", "/usr/lib/r uby/1.8/webrick/httpserver.rb:65:in `run'", "/usr/lib/ruby/1.8/webrick/server.rb:173:in `start_thread'", "/usr/lib/ruby/1.8/webrick/ server.rb:162:in `start_thread'", "/usr/lib/ruby/1.8/webrick/server.rb:95:in `start'", "/usr/lib/ruby/1.8/webrick/server.rb:92:in `s tart'", "/usr/lib/ruby/1.8/webrick/server.rb:23:in `start'", "/usr/lib/ruby/1.8/webrick/server.rb:82:in `start'", "./test/script/../ config/../vendor/rails/railties/lib/webrick_server.rb:67:in `dispatch'", "./test/script/../config/../vendor/rails/railties/lib/comma nds/servers/webrick.rb:59", "/usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'", "./test/script/../config/../v endor/rails/activesupport/lib/active_support/dependencies.rb:147:in `require'", "./test/script/../config/../vendor/rails/railties/li b/commands/server.rb:30", "test/script/server:3"]
[2006-09-07 01:05:53] ERROR `/rails/info/properties' not found.
127.0.0.1 - - [07/Sep/2006:01:05:53 EST] "GET /rails/info/properties HTTP/1.1" 404 291
- -> /rails/info/properties
```

---

