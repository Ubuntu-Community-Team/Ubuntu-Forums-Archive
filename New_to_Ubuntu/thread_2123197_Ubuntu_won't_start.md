---
title: "Ubuntu won't start"
date: 2013-03-07
forum: New to Ubuntu
---

### Post by Grekkostas on 2013-03-07
Hey guys,  first of all sorry for my english but it's not my native language 
I am having problem starting ubuntu . I used to use ubuntu but after an upgrade they crashed 
This is what i get when I try to start them :
[CENTER]GNU GRUB version 1.99-12ubuntu5.1[/CENTER]
Mnimal BASH-like editing is supported , For the first word , TAB lists possible commant completions. Anywhere else TAB lists possible device or file completions
grub>

What do I need to do to get ubuntu back ?

---

### Post by oldfred on 2013-03-07
Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

You may be able to boot and repair from inside your install.

 Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

---

### Post by Grekkostas on 2013-03-07
I didn't get you very well , which link should i post to the boot info ?

---

### Post by oldfred on 2013-03-07
You download the Boot-Repair script into any working Linux, an install or liveCD/DVD/Flash drive. 

Then you run script and if you have Internet connection it will automatically upload a lot of data with details of your install to pastebin. 
It gives you the link to post here, so we can see your data.

---

### Post by Grekkostas on 2013-03-07
Yeah , but my problem is that it won't start .. Linux does not start and i am stuck with windows now

---

### Post by oldfred on 2013-03-07
Is this error from the liveCD or flash?

---

### Post by Lisiano on 2013-03-07
> **Grekkostas said:**
> Yeah , but my problem is that it won't start .. Linux does not start and i am stuck with windows now
oldfred meant you can use a LiveCD/USB (The CD/USB you used when you first installed Ubuntu) to run boot-info/repair.

---

