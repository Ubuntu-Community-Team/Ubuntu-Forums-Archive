---
title: "ubuntu, flash for firefox and duel boot"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by TymeKyller on 2008-09-03
Ok, I finally have the pc up and running after a long, long time... :p
I'm getting use to Ubuntu and I'm really liking it... 
To bad my wife is one of those can't teach a old dog new trick type women... 
She not sure about it, so I told her we could duel boot and she could slowing migrate over to linux... 
She likes that idea so I was wondering how to make a partition on my drive right now so I could install xp too. 
I have a 40GB drive and Ubuntu is taking up all of it, there is only one partition.
Should I wipe the drive, partition it to 20GB each using xp and install xp then ubuntu? I would like to be able to do this without reinstalling ubuntu, I have all the fresh updates and everything for it.
Also with firefox I installed flash when the drop down box prompted me too, it gave me three option install flash or flash/macromeidia or something else I can't remember, I choose the second one and now some websites won't work where I use to watch movies, I just wanted to get rid of the one flash and install adobe flash..
Thanks you all so very much, sorry for the long post.
Tyme

---

### Post by tuxxy on 2008-09-03
Read the [switching from windows guide]("https://help.ubuntu.com/8.04/switching/index.html") for installing/partitioning help,

TO install Flash plugin for firefox open a terminal and type

```
sudo apt-get install flashplugin-nonfree
```

If you havnt already I would take a look at the ubuntu-restricted-extras package as this will provide many things your used to having by default in windows.

---

### Post by philinux on 2008-09-03
What is it that you need that you're used to in windows. There's more than likely to be an alternative.

---

### Post by lakris61 on 2008-09-03
> **TymeKyller said:**
> 
She not sure about it, so I told her we could **duel boot** and she could slowing migrate over to linux... 


This is very good!

"Now it's Your turn, now it's my turn, now it's Your turn..."

who will give in?
;)

Anyway, I would go with a reinstall and, yes, give them half/half. Install XP first, it's easier for Ubuntu to to adapt to an existing XP-install than the other way around.

And unless You are too political, You should enable all third party, non-free, possibly proprietary components that are available in Ubuntu. You will have a (mostly) non-problematic environment.

Just my 2 öre

/Lakris

---

### Post by t0p on 2008-09-03
> **lakris61 said:**
> 
Just my 2 öre


Okay, so what the hell is an "ore"?

---

### Post by kansasnoob on 2008-09-03
I used the following guide for my very first dual boot and things went off without a hitch:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

I'll grant you it is a bit easier to install Windows first as you don't have to mess with grub, but sooner or later you'll want to know how to work with Grub anyway.

Read that over and if you have any questions feel free to shout. Make sure you know where/how to find the backup of your menu list!

Note: where it says, "Then, type in sudo gedit /boot/grub/menu.lst, that's a lower case L in menu.lst, not a one!

---

