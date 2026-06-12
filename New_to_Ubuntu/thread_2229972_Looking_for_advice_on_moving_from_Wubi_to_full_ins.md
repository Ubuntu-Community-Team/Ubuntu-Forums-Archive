---
title: "Looking for advice on moving from Wubi to full install"
date: 2014-06-16
forum: New to Ubuntu
---

### Post by ian49 on 2014-06-16
A few years back, although mainly a desktop pc user, I bought a laptop which came with the abomination Vista pre-installed. At the time I wasn't using the laptop all that much and installed Wubi (10.04) to see what it was like and to get away from Vista. Since that time, I've never used the laptop with anything other than Wubi and I also now use it a lot more than I used to. What I'd like to do is convert my Wubi into a full Ubuntu install and get rid of Vista. However, there's a couple of other factors. One is that I've invested a lot of time with my current Wubi installation and have made numerous additions and configuration changes and I really don't want to have to try and do all of those again, assuming I can remember all the things I did. The second is I'm about to replace the laptop HD which is only 120Mb with a 1Tb drive. So, having said all of that, is there a recommended way to move from the existing 120Gb drive with Vista/Wubi to a 1Tb drive with just Ubuntu, while retaining all the configuration and software I've added over the last few years.

Any constructive help much appreciated.

---

### Post by Bucky Ball on 2014-06-16
Welcome. Get stuck into this:

[https://duckduckgo.com/?q=wubi+to+partition](https://duckduckgo.com/?q=wubi+to+partition)

Once you've migrated it to a partition you could use something like Clonezilla to clone that new Ubuntu partition to a backup device, take the 120Gb drive out, put the 1Tb drive in, boot from a Ubuntu LiveDVD or USB, launch Gparted and create a partition the same size or larger than the Ubuntu partition you just cloned, then use Clonezille to clone your Ubuntu partition from the backup device to the new partition on the 1Tb drive. Simple!

Hope that makes sense! ;) Don't hesitate to ask questions.

Clonezilla stuff:----

Create image:
[http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/](http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/)

Create recovery ISO:
[https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/](https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/)

Partition cloning step by step:
[http://cdonner.com/partition-cloning-with-clonezilla.htm](http://cdonner.com/partition-cloning-with-clonezilla.htm)

Create Live media (with pics):
[http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc](http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc)

You've chosen to migrate at the right time. Please read the new forum policy on Wubi here:

Wubi recommendations:
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

---

### Post by ian49 on 2014-06-16
Thanks for all the info... I'll have a good read of the links you provided and see how I get on. Might be back with some further questions in a few days time :)

---

### Post by Impavidus on 2014-06-16
At the same time move from 10.04 to at least 12.04 but best directly to 14.04, as 10.04 is unsupported and can break at any moment (in fact, has broken already for many people) and 12.04 is getting a bit older (although perfectly usable) and moving to 14.04 directly saves you an extra upgrade. But given the amount of changes from 10.04 to 14.04 I doubt that migrating and upgrading is easier than a fresh install.

---

### Post by ajgreeny on 2014-06-16
As you are using wubi 10.04 on the small drive I would recommend that you forget about migrating the wubi install to partition, as once you have done that you will immediately need to clone it and move it, then upgrade it to a newer version; 10.04 has been out of support for over a year now and it will therefore be a security risk to keep running it.  That double-action, time-wasting procedure hardly seems worth doing in my opinion.

I suggest you do a clean partitioned install straight onto the new, large hard disk after having backed up all your personal files and folders from the wubi home folder on to a USB drive so that you can restore everything after the install, thereby keeping all your personal configurations.

If you need more help on doing this, come back again and we can help you out.

---

### Post by squakie on 2014-06-16
+1.  My understanding is that you can't update directly from 10.xx to 14.04 anyway - you'd need to do progressive updates, that, at least in my opinion, will be big time wasters and the chances of having a decent configuration after all those release upgrades isn't the best.  

You also may want to check the minimum requirements for Ubuntu now - processor, memory and especially graphics.  A LOT of changes have happened since 10.04, and it has become much more graphics "heavy".  I would suggest:

- download the newest Ubuntu, but 32-bit, burn the install media and try booting it, selecting "Try Ubuntu" and see if it will even boot.

With hard ware that old you may be better off with lubuntu or xubuntu, but try the above first.

---

### Post by Bucky Ball on 2014-06-16
@squakie: LTS upgrades to LTS, so 10.04 LTS>12.04 LTS>14.04 LTS. But not sure if the upgrade from 10.04 LTS to 12.04 LTS would still be available.

Anyway, by rights I should be closing this thread as it deals with both an EOL release and Wubi, neither of which we are officially supporting on these forums anymore (see link I provided earlier), so I think the best bet is to do a clean install of 12.04 LTS or 14.04 LTS. Bit of a drag about the settings, but 10.04 LTS has been out of commission since last April and should have been upgraded long ago ...

---

### Post by hakuna_matata on 2014-06-16
My suggestion:

- Use the script from [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
- Copy your /home to a separate partition (it is a feature of the script)
- Install Lubuntu 14.04 without deleting your /home partition with your personal data

---

### Post by ian49 on 2014-06-16
That I can't salvage my existing configuration is somewhat depressing but I guess it's the reality based on the comments made so far.

My laptop had no problem running 14.04 but I found the Unity interface hideous and really don't want to run it. Is there a version of Ubuntu that I can install that resembles 10.04 in terms of interface if nothing else?

---

### Post by oldfred on 2014-06-16
wubi is Ubuntu, so you can backup /home and a list of installed apps and reinstall that into your new install.
This is what I back up as a desktop user.
       [http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
    
I install full Ubuntu because I want the default apps. But my 2006 laptop does not have enough of a graphics driver to support Unity, so I install fallback/flashback. How it installs and names have changed as underlying software is different. But basic menu system (some items have moved) and top & bottom panels are still there. Some extra tweaking required to make it fully functional. I only do a few of the changes suggested in the tips & tweaks posts.

       sudo apt-get install gnome-panel
On login screen click on logo/cog-wheel/star and choose 
[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)
12.04 LTS / Precise Classic (No effects) Tweaks and tricks kansasnoob & cortman
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

For 14.04 it is similar, but the tweaks are somewhat different.
      
 Flashback/fallback in 14.04 Kansasnoob
Installing the package 'gnome-session-flashback' does exactly the same thing as installing the package 'gnome-panel'.
[http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264)
[http://ubuntuforums.org/showthread.php?t=2090021&p=12994477#post12994477](http://ubuntuforums.org/showthread.php?t=2090021&p=12994477#post12994477)
[http://ubuntuforums.org/showthread.php?t=2184682&p=12986002#post12986002](http://ubuntuforums.org/showthread.php?t=2184682&p=12986002#post12986002)
[http://ubuntuforums.org/showthread.php?t=2184682&p=12971487#post12971487](http://ubuntuforums.org/showthread.php?t=2184682&p=12971487#post12971487)
    


 Classic, fallback, flash back explanation -  by kanasnoob 
[http://ubuntuforums.org/showthread.php?t=2185161](http://ubuntuforums.org/showthread.php?t=2185161)

---

### Post by ian49 on 2014-06-16
> **hakuna_matata said:**
> My suggestion:

- Use the script from [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
- Copy your /home to a separate partition (it is a feature of the script)
- Install Lubuntu 14.04 without deleting your /home partition with your personal data

I'm not sure I understood this. Does the script install Lubuntu "around" a pre-existing /home folder?

---

### Post by ian49 on 2014-06-16
> **oldfred said:**
> wubi is Ubuntu, so you can backup /home and a list of installed apps and reinstall that into your new install.
This is what I back up as a desktop user.
       [http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
    
[snip]


Thanks for responding. I'm just trying to get my head around what you've suggested. My knowledge of the finer points of Ubuntu isn't that great so I'm not sure I've understood correctly.

I understand the bit about backing up a selection of directories and then (presumably?) copying them back to the new installation and I can see how that will restore much of the actual data but how do I go about re-installing the software I've been using. For example, one of the programs I run is Calibre (I'm involved in an ebook publishing business) and I have detailed settings for all the various ebook formats configured in the sofware which I've fine tuned over the last 3 years. Will copying the directories that need to be backed up and then restoring them mean that such software and its settings are then available on the new install?

My other question was in regard to Unity. No doubt a lot of people like it but I hate what I've seen of it, I assume there are a number of ways to get rid of it and get Gnome back? How well does that work because personally I'd rather go back to using Windows than be forced to use Unity.

---

### Post by oldfred on 2014-06-16
All your settings are in hidden files & folders in /home as well as all your data unless you save it someplace else.
But copying /home does not reinstall an app.

But when going from an old version like yours to a new one, you may have lots of apps you do not want to reinstall. If so old as to be not available it just will not reinstall.

Often better to review list that it creates or export a list of top level only apps as the entire list is over a 1000 as it includes all the supporting files as well for each app.

As posted above gnome-panel gives you the old style look and feel but based on new underlying software so some changes. You can try other flavors. If older hardware Unity may not run or run well anyhow. Many suggest Lubuntu, but I find gnome-panel works on my older laptop.

       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

If you have used ppas or external sources those will not be reinstalled.


 Top level only - no depends (not for reinstall)
sudo apt-get install aptitude
aptitude --disable-columns -F '%p' search '~i!~M!~R(~i)' > toplevel

---

### Post by Bucky Ball on 2014-06-16
I don't like Unity either. You might like to try Xubuntu or Lubuntu, or a minimal install with the desktop environment of your choice (in this case, xfce4 or lxde).

---

### Post by squakie on 2014-06-17
+1.  I made that comment in my post as well as it could well be that hardware that old either won't support Unity or won't run it very well.

---

### Post by Impavidus on 2014-06-18
My favorite is xfce4, which is the interface you get with Xubuntu. Depending on the exact hardware (graphics mostly), Win Vista-era computers can be quite capable of running Unity (my brother has such a laptop with an nvidia card, no problem with Unity), but sometimes are not. But as you don't want it anyway it doesn't matter.

The configuration of most of your applications is in hidden files and hidden directories in your home directory. If you back them up and copy them to your new installation, most of them should still work and give you your old configurations back. But you'll get four year more recent versions of your software. The new programs have new options for configuration and some old options may no longer work. Some applications may be completely gone and have to be replaced by alternatives.

Calibre is still available and now at version 1.25.

---

### Post by hakuna_matata on 2014-06-19
> **ian49 said:**
> I'm not sure I understood this. Does the script install Lubuntu "around" a pre-existing /home folder?
[This script]("https://help.ubuntu.com/community/MigrateWubi") copies your current installation to real partitions. Doing this it is possible to split one virtual partition into two or more real partitions. So you can create a separate partition for folder /home.

That was the part of the script. 

The remaining part (my suggestion of an installation of Lubuntu 14.04) refers to standard installation. There are a lot of options. One option is that you can choose pre-existing partitions and that you don't format partition for /home.

---

### Post by pingadam on 2014-06-20
You may also want to try Linux Mint 17 "Qiana" LTS, which is based on Ubuntu 14.04 "Trusty Tahr" LTS, but has different desktop interfaces: a choice between Cinnamon (I'm currently using this one - this is probably the best choice for a modern but "Windows 7" style desktop) and MATE (which is almost identical to GNOME 2 on Ubuntu 10.04). Also, KDE and XFCE versions of Mint 17 are currently being tested and will be released soon. The next versions of Mint (17.1, 17.2, ... etc) for the next 2 years will all be based on Ubuntu 14.04 LTS, until Mint 18 which will be based on Ubuntu 16.04 LTS (due for release in April 2016 - so Mint 18 will probably arrive in May/June 2016). Anyway, I just thought it's worth you looking into that.

As for Calibre - the latest version 1.40 is available via a terminal command: [http://calibre-ebook.com/download_linux]("http://calibre-ebook.com/download_linux")
So you can easily re-install on your fresh Mint (or another flavour or derivative of Ubuntu) installation.
However, you may want to backup /opt/calibre (this is the default location for installation I believe) in addition to your /home folder, in case any of your customisations & tweaks are stored there, before wiping and installing a new system.

Have a look at the Calibre website ([http://calibre-ebook.com]("http://calibre-ebook.com")) for more information. They also have a forum that you may be able to browse or post a request for more information etc: [http://www.mobileread.com/forums/forumdisplay.php?f=166]("http://www.mobileread.com/forums/forumdisplay.php?f=166")

Hope this helps anyway... Good luck!

Kind regards,

Adam.

---

