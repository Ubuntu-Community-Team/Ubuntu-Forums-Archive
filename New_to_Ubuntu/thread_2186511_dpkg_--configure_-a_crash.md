---
title: "dpkg --configure -a crash"
date: 2013-11-07
forum: New to Ubuntu
---

### Post by spamthis1 on 2013-11-07
When I try to open synaptic or try 'apt-get upgrade' I get an error, "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

When I use that command, it runs fine until it gets to a process called something like, "...Sanity Check" then crashes.  The pic is what I get after the crash.
 
'apt-get -update works fine.'

[ATTACH=CONFIG]247653[/ATTACH]

---

### Post by Bashing-om on 2013-11-07
spamthis1; Hi ! Welcome to the forum.

Could be any of a thousands things to cause. Let's see what the package manager points to:
Post back the outputs of terminal commands:
```

sudo apt-get update
sudo apt-get upgrade

```
Place these outputs between code tags to preserve formatting and readability;
 code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

This will be a good place to start troubleshooting,

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

