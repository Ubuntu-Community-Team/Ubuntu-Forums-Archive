---
title: "How to 'replace' xp with lubuntu? CD seems to install dual boot - or does it ?"
date: 2014-05-28
forum: New to Ubuntu
---

### Post by fran_3 on 2014-05-28
We want to re-purpose several xp machines with 1GB of ram and 'replace' xp with Lubuntu.

After creating the ISO CD and booting from the CD and selecting 'install lubuntu' I don't see an option to reformat the hard disk so that lubuntu is the only system on the disk.

What is the proper way to do this?

Thanks for any help.

---

### Post by monkeybrain20122 on 2014-05-28
"Replace" should be the first option. But then I read somewhere that there is a bug in the installer, may affect only Lubuntu(?) Anyway, you can choose "something else" which allows you to specify your hard drive layout manually, when the partition layout shows up make the changes you want. Also remember to create a swap partition as you have only 1G of ram (make the swap around 1 G as well)

---

### Post by mörgæs on 2014-05-28
Please tell step for step what you see when trying to install.

It's very unlikely that the installer is buggy when setting up a single boot system.

---

### Post by fran_3 on 2014-05-28
maybe I didn't get far enough into the install to see the option to 'replace' or the option 'something else'

the first menu gives me the choice to 'try' or 'install' and I choose 'install'

one or two clicks later I did not see (or missed) the prompt to 'replace' the existing os with lubuntu.. so I canceled out thinking it was going to install lubuntu as a dual boot os.

should I just charge ahead and retry the install?

AND... is there a bug as monkeybrain20122 mentioned? Now I'm nervous.

Thanks for any help.

---

### Post by monkeybrain20122 on 2014-05-28
I read on this forum may be a month ago that there is a bug where sometimes Windows is not  being picked up and the result of which is that Windows gets wiped out. But I think it has to do with Win8 and UEFI. Now since you are going to wipe XP anyway what is there to worry about?  Just go ahead:) If you only make one or two clicks chances are the partition table hasn't even shown up yet.

---

### Post by fran_3 on 2014-05-28
OK, I'll charge ahead tomorrow and report back. Thanks for the help.

---

### Post by Bucky Ball on 2014-05-28
Yep, just do the install as per normal and you WILL get to the partitioning section. THEN you will see the option 'Something Else' where you can manually create your partitions. Once there, firstly wipe the XP partitions then partition the disk as you want for Ubuntu. Something basic would be:

/ = for the OS, maybe 10-15Gb (but with Lubuntu you might not even need that;
/home = your data and settings, large as you can;
/swap = 2Gb at the end of the disk is fine.

Having the separate /home makes backups easier and if you want to do a clean install to upgrade or for any other reason later, that is easier, too. Good luck. ;)

---

### Post by Rex Bouwense on 2014-05-29
I just returned from installing Lubuntu 14.04 on my son's fiance's computer.  It is not difficult.  You will probably run into just one minor problem, the nm-applet will not be displayed in the LXPanel.  There is an easy solution after you have installed.  Go to menu->Preferences->Default applications for LXSession.  Navigate to Core applications and under Network GUI, type nm-applet.  Then navigate to Autostart and then Add nm-applet.  The nm-applet should then appear in the LXPanel and will be there when you reboot.

---

### Post by paul142 on 2014-05-29
It should have the options to run from the CD, fresh install, or dual boot. Move forward on the install and those options should be proposed.

---

### Post by stalkingwolf on 2014-05-29
just select replace and tally ho.  if the option presents also install the 3rd party stuff if you will need them.

---

### Post by fran_3 on 2014-05-29
OK, I tried this again and have some questions. Here is what happened...

- Got to the "installation type" screen and selected "something else"
- On the next screen I see...
/dev/sda
/dev/sda1 ntfs
and I click the button "new partition table' to create the three suggested partitions... 20GB for the os, 18GB for the data, and 2GB for the swap disk.
- then... when notified that I'm about to wipe everything... I click on "Continue"
-next screen shows...
/dev/sda
fee space 40060 MB
- I click free space and then "+"  AND now I'm asked what type of partition and I leave the defaults of Primary and Begining of the space...
- BUT then I have to specify "Use As" and get a list of choices...
.. Ext4 journaling file system
... Ext 3 journaling file system
... etc
BUT... I don't see any choice that says put the operating system in the first partition...
Or make the 2nd partition the data partition
(I do see a 'swap area' choice but that is for the 3rd and last partition)

My question... which of these choices do I choose to get the OS in the 1st partition and the data in the 2nd partition?

Thanks for the help everyone... I think I'm almost there.

---

### Post by mörgæs on 2014-05-29
Having a separate /home, as you are about to get, makes it easier to reinstall in the future but there is also a certain loss because the / (root) partition needs to have some open space. I would say that 10-12 GB is enough if you remember to delete unneeded packages once in a while.

If you want to get up and running quickly you could also let Lubuntu do the partitioning for now. When you are more experienced after some time you could reinstall and create the separate /home.

---

### Post by monkeybrain20122 on 2014-05-30
File type should be Ext4.

The boot flag for the operating system is /, for home obviously it is /home. 

Just go ahead, worst you only need to do this again, it doesn't take that long.

---

### Post by fran_3 on 2014-05-31
Got it working!

Windows XP has successfully been replaced by Lubuntu 14.x, the Chrome browser is installed, and Home and Trash Icons have been placed on the desktop.

I ended up doing the default install but checked boxes for _download updates, _install packages, and _Logical Volume Management.

More Lubuntu post and questions on appropriately titled threads.

Thanks all.

---

### Post by Bucky Ball on 2014-06-01
All good. Please mark the thread as solved to help others.

As monkeybrain20122 mentions, when you were at the manual partitioning section of the install after hitting 'Something Else' you simply needed to create a 10-12Gb partition, EXT4, and Ubuntu 'automagically' knows that '/' is where the OS goes and that's that. Same with /home. The install will create your 'documents' folders like Music Videos Pictures etc. in /home partition (which should also be EXT4, the /home mount point is a default you can select). /swap partition takes care of itself as soon as you select to use it as (2Gb) 'swap space'; you don't need to set it as EXT4 .

Anyways, nice to hear you have it up and running and welcome to the swim. ;)

---

### Post by corey13 on 2014-06-02
I went through this last night. Here is how I did it.
1 * Make backup of all your files
2 * Download lubuntu 14.04
3 * Burn ISO file to unformatted CD (so it all fits, it's a 689mb file I believe it was)
4 * Put CD in drive
5 * Reboot computer - Tap F2 as it loads.
6 * Go to BIOS and set it to run from CD/DVD instead of Internal HD.
7 * Gives an option to delete Windows and install Lubuntu > Check this
8 * Follow prompts, takes about 10 minutes to fully install
9 * Restart computer at prompt
10 * Log in with password you made (if you didn't check auto-sign in) and enjoy!


Hope this step by step approach works for you!

---

