---
title: "ALERT! /dev/disk/by-uuid/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx does not exist."
date: 2011-10-31
forum: New to Ubuntu
---

### Post by Alita99 on 2011-10-31
Hi everybody!

I'm new here, I really appreciate this forum and what you do...

Now I've a problem with my laptop, when I start it with ubuntu it didn't turn on and I see only a black screen.
If I press a key I receive this answer:

"ALERT! /dev/disk/by-uuid/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx does not exist.

Dropping to a shell!

BusyBox v1.13.3 (ubuntu 1:1.13.3-1ubuntu11) buitl-in shell (ash)
Enter "help" for a list of commands."

what must I do?

thank you very much!

Cris

---

### Post by matt_symes on 2011-10-31
Hi

Can you boot into an older kernel ?

If not, do you have a LiveCD/USB handy ?

Kind regards

---

### Post by Alita99 on 2011-10-31
> 
Can you boot into an older kernel ?No

> If not, do you have a LiveCD/USB handy ?No

I really don't know how can I take a LiveUSB

tks :)

---

### Post by Rex Bouwense on 2011-10-31
How did you install Ubuntu?  Which version is it?  Are you dual booting or is Ubuntu your only operating system?  We do need some more information to help you.

---

### Post by Alita99 on 2011-11-03
> How did you install Ubuntu?  Which version is it?  Are you dual booting  or is Ubuntu your only operating system?  We do need some more  information to help you.     It's Ubuntu 9.10 and I'm dual booting with XP. Someone install me Ubuntu, I can't ask him now how he do it, but I think he used a liveCD.

tanks! best regards,

Cris

---

### Post by coffeecat on 2011-11-03
> **Alita99 said:**
> "ALERT! /dev/disk/by-uuid/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx does not exist.

The long alphanumeric string, which you have represented with the x's, is called the UUID. It's the identifier for one of the partitions on your hard drive. It has clearly disappeared, or been severely damaged somehow. The reason you are getting the error is that Ubuntu needs to mount that partition on bootup in order to function.

Question: do you see the "grub" menu which gives you a choice of booting into Ubuntu or Windows? And, if you do, can you boot into Windows OK? If yes to both, then that means that your Ubuntu root partition is OK, and that another partition is the problem.

> **Alita99 said:**
> It's Ubuntu 9.10

Ubuntu 9.10 in now unsupported and if you want a functional Ubuntu installation, the best thing to do would be to back up any personal files and then do a fresh installation of a supported version of Ubuntu, for which you would need to create a live Ubuntu CD.

Before we go any further, do you want to make a fresh installation of Ubuntu so that you have an Ubuntu/Windows dual-boot, or do you want to revert your machine to Windows only? Then we can advise you what to do next.

---

### Post by Alita99 on 2011-12-12
Sorry if I take many time to answer!

> 
Question: do you see the "grub" menu which gives you a choice of booting  into Ubuntu or Windows? And, if you do, can you boot into Windows OK?  If yes to both, then that means that your Ubuntu root partition is OK,  and that another partition is the problem.


I can see the grab menu and I can only choose Windows OK.
I think my H-D is divided in two parts,(maybe I'm wrong) so I don't understand how would be another partition the problem. 

> [...]do you want to make a fresh installation of  Ubuntu so that you have an Ubuntu/Windows dual-boot 	
I would like an Ubuntu/Windows dual-boot, yes.

> the best thing to do would be to back up any personal files
How can I take my personal files saved in the ubuntu partition of my hard disk? If it is possible...

Tanks

---

### Post by coffeecat on 2011-12-13
To recover personal files from the Ubuntu partition, if that is possible, you would need to run a live CD. I say "if that is possible" because with the error you are getting, it is likely that one of your partitions is badly damaged. It would not be the Ubuntu root partition because it seems as though the grub bootloader is working and some essential grub files are in the Ubuntu root partition. Which means that it is possible that you have a separate /home partition and that is the one that is damaged. But that is mostly speculation. Before doing anything else, you need to do some investigation and that also requires running the Ubuntu live CD. Lastly, if you want to re-install Ubuntu for a Windows/Ubuntu dual-boot you would need to do that from the live CD.

Have a read of this:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

You can download the ISO here:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Under "download options" I suggest you select the 10.04LTS version which has the desktop interface you are used to. The newest 11.10 version has a quite different desktop, and if you are going to do some rescue work, you will probably prefer something familiar to work with.

Once you have burnt the ISO to CD, you need to make sure that the BIOS on your machine is set to boot from the optical drive first. Let us know when you have a bootable CD and then we can take it from there.

---

