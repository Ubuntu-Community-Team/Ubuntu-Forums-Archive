---
title: "Idea of installing several distros: SAFE?"
date: 2006-11-26
forum: Other OS Talk
---

### Post by celsofaf on 2006-11-26
Hello. I have an HD with Windows and is FAT32 formated, and I'll get a second HD (120GB) on which I want to do the following:

- hdb1: 60GB for my files (could be ext3, since I use that Windows software who makes reading/writing over ext3 possible; but I'd make it FAT32 without a problem).
- hdb2: 1GB /boot partition. Yes, quite big for it, but I'd like to have a small distro installed there (Damn Small Linux maybe) just in case I run into problems on the other linux root partitions.
- hdb3: 1.5GB swap: obvious thing needed.
- hdb4: 15GB /opt partition: so I can install software in there to have common use between my linux distros.
- hdb5: about 15GB to install and run K/Ubuntu.
- hdb6: about 15GB to install Arch Linux.
- hdb7: about 10GB to test random linux distros.

I don't realy need a /home partition, as my peronal files will all be in hdb1.

Is this a good setup? :D Ideas, thoughts? Is it SAFE?

I already use Ubuntu (Dapper) on my slave HD which will get retired as soon as I get the new HD.

Now, a question... Yes, I can boot from Ubuntu LiveCD and do the formating and partitioning I want, before starting the "fun". Noting that I have Windows installed (hda1) and want to keep it, what is the best order to install my stuff? Arch first (with /boot on hdb2), then DSL then Ubuntu? Or does the order realy matter anyway?

GRUB should also be installed on hdb2 (ie: hd1,1)?

Any comments are more than welcome, by the way. Not only regarding install tips but also my idea.

Thank you all for the patience!

---

### Post by justin whitaker on 2006-11-27
I've had 12 distros and XP on my 160GB HD, and an 100GB for /Home.

Now I've got a 250 and the 160, so imagine the damage I can inflict on my partition table!

Ok, here's what I do. Chose one main, let that install GRUB, LILO onto the MBR. You can manage booting into everything else from there.

Next, I would not seperate out /OPT for each distro. Not everything installs to /Opt cleanly, and you might install something which needs a library or something that the other distro does not have. 

You aren't installing anything that is difficult to update....apt and pacman are perfectly fine for managing each distro. 

The critical thing here is keeping your /Home partition distinct. I don't even name it /Home. I call it /Personal or /Stuff, and make it automount for each distro. That way I make sure that I don't accidently write over it. 

Good luck!

---

### Post by celsofaf on 2006-11-27
Right, Justin, thank you! But let me disturb (:D) you a little more.

Does it mean that I have to install both GRUB and LILO at /boot partition? And, since I'd like (on the beginning only, perhaps) use Ubuntu as a "main stable distro", and use Arch Linux for learning to work the hard way (I haven't tested Arch yet, but I consider myself ready for it after reading too much about it), and perhaps have a small distro like DSL in the /boot partition... So... should I install Ubuntu first and foremost?

All right, I won't separate /opt from the others. Didn't think about that. Good advice. And my "personal files partition" will not have /home mounted on it. The /home of each distro will be mounted on respective root partition, and used only for personal configs and customization. My personal files will be away from the mess!

Thank you for the patience: I will be sure to get back here after the mess (;)) will start, and also after it's working!

---

### Post by celsofaf on 2006-12-02
**(warning: long post)**


Well... here we go again.

I decided to do some testing this weekend. My current slave HD has 40GB (it will be replaced by that 120GB one), it only had about hdb1 = 38GB for Ubuntu 6.06 and hdb2 = 2GB for Swap. This partitioning was made by the Ubuntu installer.

My RAM memory is of 1GB. My master HD was (until hours ago...) of 80GB FAT32 formated with Windows XP on it.

OK... I take a Live-CD and do some mess... Aproximate figures for new partition table:

hdb1 = 9GB ext3 for files
hdb5 = 1GB swap (yes, I don't even need this much)
hdb6 = 10GB reiserfs
hdb7 = 10GB ext3
hdb8 = 10GB ext3

OK, let's boot again. Zenwalk 4.0 CD on the drive, install it to hdb6. I let it install LILO on the MBR (master boot record), since it doesn't offer GRUB as an alternative. No problem with this. Install went fine, LILO automaticaly recognized Windows on hda1.

Found Zenwalk to be very, very fast and without fussy or choosy things. Very good to my taste. And having a very small repository means a nice oportunity to learn how to install stuff "by hand", although it brings Xfce and basic stuff with it, but only the minimum needed. It also lacks some GUIs for configuring stuff, so I also have the oportunity to learn configure my system a harder (and better!) way.

OK, back to life.

Ubuntu 6.06 live-CD on the drive, let's boot it up and install on hdb7. Fine, all went well, GRUB is back again and it recognized both Windows and Zenwalk (he called it Slackware, though... well... it **IS** Slack anyway!), but I thought... I installed the wrong distro. I realy wanted to install Kubuntu 6.10 on hdb7, but put the wrong stuff to load and didn't realy care about it.

OK, so let's install Kubuntu 6.10. On to hdb7, of course. It went well... But I booted later and... Hey, where is Windows on GRUB's menu? Kubuntu is here, Zenwalk ("Slackware") also. OK, I can fix /boot/grub/menu.lst without a problem. Let's boot Kubuntu, mount hda1... it's EMPTY. oops... seems I formated it by mistake during the partition choosing for Kubuntu. This is: when you install Kubuntu (or any other *buntu) and manualy choose the partitions, you can check the partitions to be mounted if they will be formated or not. I must have accidentaly checked hda1 for formatting...

OK, no big deal. My personal files were backed up, so I didn't lose any important stuff. The Windows and softwares I can install again, and I realy am not using Windows for other stuff than playing: Linux is for everything else lately. :) But... let's reinstall Windows!

Pick WinXP disc, let's boot from it... No, it doesn't. Yes, booting from CD is turned on, the CD is intact also, but it doesn't boot. So, searching around, I saw that it won't boot if GRUB is on the MBR. I have to "restore" the MBR before being able to boot the WinXP disc. Yes, there are a lot of ways to do it, I know.

But now I plan to use the whole "new" HD of 80GB to finaly do the mess I want to do. Will repartition it, etc. I will reinstall Windows XP to the slave drive, then reinstall it AGAIN when the 120GB HD comes up.

With this experience, I see I could live without a separate /boot partition. :) Now, just two questions:

(1) Is there any problem to allocate hda1 for swap, or it "cannot" be the first partition?

(2) Best way to install WinXP to hdb1 after I have at least one Linux distro running on hda?

I may even run Windows inside Linux via VMware or so, but... I need to know about (2) so I can get to know the alternatives.

Thank you, specialy for the patience!

---

