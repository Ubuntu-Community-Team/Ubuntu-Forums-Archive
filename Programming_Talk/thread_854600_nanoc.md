---
title: "nanoc"
date: 2008-07-09
forum: Programming Talk
---

### Post by AnLGP on 2008-07-09
hello,

in conjunction with me starting to learn Ruby I found out about "nanoc".  I got all the way through the tutorial

[http://nanoc.stoneship.org/help/tutorial/](http://nanoc.stoneship.org/help/tutorial/)

but must have done something to produce these errors on my localhost:3000


500 Server Error

An error occurred while compiling the page you requested, /.

If you think this is a bug in nanoc, please do report it&#8212;thanks!

Message:

    Input/output error

Backtrace:

   1. /var/lib/gems/1.8/gems/nanoc-2.0.4/bin/../lib/nanoc/base/enhancements.rb:9:in `write'
   2. /var/lib/gems/1.8/gems/nanoc-2.0.4/bin/../lib/nanoc/base/enhancements.rb:9:in `puts'
   3. /var/lib/gems/1.8/gems/nanoc-2.0.4/bin/../lib/nanoc/base/enhancements.rb:9:in `log'
   4. /var/lib/gems/1.8/gems/nanoc-2.0.4/bin/../lib/nanoc/base/compiler.rb:12:in `run'
   5. /var/lib/gems/1.8/gems/nanoc-2.0.4/bin/../lib/nanoc/base/auto_compiler.rb:115:in `serve_page'
   6. /var/lib/gems/1.8/gems/nanoc-2.0.4/bin/../lib/nanoc/base/auto_compiler.rb:86:in `handle_request'
   7. /var/lib/gems/1.8/gems/nanoc-2.0.4/bin/../lib/nanoc/base/auto_compiler.rb:62:in `start'
   8. /usr/lib/ruby/1.8/webrick/httpservlet/prochandler.rb:26:in `call'
   9. /usr/lib/ruby/1.8/webrick/httpservlet/prochandler.rb:26:in `do_GET'
  10. /usr/lib/ruby/1.8/webrick/httpservlet/abstract.rb:35:in `__send__'
  11. /usr/lib/ruby/1.8/webrick/httpservlet/abstract.rb:35:in `service'
  12. /usr/lib/ruby/1.8/webrick/httpserver.rb:104:in `service'
  13. /usr/lib/ruby/1.8/webrick/httpserver.rb:65:in `run'
  14. /usr/lib/ruby/1.8/webrick/server.rb:173:in `start_thread'
  15. /usr/lib/ruby/1.8/webrick/server.rb:162:in `start'
  16. /usr/lib/ruby/1.8/webrick/server.rb:162:in `start_thread'
  17. /usr/lib/ruby/1.8/webrick/server.rb:95:in `start'
  18. /usr/lib/ruby/1.8/webrick/server.rb:92:in `each'
  19. /usr/lib/ruby/1.8/webrick/server.rb:92:in `start'
  20. /usr/lib/ruby/1.8/webrick/server.rb:23:in `start'
  21. /usr/lib/ruby/1.8/webrick/server.rb:82:in `start'
  22. /var/lib/gems/1.8/gems/nanoc-2.0.4/bin/../lib/nanoc/base/auto_compiler.rb:66:in `start'
  23. /var/lib/gems/1.8/gems/nanoc-2.0.4/bin/../lib/nanoc/base/site.rb:110:in `autocompile'
  24. /var/lib/gems/1.8/gems/nanoc-2.0.4/bin/nanoc:182:in `autocompile_site'
  25. /var/lib/gems/1.8/gems/nanoc-2.0.4/bin/nanoc:189

-

Can anyone help me fix it please?

---

### Post by AnLGP on 2008-07-09
I was going to just upload nanoc to this:

[http://musicauniversalis.budreausquared.net/steve/](http://musicauniversalis.budreausquared.net/steve/)

but I don't think it worked.  That is, I don't think it's nanoc.  Which files would I upload?  All the folders (ex nanoc_site) or just the ones in output?

---

