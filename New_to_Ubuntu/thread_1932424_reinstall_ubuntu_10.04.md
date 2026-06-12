---
title: "reinstall ubuntu 10.04"
date: 2012-02-27
forum: New to Ubuntu
---

### Post by geobm on 2012-02-27
E-machines 250 netbook. Have previously installed 10.04 OK using Wubi .  Wanted to try 11.10 but didn't like the interface so tried to re-install 10.04 but did a system factory restore first.
Now get message "No root file system is defined.  Please correct this from the partitioning menu".  (Also had same problem with Mint).  
I've no idea what this means or how to do the correction. Any simple help for a novice greatly appreciated, please.

geobm

---

### Post by Double.J on 2012-02-27
Hi there Geobm,

Please forgive me, but I got a little confused, do you mean that you:
installed 10.04 via wubi,
installed a full copy of 11.10,
reinstalled windows,
now trying to install 10.04 from CD?

Just to clarify is this an error message you are getting during the installer? It sounds like an installer error message; it's basically saying that you haven't told the ubuntu installer where to install the operating system. 

The message comes up for mint and Ubuntu because they are so similar that they actually use the same installer program.

Usually when you install, the first options you are given are to install alongside windows (if you have it) install over the whole disk, or something else (you may get more options if you have more operating systems) I'm assuming that you are getting this error after choosing to do "something else" and being presented with a table of partitions on the hard drive? If you are getting this message from one of the other options for whatever reason, try choosing something else and performing a manual install.

Once in the partition editor, you need to have free space for ubuntu. if you only have once solid windows partition across the whole hard drive, select it by clicking on it, then click the "change" button on the bottom menu. set the new size of the partition to create room for Ubuntu. As a rough guide ubuntu should be 20GB plus twice your RAM  and windows 7 50GB or more if you have the space (don't shrink the windows partition too much)

Once you have created the free space, make a swap partition by clicking the free space, then "add" from the bottom again. set the size to be twice the size of your RAM, and format as SWAP - the bottom box will now blank out and you can click done.

With the rest of the free space create another partition to take up all that space (if that's how you want it) and format as EXT4, now set the mount point as / and click done.

Finally check that grub is going to install in the correct place in the drop down list at the bottom of the window - you almost definitely want /dev/sda as the location then continue the installation. Hopefully this time it will go through without error

Hope it helps!

---

### Post by Andrew_P on 2012-02-27
> **geobm said:**
> E-machines 250 netbook. Have previously installed 10.04 OK using Wubi .  Wanted to try 11.10 but didn't like the interface so tried to re-install 10.04 but did a system factory restore first.


If you've resigned yourself to rebuilding the system from scratch, I'd suggest getting the latest ISO file of Lucid Lynx and burning a new LiveCD.  Release 10.04.4 LTS is available now; see [http://releases.ubuntu.com/10.04/](http://releases.ubuntu.com/10.04/).  Using a later version of the release will bypass having to install 200-300 patches and updates after the basic installation is completed, said updates taking as long or longer to accomplish than the system installation takes.

---

### Post by geobm on 2012-02-27
Sorry if attempt at brevity confused.

I have previously installed 10.04 alongside Win XP using Wubi.
Removed it and installed 11.10 also using Wubi with XP. Not liking the new interface decided to go back to the LTS version, so to have a clean machine, restored it to factory settings.  Then installed a freshly downloaded version of 10.04.4, again using Wubi, which seemed to go normally as in the past.  
On rebooting, I had the usual choice of Windows or Linux and it was after choosing the latter that Ubuntu seemed to start loading normally but then the quoted messages appeared.
The OS seems to have installed since it appears in the Win uninstaller as the size to be expected - there is just presumably a small glitch preventing it from starting.
Every time I've installed Linux there are the same three options, ie replace Windows, install alongside Windows (which I always choose) or run from the CD I've burned, so nothing has changed there and the various stages of the installation are, I'm sure, exactly the same, which is why I''m baffled.
(Incidentally, I did realise that Mint is an Ubuntu derivative).
Has this helped clarify my problem?

---

### Post by 23dornot23d on 2012-02-27
If you run the bootinfoscript ...... [[COLOR=Blue]_**LINK**_[/COLOR]]("http://bootinfoscript.sourceforge.net/")

It will give us more information about how the disk is setup  ..... cut and paste the results back in code tags please.

---

### Post by geobm on 2012-02-28
Thanks for reply 23d, but I've just uninstalled Ubuntu.  Have NOT given up, but when I try again, I will do as you suggest if still no success.

---

### Post by geobm on 2012-02-28
Hello All,

Have decided, after all, to go the whole hog and install Ubuntu alone.  This worked perfectly.  I know there will soon be a new LTS version out, so I will probably have to update. I only hope it has the option of the Gnome interface which I am used to and prefer.
Windows XP had served me well since it came out, but its life will soon be over and (as a long time pensioner) I've no intention of paying out for a new MS system. I've used Firefox, Thunderbird and Open Office for years (by choice) so I'm not sorry to change.

So long and thanks for your attention.

geobm

---

### Post by asifnaz on 2012-02-28
It is always a good idea to install Ubuntu on real partition instead of Wubi . Good Luck

---

### Post by Mark Phelps on 2012-02-28
> **geobm said:**
> ... I only hope it has the option of the Gnome interface which I am used to and prefer.

Sorry, but Canonical has pushed us all into Unity -- that's their choice.

IF you want current Linux features but WITH Gnome, then you should be looking at Mint.  They may be sticking with Gnome for a while.

---

### Post by geobm on 2012-03-01
Thanks Mark.
Have tried Mint in the past and liked it.  Hope they do stick with Gnome, in which case I may go back there if no alternative.  It will help keep my brain in action, anyway, as it's starting to slow down in the upper 70's!!

---

