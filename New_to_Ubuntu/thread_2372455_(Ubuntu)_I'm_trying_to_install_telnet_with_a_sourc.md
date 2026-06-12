---
title: "(Ubuntu) I'm trying to install telnet with a source package… Make doesn't work!"
date: 2017-09-25
forum: New to Ubuntu
---

### Post by soomin on 2017-09-25
!!I should install Telnet with source package for personal reasons. Plz don't advise me to use 'apt-get install' command.!!
I've just install Ubuntu 14.04.4(LTS) 32bits on VirtualBox and full desktop as well. There was no issue with 'apt-get update', 'apt-get install' on the Virtualbox though there were some on the full desktop.(That's why I install Ubuntu again on the VirtualBox in my laptop...)
After I downloaded and extracted 'netkit-telnet_0.17.orig.tar.gz'. I installed build-essential and I also install 'termcap' for './configure'. I just wanted to said that I did all the things I should've done without issues or mistakes.
But, whenever I try to compile with 'Make' command, it's not working. I got this error message : 'exit' was not declared in this scope. It was in main.cc, so I added '#include though I thought it was weird to edit codes like telnet by myself.. error in main.cc has gone! but there are a lot of .cc files that include 'exit' function. Do I have to add in all the files? I do not think so..
Is there anybody who knows how to solve this problem? Plz give me some advice I'm struggle to solve it..........
(Here's what I've tried. :downgrade/reinstall gcc compiler, reinstall Ubuntu, download telnet source packages in other website, download other version of telnet source package ...... and some others that I can not even remember.)

---

### Post by wildmanne39 on 2017-09-25
Welcome to the Forum!

*Thread moved to **New to Ubuntu for better support**.*

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---

### Post by Tadaen_Sylvermane on 2017-09-25
you should create a ppa and let launchpad build proper packages for you from the source you upload. saves a world of hurt. make and make install is and should always be an absolute last resort.

---

