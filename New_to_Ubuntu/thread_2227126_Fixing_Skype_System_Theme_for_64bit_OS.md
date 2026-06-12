---
title: "Fixing Skype System Theme for 64bit OS"
date: 2014-05-30
forum: New to Ubuntu
---

### Post by Rebecca_D on 2014-05-30
I am using Ubuntu 14.04 LTS on an Asus P6T SE 64 bit motherboard and running Skype 4.2.0.11.

I have read a number of recent online articles which show a way of installing the 32 bit GTK2 theme engine on 64 bit machines (e.g. [http://tinyurl.com/pvvkhou]("http://tinyurl.com/pvvkhou")) to improve the appearance of Skype. They all suggest the following command:

[INDENT]sudo apt-get install gtk2-engines-murrine:i386 gtk2-engines-pixbuf:i386[/INDENT]

When I run this command I get the following output:

[INDENT]Reading package lists... Done[/INDENT]
[INDENT]Building dependency Tree[/INDENT]
[INDENT]E: Unable to locate package apt-get[/INDENT]
[INDENT]E: Unable to locate package install[/INDENT]

Can anyone explain please? Is this unavailable in a repository? Thank you.

---

### Post by doctorjellyface on 2014-11-08
I just tried the command now - worked perfectly, and fixed the skype theming, thanks. Did you copy+paste it right? Looks like apt-get is trying to install itself...

---

