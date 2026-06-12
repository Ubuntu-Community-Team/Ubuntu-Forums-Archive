---
title: "Lubuntu on Vaio VPCW21C7E"
date: 2014-01-07
forum: New to Ubuntu
---

### Post by Citta on 2014-01-07
Hi, 
After having installed Lubuntu as a netbookinstall on Vaio VPCW21C7E, difficult problems occurred:

1. Fn-keys for dec/inc brightness did not work, even not after 65 posts!! At least this advanced my Linux-education!?
2. Win crashed, Lubuntu also did not start. After 1,5 days rebooting I could start the &#8220;System Image Recovery&#8221; of Win.
 So I can use Win and Lub. again. A Clerk in a shop told that it is not unusual, when having dual-boot, the recovery partition is hardly accessible.
Is this correct??
3. Several applications in Lubuntu did not start, e.g. USB-Startcreator, VLC. 
4. Using this OS the DE went black, later I had a different DE, tabs on the top, with topics on them displayed. Why? What is it, does this mean?
5. Before and after 4. small windows with ..internal error.. and other assertions popped up-what is the conclusion? Report-option did not work. 
6. Last, but not least, how to remove this buggy OS??? Searched in this forum, could not find something suitable,
 googling this gave results, but I am not sure about the trustworthiness, because I do not want mess up the netbook.Frittered time and temper away sufficiently. 

Thanks a lot for taking the time reading and your suggestions!
PS: Different font sizes are not intended and could not be changed...

---

### Post by mastablasta on 2014-01-07
> **Citta said:**
> Hi, 
After having installed Lubuntu as a netbookinstall on Vaio VPCW21C7E, difficult problems occurred:

1. Fn-keys for dec/inc brightness did not work, even not after 65 posts!! At least this advanced my Linux-education!?

if you tried it all and still doens't work it means your hardware is not fully compatible with Lubuntu (btw there are workarrounds like using app to reduce brightness etc.).

> 
2. Win crashed, Lubuntu also did not start. After 1,5 days rebooting I could start the “System Image Recovery” of Win.
So I can use Win and Lub. again. A Clerk in a shop told that it is not unusual, when having dual-boot, the recovery partition is hardly accessible.
Is this correct??
if propperly done there should be no interference. however changing recovery partition into secondary partition or removing it might interfere with the windows recovery process.
> 
3. Several applications in Lubuntu did not start, e.g. USB-Startcreator, VLC. 
Hard to say what is wrong without more info.
> 
4. Using this OS the DE went black, later I had a different DE, tabs on the top, with topics on them displayed. Why? What is it, does this mean?


don't know exactly what you mean. did you maybe change DE on login?

> 
5. Before and after 4. small windows with ..internal error.. and other assertions popped up-what is the conclusion? Report-option did not work. 
I do not understand this one. linux logs all errors in log files.
> 
6. Last, but not least, how to remove this buggy OS??? Searched in this forum, could not find something suitable,
googling this gave results, but I am not sure about the trustworthiness, because I do not want mess up the netbook.

[SIZE=2]you need windows recovery USB (which is what you should have created before doing any OS install. then you run Lubuntu live USB select try it instead of install (which is what you should have done before installing the Lubuntu OS to see if it all works and if hardware you are using is compatible). Next start gparted and remove Lubuntu partitions from disk. now boot into widnows recovery console and fix the mbr (depending which windows you run you need to run appropriate command - see microsoft help articles on this)
[/SIZE]

---

### Post by coffeecat on 2014-01-07
> **Citta said:**
> PS: Different font sizes are not intended and could not be changed...

You may not have intended them, but you must have been clicking buttons in the message toolbar to get all those font variations. And they certainly can be changed - which I have done for you. :)

---

### Post by Citta on 2014-01-07
Ad 4.: Not the login, DE changed!
Ad 5.: After displaying the error the option to send this popped up-this did not work, too. 
Ad 6.:USB recovery cannot be created, because Win7Starter is installed and you do not get a DVD or something else for this purpose. Netbooks are not shipped with a DVD!!
No, till now I do not know how to remove that OS-it is a beginners section!

---

### Post by mastablasta on 2014-01-08
> **Citta said:**
> Ad 4.: Not the login, DE changed!
well would have to see the pic to know more (i am not using Lubuntu) but it could be a GPU driver crash that activated a fallback mode of sorts. 
> 
Ad 5.: After displaying the error the option to send this popped up-this did not work, too. 
quite possible yes. LXDE though good is not really a mature desktopenvironment. if you look at it's components many have not reached version 1 yet. perhpas you could give KDE a try (i dont' know what your specs are). they have a netbook plasma version.

> 
Ad 6.:USB recovery cannot be created, because Win7Starter is installed and you do not get a DVD or something else for this purpose. Netbooks are not shipped with a DVD!!
No, till now I do not know how to remove that OS-it is a beginners section!

i have windows starter on my netbook too and i had the option could create 1 full backup to USB stick/disk (essentially i now have windows starter on USB). perhaps repair USB disk can be created. i am not sure if it's enough to do the fixmbr command. but repair disk is definatelly possible (it's basically a windows boot disk, not windows install disk).

if you can access windows recovery you might also be able to do "fix" the mbr:
[https://support.microsoft.com/kb/927392](https://support.microsoft.com/kb/927392)

this one has explanation how get install disk it manually on USB (usefull for netbook with this kind of tool missing)
[http://www.tomshardware.com/news/win7-windows-7-mbr,10036.html#win7-windows-7-mbr%2C10036.html?&_suid=138916755436902223486725827185](http://www.tomshardware.com/news/win7-windows-7-mbr,10036.html#win7-windows-7-mbr%2C10036.html?&_suid=138916755436902223486725827185)

edit: if oyu ever wish to try a newer version (might be more compatible with your HW) or try another linux distro or ubuntu desktop version (e.g. Kubuntu, Xubuntu) make sure oyu go with "try it" first. just to see how well it works on your hw first before comitting to installing it.

---

### Post by Citta on 2014-01-09
I have a system image on an external HDD, created in "Backup and Restore", some time ago and a system recovery disk...but no player. Is the system image sufficient for this purpose? Can you start Win from your USB and use it like, e. g. Ubuntu.iso, installed via YUMI or is it something else? System recovery could not be saved on an ext. HDD or USB-it demanded always an optical drive. I will buy a stick and try it again. 
[SIZE=2]"Widnows recovery console and fix the mbr". What is a recovery console and what happened to the mbr so I have to fix it? [/SIZE]Clicked the first link, MS, did understand....nothing. The second....well, Win boots!
People assert that an installation with Wubi is not so good...why? At least an OS can be deleted with Wubi without ceaseless time consuming tinkering around. 
Thanks!

---

### Post by Citta on 2014-01-11
As assumed with a stick is neither a system image nor a system recovery savable.

---

