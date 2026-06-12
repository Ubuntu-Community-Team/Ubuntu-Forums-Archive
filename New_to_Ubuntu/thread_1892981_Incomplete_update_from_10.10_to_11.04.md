---
title: "Incomplete update from 10.10 to 11.04"
date: 2011-12-09
forum: New to Ubuntu
---

### Post by donna111 on 2011-12-09
I installed version 10.10 using Wubi and have had no problems with it. I updated it to 11.04 through the update manager and all the installation etc went ok. However I have tried to restart after the install and it won't go any further than the purple screen with ubuntu and 5 red dots underneath. I really don't want to have to wipe the install and do it again as i have stuff stored on the ubuntu drive that i need and can't access (don't know how or if i can) from windows. How can i get the install to finish properly?
 
Thanks

---

### Post by fantab on 2011-12-09
> **donna111 said:**
> I installed version 10.10 using Wubi and have had no problems with it. I updated it to 11.04 through the update manager and all the installation etc went ok. However I have tried to restart after the install and it won't go any further than the purple screen with ubuntu and 5 red dots underneath. I really don't want to have to wipe the install and do it again as **i have stuff stored on the ubuntu drive that i need and can't access** (don't know how or if i can) from wondows. How can i get the install to finish properly?

Well, to rescue your data you will have to use the Ubuntu LiveCD and boot with it. Then you can access the Ubuntu partition or disk and save data. 

WUBI is not a Permanent way to install Ubuntu, at best it is provided so that you can try Ubuntu from within your windows install. I suggest that after you've backed up your data **clean install Ubuntu on its own and Dual Boot with Windows.** Personally I don't recommend Upgrades to next version of Ubuntu. It is best to do a clean install.

If you so decide to Dual boot then please provide us more information about your HDD and partitions and we will help you do a dual boot installation.

---

### Post by bcbc on 2011-12-09
This tool [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/) can read the \ubuntu\disks\root.disk. I've heard it can be a little flaky but it gets the job done.

At the least you should try a few options when booting:
e.g. select the recovery menu, or an older kernel.

Or hit 'e' to edit the first entry, delete 'quiet splash' to see if that indicates where the failure is. (Hit Ctrl+X to boot).

If you have an nvidia card you may need to reinstall your drivers. In that case, add 'nomodeset' (no quotes) where the quiet splash was.

---

