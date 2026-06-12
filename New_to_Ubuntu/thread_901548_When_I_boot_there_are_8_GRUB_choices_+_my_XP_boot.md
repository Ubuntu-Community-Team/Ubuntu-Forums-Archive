---
title: "When I boot there are 8 GRUB choices + my XP boot"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by waste301 on 2008-08-26
I just want to get rid of all the GRUB boot selections, remove ubuntu, and start over with a fresh install of Hardy Heron.  My firefox is dead in ubuntu.  I'm afraid to monkey around with GRUB, because then I won't even be able to boot XP so I can ask for help on these forums.

---

### Post by lackoblacko on 2008-08-26
you can remove choices in your grub but editing the file menu.lst located at /boot/grub/.  As fore firefox, what is wrong with it?  You can try reinstalling firefox instead of reinstalling hardy heron.

---

### Post by kellemes on 2008-08-26
> **waste301 said:**
> I just want to get rid of all the GRUB boot selections, remove ubuntu, and start over with a fresh install of Hardy Heron.  My firefox is dead in ubuntu.  I'm afraid to monkey around with GRUB, because then I won't even be able to boot XP so I can ask for help on these forums.

No need to remove Ubuntu or Grub.
Simply pop-in the livesystem and reinstall Ubuntu, have it format the partitions you want it to use. Grub will provide you with a brandnew and clean bootmenu.
Obviously don't format the Windows partition.

---

### Post by Thelasko on 2008-08-26
You don't need to mess with Grub.  As kellemes said, just reinstall Ubuntu over your current installation.

The reason you have more than one Ubuntu in Grub is because when your kernel (the most basic part of linux) is updated, it keeps a few of the old kernels in Grub, so if you have a problem with the new kernel you can still use the old one.

---

### Post by WRDN on 2008-08-26
If the only issue if Firefox, then I don't see any point in reinstalling Ubuntu.
You can remove the entries from the GRUB menu using multiple methods.
If there are kernels (which are named in the GRUB entries at bootup) you no longer need, then feel free to uninstall them. Alternatively, remove the entries from the GRUB menu, or comment them out.

To do this, open the Terminal and type:

```
sudo gedit /boot/grub/menu.lst
```

Now, delete any entries you don't want, before the line "### END DEBIAN AUTOMAGIC KERNELS LIST". Do not change the file after that line, else you may effect Windows ability to boot properly. Alternatively, if you don't want to delete the entries, just place put change the "title" line for each entry e.g. add a # before title, or edit the word itself.

---

### Post by waste301 on 2008-08-26
> **lackoblacko said:**
> you can remove choices in your grub but editing the file menu.lst located at /boot/grub/.  As fore firefox, what is wrong with it?  You can try reinstalling firefox instead of reinstalling hardy heron.

The firefox thing I have given up on after talking with several people here.

> **kellemes said:**
> No need to remove Ubuntu or Grub.
Simply pop-in the livesystem and reinstall Ubuntu, have it format the partitions you want it to use. Grub will provide you with a brandnew and clean bootmenu.
Obviously don't format the Windows partition.


My system has problems with the Live CD, can I do this with the command line ISO I burned?

Is it OK to just wipe my ubuntu partition, or will that mess with GRUB and keep me from booting at all?

> **Thelasko said:**
> You don't need to mess with Grub.  As kellemes said, just reinstall Ubuntu over your current installation.

The reason you have more than one Ubuntu in Grub is because when your kernel (the most basic part of linux) is updated, it keeps a few of the old kernels in Grub, so if you have a problem with the new kernel you can still use the old one.

I downloaded and burned the Hardy Heron command line install, and when I boot from CD it locks up: error -5

---

### Post by nicedude on 2008-08-26
Since most or all of the extra entries you see in grub are older kernels that have been superseded by newer one, You can use synaptic to remove all the linux kernels you no longer use and that will both remove them from Grub menu and get you back like 60MB of space per kernel version. Just don't remove the one you are booting from now :-)

---

### Post by kellemes on 2008-08-26
<QUOTE>Is it OK to just wipe my ubuntu partition, or will that mess with GRUB and keep me from booting at all?</QUOTE>

Yes it will mess with Grub since Grub depends on files in /boot

<QUOTE>I downloaded and burned the Hardy Heron command line install, and when I boot from CD it locks up: error -5[/QUOTE]

You are talking about the alternate desktop cd?

By the way.. you can always use [Super Grub Disk]("http://www.supergrubdisk.org/") to get around bootloader trouble and to load XP if Grub goes wrong. I'd advise you to download and burn it just in case.

---

### Post by waste301 on 2008-08-26
> **nicedude said:**
> Since most or all of the extra entries you see in grub are older kernels that have been superseded by newer one, You can use synaptic to remove all the linux kernels you no longer use and that will both remove them from Grub menu and get you back like 60MB of space per kernel version. Just don't remove the one you are booting from now :-)

OK - I'm in XP right now.  I'll boot into ubuntu and fire up synaptic.  What do I use to remove old kernels?

---

### Post by kellemes on 2008-08-26
> Is it OK to just wipe my ubuntu partition, or will that mess with GRUB and keep me from booting at all?

Yes it will mess with Grub since Grub depends on files in /boot

> I downloaded and burned the Hardy Heron command line install, and when I boot from CD it locks up: error -5

You are talking about the alternate desktop cd?

By the way.. you can always use [Super Grub Disk]("http://www.supergrubdisk.org/") to get around bootloader trouble and to load XP if Grub goes wrong. I'd advise you to download and burn it just in case.

---

### Post by waste301 on 2008-08-26
> **kellemes said:**
> <QUOTE>Is it OK to just wipe my ubuntu partition, or will that mess with GRUB and keep me from booting at all?</QUOTE>

Yes it will mess with Grub since Grub depends on files in /boot

<QUOTE>I downloaded and burned the Hardy Heron command line install, and when I boot from CD it locks up: error -5

You are talking about the alternate desktop cd?

By the way.. you can always use [Super Grub Disk]("http://www.supergrubdisk.org/") to get around bootloader trouble and to load XP if Grub goes wrong. I'd advise you to download and burn it just in case.[/QUOTE]

Thx - I've already got it :) and yes, I was talking about the alternate CD.

---

### Post by waste301 on 2008-08-26
OK - I can no longer boot into ubuntu.  The loading bar just paces endlessly.

What I need is a way to wipe my ubuntu partition, and install Hardy Heron.  GRUB shows multiple kernels to load when I boot, so I am afraid to just delete the ubuntu partition.  I would like to remove all evidence of a dual boot from my system, and start with an XP partition and a blank 35 gig partition.  I will then use my Hardy Heron CD to install ubuntu on to it.

---

