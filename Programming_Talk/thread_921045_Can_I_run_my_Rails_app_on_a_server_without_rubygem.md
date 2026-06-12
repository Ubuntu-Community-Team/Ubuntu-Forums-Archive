---
title: "Can I run my Rails app on a server without rubygems installed?"
date: 2008-09-15
forum: Programming Talk
---

### Post by stickmangumby on 2008-09-15
I have a bit of an unusual problem. I'm doing a uni project that is required to be able to run on one of the uni servers. I want to use Ruby on Rails instead of Java. The uni servers have Ruby 1.8.7 installed, but they don't have rubygems or rails installed.

I've frozen rails into my /vendor/rails directory using "rake rails:freeze:gems", and uploaded it to the uni server. However, when I try to boot WEBrick using ./script/server I get the following error:

```

[PATH]/vendor/rails/activesupport/lib/active_support/vendor.rb:2:in `require': no such file to load -- rubygems (LoadError)
        from [PATH]/vendor/rails/activesupport/lib/active_support/vendor.rb:2
        from [PATH]/vendor/rails/activesupport/lib/active_support.rb:26:in `require'
        from [PATH]/vendor/rails/activesupport/lib/active_support.rb:26
        from [PATH]/vendor/rails/railties/lib/commands/server.rb:1:in `require'
        from [PATH]/vendor/rails/railties/lib/commands/server.rb:1
        from ./script/server:3:in `require'
        from ./script/server:3

```

Is what I'm trying to do possible? I'm quite new to Rails (and Ruby), so I'm not sure how to go about tackling this problem.

Any feedback is much appreciated! Thanks :)

---

### Post by escapee on 2008-09-15
I know it's a simple and probably obvious answer, but have you asked the system admin to install it?  They're likely not as lax there as our Linux system admin here, but you never know.

---

