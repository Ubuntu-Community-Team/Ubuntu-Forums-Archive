---
title: "how to uninstall web server?"
date: 2010-08-06
forum: Programming Talk
---

### Post by 007casper on 2010-08-06
I am trying to launch an application in ruby.  I have installed passenger, nginx, and rails.  When I tried to launch the application.  It gives me this error

> => Booting WEBrick
=> Rails 2.3.8 application starting on [http://0.0.0.0:3000](http://0.0.0.0:3000)
=> Call with -d to detach
=> Ctrl-C to shutdown server
[2010-08-06 11:41:20] INFO  WEBrick 1.3.1
[2010-08-06 11:41:20] INFO  ruby 1.8.7 (2010-01-10) [i486-linux]
[2010-08-06 11:41:20] WARN  TCPServer Error: Address already in use - bind(2)
Exiting
/usr/lib/ruby/1.8/webrick/utils.rb:73:in `initialize': Address already in use - bind(2) (Errno::EADDRINUSE)
        from /usr/lib/ruby/1.8/webrick/utils.rb:73:in `new'
        from /usr/lib/ruby/1.8/webrick/utils.rb:73:in `create_listeners'
        from /usr/lib/ruby/1.8/webrick/utils.rb:70:in `each'
        from /usr/lib/ruby/1.8/webrick/utils.rb:70:in `create_listeners'
        from /usr/lib/ruby/1.8/webrick/server.rb:75:in `listen'
        from /usr/lib/ruby/1.8/webrick/server.rb:63:in `initialize'
        from /usr/lib/ruby/1.8/webrick/httpserver.rb:24:in `initialize'
        from /var/lib/gems/1.8/gems/rack-1.1.0/lib/rack/handler/webrick.rb:10:in `new'
        from /var/lib/gems/1.8/gems/rack-1.1.0/lib/rack/handler/webrick.rb:10:in `run'
        from /root/.gems/gems/rails-2.3.8/lib/commands/server.rb:111
        from /root/lib/rubygems/custom_require.rb:31:in `gem_original_require'
        from /root/lib/rubygems/custom_require.rb:31:in `require'
        from script/server:3


how can I get rid of webrick?  How do I uninstall it from /usr/lib/ruby/1.8 and make the application to go with passenger nginx set up.

thank you.

---

### Post by jdonnell on 2010-08-21
you don't need to get rid of it, you need to start your web app differently.

---

### Post by dv3500ea on 2010-08-22
WEBrick is part of the ruby standard library, so you can't uninstall it without uninstalling ruby.

Your problem is that there is already a web server running on port 3000.

I'm not sure if this is possible in rails because I've never used it, but to solve your problem, choose a different port number for your server.

also, I don't know what the IP address 0.0.0.0 is. If you can, change this to 127.0.0.1 (localhost).

---

