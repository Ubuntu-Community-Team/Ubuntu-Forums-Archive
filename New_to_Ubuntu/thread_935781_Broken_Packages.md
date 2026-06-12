---
title: "Broken Packages"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by Anonono on 2008-10-02
About an hour ago I tried to install globalmenu, but it failed. I didn't think it was much, so I just left it. Now the update manager is an error: BrokenCount> 0 . I clicked on it, and it came up with this: 
> Not all updates can be installed. Run a partial upgrade, to install as many updates as possible.
If I do a Partial update, it comes up with this:
> Can't install 'ubuntu-desktop'
It was impossible to install a required package. Please report this as a bug.
HELP!

---

### Post by Bucky Ball on 2008-10-02
Perhaps run:

```
sudo apt-get remove globalmenu
```... or see if it is ticked on in Synaptics and untick it. You could also try running this:

                                       ```
sudo dpkg --configure -a
```
... which will configure packages.

---

### Post by hansdown on 2008-10-02
Hi anonono.

Please read this first.

[http://code.google.com/p/gnome2-globalmenu/wiki/InstallingonUbuntu](http://code.google.com/p/gnome2-globalmenu/wiki/InstallingonUbuntu)

---

### Post by cariboo on 2008-10-02
Did you notice what the page you linked to had at the top?

> THIS IS A DRAFT. DO NOT USE. IT KILLS KITTENS AND COMPUTERS TOO


Is that supposed to mean that you can only use it if your are willing to kill your computer? :)

Jim

---

### Post by Anonono on 2008-10-02
> **hansdown said:**
> Hi anonono.

Please read this first.

[http://code.google.com/p/gnome2-globalmenu/wiki/InstallingonUbuntu](http://code.google.com/p/gnome2-globalmenu/wiki/InstallingonUbuntu)
Oh, I only just saw the comments. And isn't that draft message just a automatic message in Google Code for drafts?

Oh yeah, and I got this from sudo dpkg --configure -a:
> dpkg: dependency problems prevent configuration of gtk2.0-examples:
 gtk2.0-examples depends on libgtk2.0-0 (= 2.12.9-4ubuntu3); however:
  Version of libgtk2.0-0 on system is 2.12.9-3ubuntu4.
dpkg: error processing gtk2.0-examples (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gtk2-engines-pixbuf:
 gtk2-engines-pixbuf depends on libgtk2.0-0 (= 2.12.9-4ubuntu3); however:
  Version of libgtk2.0-0 on system is 2.12.9-3ubuntu4.
dpkg: error processing gtk2-engines-pixbuf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtk2.0-bin:
 libgtk2.0-bin depends on libgtk2.0-0 (>= 2.12.9-4ubuntu3); however:
  Version of libgtk2.0-0 on system is 2.12.9-3ubuntu4.
dpkg: error processing libgtk2.0-bin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gtk2.0-examples
 gtk2-engines-pixbuf
 libgtk2.0-bi
And the first command didn't work.

---

### Post by Ryadt on 2008-10-02
Try```
sudo apt-get install -f
```

---

### Post by rybaxs on 2008-10-02
help! every command i've input gives me a result like this..

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up postgresql-8.3 (8.3.3-0ubuntu0.8.04) ...
 * Starting PostgreSQL 8.3 database server                                       * pg_controldata: could not open file "/var/lib/postgresql/8.3/main/global/pg_control" for reading: Permission denied
Error: Could not parse locale out of pg_controldata output
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.3, action "start" failed.
dpkg: error processing postgresql-8.3 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of postgresql:
 postgresql depends on postgresql-8.3; however:
  Package postgresql-8.3 is not configured yet.
dpkg: error processing postgresql (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 postgresql-8.3
 postgresql
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by Anonono on 2008-10-02
> **Ryadt said:**
> Try```
sudo apt-get install -f
```
It says it's going to remove the package 'ubuntu-desktop'. Isn't that an important file?

---

### Post by Ryadt on 2008-10-02
> **Anonono said:**
> It says it's going to remove the package 'ubuntu-desktop'. Isn't that an important file?

It is the ubuntu desktop. It should install it back. If not just do```
sudo apt-get install ubuntu-desktop
```

---

### Post by Anonono on 2008-10-02
Okay, thanks. It's working now.

---

### Post by Ryadt on 2008-10-02
> **Anonono said:**
> Okay, thanks. It's working now.
Great.
Can you mark it as solved plz.

---

