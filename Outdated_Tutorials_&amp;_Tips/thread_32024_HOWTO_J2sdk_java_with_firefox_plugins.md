---
title: "HOWTO: J2sdk java with firefox plugins"
date: 2005-05-05
forum: Outdated Tutorials &amp; Tips
---

### Post by RastaMahata on 2005-05-05
Here's an easy way to install java sdk 1.5 with firefox plugins.
Just follow these steps:

1. Add backports-extra to your repositories list:```
sudo gedit /etc/apt/sources.list
```In the last line, add this (if not present):```
deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted
```
2. Update your apt-get info:```
sudo apt-get update
```
3. Install the java sdk package:```
sudo apt-get install sun-j2sdk1.5
```
4. Now open a console and type this:```
sudo ln -sf /usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /etc/alternatives/firefox-javaplugin.so
```
5. Open up firefox (close it and open it again if you had it open), and type this in the address bar:```
about:plugins
```You should see a "Java(TM) Plug-in 1.5.0_02-b09" Section.

Enjoy

PD: Sadly enough, I haven't downloaded the jre package yet, so I cant give exact instrucions, but it should be among the same lines... Good luck.

---

### Post by bored2k on 2005-05-05
I believe this topic has been dealt with several times.
1. [http://www.ubuntulinux.org/wiki/Java](http://www.ubuntulinux.org/wiki/Java)
2-4. The several scripts here
5-11. The 7 different steps on [http://www.ubuntulinux.org/wiki/Java](http://www.ubuntulinux.org/wiki/Java)

Nonetheless, I suppose it's still good.
BTW, making a debian package automatically makes Java work systemwide [firefox, etc].

---

### Post by RastaMahata on 2005-05-05
[QUOTE=bored2k]I believe this topic has been dealt with several times.
1. [http://www.ubuntulinux.org/wiki/Java](http://www.ubuntulinux.org/wiki/Java)
2-4. The several scripts here
5-11. The 7 different steps on [http://www.ubuntulinux.org/wiki/Java](http://www.ubuntulinux.org/wiki/Java)

Nonetheless, I suppose it's still good.
BTW, making a debian package automatically makes Java work systemwide [firefox, etc].[/QUOTE]
 its just that I tried them all and had several problems myself. I thought it would be nice to have these instructions posted here.

Anyway, I dont know why the firefox plugin doesnt work out of the box... I should ask jdong that :S

---

### Post by bored2k on 2005-05-05
[QUOTE=RastaMahata]its just that I tried them all and had several problems myself. I thought it would be nice to have these instructions posted here.

Anyway, I dont know why the firefox plugin doesnt work out of the box... I should ask jdong that :S[/QUOTE]
 I'm not saying your guide is bad, I just used my argument as an excuse to post other options for newbies ;). Anyway, the debian package I created through step 5 automatically made java links for firefox. I believe jdong's did too. You sure theyre not there for you ?

---

### Post by htruong0101 on 2005-05-07
Thanks you for your post RastaMahata!!
  I just install sdk and things went smoothly.

---

### Post by RastaMahata on 2005-05-07
[QUOTE=bored2k]I'm not saying your guide is bad, I just used my argument as an excuse to post other options for newbies ;). Anyway, the debian package I created through step 5 automatically made java links for firefox. I believe jdong's did too. You sure theyre not there for you ?[/QUOTE]
Well, they're not there with j2sdk... maybe they are with jre :/

---

### Post by koyi on 2005-06-26
Thanks for the tips.

Just to add that the main repo of the backport project seems to be disabled from public access. So you need to use one of the mirrors they provide instead.

Ref: [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

---

