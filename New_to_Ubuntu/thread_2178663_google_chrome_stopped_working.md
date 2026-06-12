---
title: "google chrome stopped working"
date: 2013-10-04
forum: New to Ubuntu
---

### Post by mellery on 2013-10-04
Google chrome stopped working today and I don't know why.  When I run it from the command line it says the following

[2473:2506:1004/134230:FATAL:nss_util.cc(396)] NSS_VersionCheck("3.14.3") failed. NSS >= 3.14.3 is required. Please upgrade to the latest NSS, and if you still get this error, contact your distribution maintainer.
Aborted (core dumped)

synaptic says installed version is google-chrome-stable 30.0.1599.66-1

How can I fix it?

---

### Post by Frogs Hair on 2013-10-04
This is the second post about this problem today and I am curious about your Ubuntu version . I had an update to 30 on Tuesday but have no problems on 13.04.

---

### Post by mellery on 2013-10-04
I'm also on 13.04, everythings up to date.  Do you have a link to the other post?  I searched but couldn't find anything

---

### Post by Frogs Hair on 2013-10-04
This is an add-on to an old thread and there has been little activity. 

[http://ubuntuforums.org/showthread.php?t=2099377&page=2&p=12807268#post12807268](http://ubuntuforums.org/showthread.php?t=2099377&page=2&p=12807268#post12807268)

---

### Post by deadflowr on 2013-10-04
Your version of libnss3 seems to be borked or missing.
Try installing or reinstalling it.

```
sudo apt-get update && sudo apt-get install libnss3
```
or
```
sudo apt-get install --reinstall libnss3
```

See if that helps.
If not it a may be a problem with the version on raring(doubtful)
Chrome for me works on precise and saucy fine, both current stable [COLOR=#303942][FONT=Ubuntu]Version 30.0.1599.66.


[/FONT][/COLOR]

---

