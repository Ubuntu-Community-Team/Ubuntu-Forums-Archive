---
title: "Ruby missing headers, can't compile extensions"
date: 2007-09-28
forum: Programming Talk
---

### Post by billmcn on 2007-09-28
I have Ruby installed.  I want to install the hpricot Ruby gem.  hpricot has extensions written in C.  I did an apt-get install on ruby1.8-dev (because hpricot requires mkmf, which is in ruby1.8-dev).  I then tried to do a gem install hpricot with the following results:

> 
/usr/lib/ruby/1.8/i486-linux/ruby.h:31:21: error: stdlib.h: No such file or directory
/usr/lib/ruby/1.8/i486-linux/ruby.h:35:21: error: string.h: No such file or directory
/usr/lib/ruby/1.8/i486-linux/ruby.h:45:19: error: stdio.h: No such file or directory
/usr/lib/ruby/1.8/i486-linux/ruby.h:67:20: error: alloca.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from /usr/lib/ruby/1.8/i486-linux/ruby.h:87,
                 from ext/hpricot_scan/hpricot_scan.rl:9:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
In file included from /usr/lib/ruby/1.8/i486-linux/ruby.h:698,
                 from ext/hpricot_scan/hpricot_scan.rl:9:
/usr/lib/ruby/1.8/i486-linux/missing.h:16:24: error: sys/time.h: No such file or directory
/usr/lib/ruby/1.8/i486-linux/missing.h:25:25: error: sys/types.h: No such file or directory
...


And so forth.  Afterwards, I have a non-functional hpricot install.

The issue appears to be that a bunch of core header files are missing from /usr/lib/ruby/1.8/i486-linux.  I haven't tried to install any other Ruby gems with C extensions on this machine, but I imagine I'll hit the same problem.

I'm stuck.  Is there some other package I have to install to get Ruby C headers on my machine?

Thanks.

Ubuntu 7.04, Ruby 1.8.5.

---

### Post by mssever on 2007-09-28
I'm no C programmer, but those error messages make me wonder if you're missing the C stdlib. Do you have build-essential installed?

---

### Post by billmcn on 2007-10-01
"apt-get install build-essential" fixed the problem.  Thanks.

---

