---
title: "DBD::mysql problems"
date: 2007-02-23
forum: Programming Talk
---

### Post by Yoeri on 2007-02-23
Hi,

I am upgrading my bugzilla installation to the latest development version (2.23.4). The installscript has DBD::mysql  version 3.0006 blacklisted. Is there a way to install a newer version of the module?

When I try to remove the module via the synaptic package manager, it also removes MySQL Client 5 and MySQL server 5... I'm really stuck here...:confused: 

Thanks

---

### Post by edmicman on 2007-03-23
Did you ever resolve this?  I'm running into the same problem.

---

### Post by Yoeri on 2007-03-25
Jep,

Very weird problem though. I tried again via apt-get and all of a sudden it just worked (after a few reboots). I almost gave up on it ...

Probably not much of a help for you ... hope you have the same miracle as I had :wink:

---

### Post by edmicman on 2007-03-25
What's the apt-get package to install it?  I think I got it working, but I think I ended up having to go into the directory that CPAN downloaded things, and do a make install from there.  I *think* that's what I did.  I dunno...I kepts trying things until it worked.  Sigh....

I guess if you throw enough sh*t at a wall, something is bound to stick...

---

### Post by Vinic0com on 2007-03-29
oops, tried deleting my off base reply with no luck... sorry for waisting time and bandwidth.

---

