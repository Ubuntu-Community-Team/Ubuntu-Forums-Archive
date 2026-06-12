---
title: "Wine uninstall broke my laptop...."
date: 2012-12-20
forum: New to Ubuntu
---

### Post by mrsjcmking on 2012-12-20
So I was trying to uninstall wine. Had a google and after some failed attempts I found a command that worked only problem was that it also uninstalled a lot of other things including my software center and my terminal. Computer crashed and when I start it a thing pops up saying there's a problem with my graphics card and it needs to start in low graphics mode. If I click yes it doesn't run and if I click no it doesn't run. 

Any ideas that aren't reinstall Ubuntu (which I will do if I really have to)

---

### Post by audiomick on 2012-12-20
Don't like your chances much. If you don't know exactly what was removed, I could be an extremely tedious process getting a stable install back.

What you almost certainly can do is boot into the live environment, copy the contents of your /home/user folder out, and anything else you want to save, and put it all back after a fresh install. If you have your /home on a seperate partition, you can, of course, just re-mount it.

How experienced and adventurous are you? It just occurs to me that you can almost certainly, using gparted before the install, shrink down the partition from your existing install, install (using the manual option on the installer) to the empty space (consider creating a separate /home partition...) and mount to old partition to the new install. I think if you setup the same user name and password that you wouldn't even have permission problems. This would give you access to your old data and config files. When you have the new install set up, you can clean out the partition from the old install, keep it as a data partition or remove it.

---

