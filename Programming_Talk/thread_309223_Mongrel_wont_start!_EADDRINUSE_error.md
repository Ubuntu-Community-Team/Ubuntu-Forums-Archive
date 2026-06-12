---
title: "Mongrel wont start! EADDRINUSE error"
date: 2006-11-29
forum: Programming Talk
---

### Post by adam_pretty on 2006-11-29
After booting up today, after doing some updates (cant remember what) seems that Mongrel is not happy - when starting it I get this error.

```
** Starting Mongrel listening at 0.0.0.0:3000
/usr/lib/ruby/gems/1.8/gems/mongrel-0.3.13.4/lib/mongrel/tcphack.rb:12:in `initialize_without_backlog': Address already in use - bind(2) (Errno::EADDRINUSE)

```

Searched around for it but the only info I can find is from someone on OSX who had problems with mongrel processes not terminating properly. This doesn't seem to be the case here, have used ```
sudo ps -ax |more

``` to check which processes are running.

Any tips much appreciated! 

Thanks
Adam.

---

### Post by adam_pretty on 2006-11-29
OK - shame on me
lighttpd was still running!! :oops: 

:roll:

---

