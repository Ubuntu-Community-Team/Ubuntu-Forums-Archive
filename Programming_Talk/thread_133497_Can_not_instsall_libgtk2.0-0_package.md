---
title: "Can not instsall libgtk2.0-0 package"
date: 2006-02-20
forum: Programming Talk
---

### Post by metaosp on 2006-02-20
I tried to install libgtk2.0-dev package but with no luck:

[COLOR="Blue"][FONT="Courier New"]$ sudo apt-get install libgtk2.0-dev
...
The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.8.6-0ubuntu2) but 2.8.6-0ubuntu2.1 is to be installed
E: Broken packages[/FONT][/COLOR]

What's wrong? I do have libgtk2.0-0 install in my system:

[COLOR="Blue"][FONT="Courier New"]$ dpkg -l libgtk2.0-0
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name            Version         Description
+++-===============-===============-==============================================
[COLOR="Red"]pi[/COLOR]  libgtk2.0-0     2.8.6-0ubuntu2. The GTK+ graphical user interface library[/FONT][/COLOR]

I noticed that the prefix in dpkg -l output is 'pi' instead of 'ii', is this what cause the problem?  How can I change it back to 'ii' ?


Thanks,
Metaosp

---

### Post by gord on 2006-02-20
you need to [ enable extra repositorys](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse)

those dependacys are in the other repositorys that you need to enable, once you have done that just try again and it should work fine. 

if you allready have done that it could just be that you need to update apt's package list ```
sudo apt-get update
```

---

### Post by metaosp on 2006-02-20
I did enable all the extra repositorys... besides the package it depends (libgtk2.0-0) is already installed in my system.  I wonder what exactly does [COLOR="Blue"]"Depends: libgtk2.0-0 (= 2.8.6-0ubuntu2) but 2.8.6-0ubuntu2.1 is to be installed"[/COLOR] means? Does that mean I need 2.8.6-0ubuntu2 version of the package?  The one that I already have is 2.8.6-0ubuntu2.1, why it says 'to be installed'?

---

