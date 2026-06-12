---
title: "Running WEBrick with newly installed Rails"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by DaWeasel on 2008-04-23
hey, 
I just installed Rails and was just booting the WEBrick server with

```
$ruby script/server
```

and I get this:

```

=> Booting WEBrick...
/usr/lib/ruby/gems/1.8/gems/rails-2.0.2/lib/initializer.rb:159:in `require_frameworks': no such file to load -- openssl (RuntimeError)
        from /usr/lib/ruby/gems/1.8/gems/rails-2.0.2/lib/initializer.rb:88:in `process'
        from /usr/lib/ruby/gems/1.8/gems/rails-2.0.2/lib/initializer.rb:49:in `run'
        from /home/weasel/RubyonRails/demo/config/environment.rb:13
        from /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'
        from /usr/lib/ruby/gems/1.8/gems/activesupport-2.0.2/lib/active_support/dependencies.rb:496:in `require'
        from /usr/lib/ruby/gems/1.8/gems/activesupport-2.0.2/lib/active_support/dependencies.rb:342:in `new_constants_in'
        from /usr/lib/ruby/gems/1.8/gems/activesupport-2.0.2/lib/active_support/dependencies.rb:496:in `require'
        from /usr/lib/ruby/gems/1.8/gems/rails-2.0.2/lib/commands/servers/webrick.rb:59
        from /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'
        from /usr/lib/ruby/gems/1.8/gems/activesupport-2.0.2/lib/active_support/dependencies.rb:496:in `require'
        from /usr/lib/ruby/gems/1.8/gems/activesupport-2.0.2/lib/active_support/dependencies.rb:342:in `new_constants_in'
        from /usr/lib/ruby/gems/1.8/gems/activesupport-2.0.2/lib/active_support/dependencies.rb:496:in `require'
        from /usr/lib/ruby/gems/1.8/gems/rails-2.0.2/lib/commands/server.rb:39
        from /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'
        from script/server:3

```

Any ideas?

---

### Post by philphil on 2008-04-26
[http://www.ruby-forum.com/topic/136893](http://www.ruby-forum.com/topic/136893)

this thread may help (if you've not fixed it already)

---

