---
title: "Is it time to switch from 10.04 LTS to 12.04 LTS???"
date: 2012-08-26
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2012-08-26
I have been running Lucid Lynx for about two years and it works great. Today my Update Manager said a new release (12.04 LTS) is available. I decided to do the upgrade but halted it when I saw the protracted download time of nearly 4 hours. 
Question 1: Would it be wiser to wait another 6 months or so?
         2: Do I need to check my pc for memory availability?
         3: Would it download the files faster at nite or through a                    certain server location? Or is getting a CD the better option?
         4: Any precautions I need to follow before upgrading?

I have limited Linux experience, not a programmer but can operate in terminal mode etc. 
Thanx to the Gurus for helping out an elderly Linux lover,

Ed

---

### Post by ratcheer on 2012-08-26
Do you have a separate /home partition, or just a single root partition with home as a sub-directory on it?

If you only have a root partition, my recommendation would be to make a good backup of your home directory, then do a clean install of 12.04, then immediately restore the home directory.

If /home is on a separate disk partition, I recommend a "dirty install", which is a clean install of 12.04, except you instruct it not to reformat your /home partition.

Both of these methods require reinstallation of your non-standard applications, but all their settings, bookmarks, etc will remain intact. These methods will certainly be much faster than an upgrade and the resulting installation will probably be more stable and problem-free.

Let me know and I will try to lead you through whichever way you choose.

Tim

PS - I am an old guy, too! ;)

---

### Post by Peripheral Visionary on 2012-08-26
A fresh install is *always* better than the upgrade! Upgrades are infamous for failures and "partial" upgrades and such. Very frustrating, and many folks who have tried the upgrade and run into problems have quickly solved them with a fresh new installation from the LiveCD.

I have an 80 GB hard drive and I use a separate "/home" partition to preserve my bookmarked favorites, e-mail settings, desktop settings, and all my personal stuff like documents, music, and pictures.

Mine is set up like this:

[COLOR=Purple]**/linux swap**[/COLOR] is 1 GB (double my machine's RAM)

[COLOR=Purple]**/ **[/COLOR]is 20 GB big, more than enough room for Xubuntu, which only really uses about 1/4th of that

And the rest of the drive, a bit less than 60 GB, is [COLOR=Purple]**/home**[/COLOR].

When I do a fresh install I simply *uncheck* the "format this partition" box when setting up the partitions, and it preserves all my stuff!

Still, always back up just in case!

---

### Post by grahammechanical on 2012-08-26
You should also review this:

[https://help.ubuntu.com/12.04/ubuntu-help/index.html]("https://help.ubuntu.com/12.04/ubuntu-help/index.html")

It is the 12.04 Ubuntu Desktop Guide. It will be installed when you upgrade. Just type help in what is called the Dash. But you should examine what you will get when you move to 12.04.

And that is another reason for doing a fresh install. Not only are there differences to the look of the desktop but there is a big change to the libraries that are used underneath the desktop. If you have modified your desktop then you may have problems with the upgrade.

I would suggest that you make the desktop as basic or default as possible.

You should also notice that you still have support for 10.04 until April next year. So, you do not have to upgrade if you do not want to.

[https://wiki.ubuntu.com/Releases]("https://wiki.ubuntu.com/Releases")

Regards.

---

### Post by oldfred on 2012-08-26
I always suggest you have a current version liveCD so you can make repairs, so you should download 12.04.1 anyway and try it out to see the changes and that it still works with your system. Some like the new Unity, it does take getting used to and others use gnome fall-back which is like your current menu system.

I prefer clean installs. In addition to a good backup of /home you may want to make a list of installed applications. But my lists from previous installs also had obsolete software which was not reinstalled and some old versions like python2.5 and OpenOffice which now is LibreOffice. You do not need the old versions.

Mine is just a home system and I just plan a clean install and restore my data from backups. So my backup plan is most of what you should have. Of course you may have some other things also.

Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

### Post by Bashing-om on 2012-08-26
--hillbilly;


  +1 to the above post.... clean install from live CD ..backup/restore any desirable files/configs ect. I also am happy with 10.04 .. and contemplating the upgrade ...my path is going to be to install 12.04 on another hard drive and dual boot for a while!

[INDENT]    my regards <==BDQ

[/INDENT]

---

### Post by aPanzerIV on 2012-08-26
adding to the above post, If you don't have a hdd laying around you can always repartition your disk without messing up your install from the 12.04 install disk, havn't tried it yet but it sounds cool :D

---

### Post by oldfred on 2012-08-26
I cheat to and put the new install into another 25GB root partition. Then if I have forgotten anything I can go back.

It just is now my 3 year old 'new' drive is filling up with 25GB partitions. :)

---

### Post by ozark_hillbilly on 2012-08-26
> **ratcheer said:**
> Do you have a separate /home partition, or just a single root partition with home as a sub-directory on it?


Let me know and I will try to lead you through whichever way you choose.

Tim

PS - I am an old guy, too! ;)

Tim & Others,

Attached is a screenshot of my GParted tool. It looks like I do have a /home partition.
I want to go the route of little to no headaches and it would be great if that can be accomplished without messing with my /home partition. My biggest problem is that I only do this stuff every couple years and forget most everything I did the last update. So everyone's input is welcome.  -Ed

---

### Post by oldfred on 2012-08-26
You are not using 97GB of your drive.

I might move the right of the extended partition sda2 all the way to the end of the drive. Then make a new 30GB ext4 partition for your new install and use the rest for a shared NTFS data partition.

Then after you get used to, everything converted you can convert current install's root partition to data or save for future / (root) for next install.

You then use manual install, choose new partition for / and reformat to ext4, choose existing /home but DO NOT select reformat or any change to format. If you use same userid & password it will work without any issue, otherwise some changes may be required.

The only issues should be minor, if you boot into old install and some new settings may not work with the older versions. 

Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by ratcheer on 2012-08-26
Yes, you do have a separate /home partition.

So: 1) Download the 12.04 LiveCD and burn it to a CD or DVD. It may require a DVD due to size, I'm not sure.
2) Boot the CD or DVD. You can either let it boot all the way to the Live desktop and install from there, or I think there is a selection to install it as it is booting up.
3) When you get to the disk partitioning step, select your current root partition and tell it to use it as root and to format it. This will give you a completely fresh install of 12.04.
4) Select the /home partition and tell it to use it as /home. However, make sure the check box to format it is NOT checked.
5) Proceed with the 12.04 installation. Reboot when it instructs you to.

As you are using your new system, you will probably occasionally come to an app you used to have that is not installed. Just install it, and then when you run it, it will pick up on your previous settings from your non-overwritten /home. You will still have any data that was stored under /home.

I have done it this way at least twice before. It's a great way to clean install while acting like an upgrade.

Good luck. Let us know how it turns out.

Tim

PS - Do not change the hostname or your main userid from what you were using with 10.04.

---

### Post by mansonfan78 on 2012-08-26
I notice you have a very small swap partition, now would be a good time to resize it.  It should be at least as big as your physical ram, even if you never use it.

---

### Post by ozark_hillbilly on 2012-08-27
> **ratcheer said:**
> Yes, you do have a separate /home partition.

So: 1) Download the 12.04 LiveCD and burn it to a CD or DVD. It may require a DVD due to size, I'm not sure.
2) Boot the CD or DVD. You can either let it boot all the way to the Live desktop and install from there, or I think there is a selection to install it as it is booting up.
3) When you get to the disk partitioning step, select your current root partition and tell it to use it as root and to format it. This will give you a completely fresh install of 12.04.
4) Select the /home partition and tell it to use it as /home. However, make sure the check box to format it is NOT checked.
5) Proceed with the 12.04 installation. Reboot when it instructs you to.

As you are using your new system, you will probably occasionally come to an app you used to have that is not installed. Just install it, and then when you run it, it will pick up on your previous settings from your non-overwritten /home. You will still have any data that was stored under /home.

I have done it this way at least twice before. It's a great way to clean install while acting like an upgrade.

Good luck. Let us know how it turns out.

Tim

PS - Do not change the hostname or your main userid from what you were using with 10.04.

Tim,

The process you described seems very straightforward. As soon as I get the nerve up I will take the plunge. Something in the back of my mind says "If it ain't broke don't fix it!"

Someone else suggested increasing my swapfile size. Is that a good idea as well?

Ed

---

### Post by oldfred on 2012-08-27
More swap is probably better. How much RAM do you have. If you have lots of RAM like 8GB then you may never use swap. I have 4GB and only rarely use swap, but it depends on how you use system. If you want to hibernate then swap should be at least the size of RAM in GiB (not GB).

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by ratcheer on 2012-08-27
Yes, I agree with oldfred. I have 8 GB of RAM and my system almost never uses swap, but I still have an 8 GB swap partition. The only time I ever recall seeing any of it actually being used was when I was playing around with the zfs filesystem.

Tim

---

