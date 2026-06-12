---
title: "Struggling with apt-get"
date: 2013-03-28
forum: New to Ubuntu
---

### Post by usernamer on 2013-03-28
Okay, I want to get a package so I can use the header ncurses when programming in c.
I looked into it, and I need to get the package libncurses5-dev.

I load the terminal and typed: 'sudo apt-cache search libncurses5-dev', then, sure enough, it's there (output is: libncurses5-dev - developer's libraries for ncurses).
I then tried 'sudo apt-get libncurses5-dev', but to no avail. It gives an output of: E: Invalid operation libncurses5-dev
This seems like I'm probably making a very basic error, but I'm not seeing it.

Any help would be appreciated.

---

### Post by westie457 on 2013-03-28
```
sudo apt-get install [COLOR=#000000]libncurses5-dev
``` should install the package for you and possibly drag in any dependencies.[/COLOR]

---

### Post by slickymaster on 2013-03-28
You can always get the package directly from UbuntuUpdates.org.

Here's the link for the [download]("http://security.ubuntu.com/ubuntu/pool/main/n/ncurses/libncurses5-dev_5.7+20101128-1_i386.deb").
And the[ APT-INSTALL]("http://apt:libncurses5-dev") link.

---

