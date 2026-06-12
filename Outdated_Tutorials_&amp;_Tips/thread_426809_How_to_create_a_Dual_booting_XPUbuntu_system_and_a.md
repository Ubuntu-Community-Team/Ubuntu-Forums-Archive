---
title: "How to create a Dual booting XP/Ubuntu system and avoid problems.."
date: 2007-04-28
forum: Outdated Tutorials &amp; Tips
---

### Post by tibetanpunk on 2007-04-28
Ok, I had some problems with a dual booting OS which meant I had to reformat and reinstall both XP and Ubuntu. I seem to have resolved this issue by myself. I will explain how I was able to do it here and how to avoid the problems I had first time I tried (using my brand spanking new dual booting Ubuntu install as I type this!!!).
First, you need to make sure that your Windows XP installation is on Dev/Sda1 or Hda1, you can check this when you run the emulated Ubuntu that you can boot from the cd before you go ahead and install.

When you boot from the Ubuntu cd, begin your install as normal, select your location, name etc. until you get to the partitioning tool within Ubuntu.
From here, identify the partition (if you have more than one already) that contains your XP system files, it should be labeled 'Sda1' or as other people seem to see it 'Hda1'. If you only have one partition you should be sweet, you can simply resize the one you have as long as you have compacted all the files so that they are all at the start of the drive (using windows defrag or equivalent).

This is IMPORTANT, if your XP system partition is not registered as 'Sda1' or 'Hda1' within the Ubuntu partition manager, quit the install for now and go and back up all of your XP related files because you will need to do a fresh install of XP in order for the dual boot to work correctly.
That is unless you are very computer savvy and can work out how to resolve the issue when XP freaks out and refuses to load any more after you install Ubuntu.

If your XP system partition is Sda1 or Hda1 you are good to go, when you go to the next stage of the installation it will automatically recognize your windows XP installation and ask you if you want to import your profile from XP to the Ubuntu OS. I chose to let Ubuntu import my profile from windows XP. Then simply wait for the install to finish and restart, both XP and Ubuntu should be fully working and you now have a dual OS booting system! Congratulations! Give your self a nice pat of the back...And relax.

Ok, now for the people who were not so lucky... If your XP installation did not show up as Sda1 or Hda1 (like when I first tried to do this and it went horribly wrong when I installed Ubuntu, rendering XP useless) and you don't know much about command lines and such in order to fix the problem, well...Sorry, it looks like you are going to have to reinstall XP. So you are going to need a working copy of XP to reinstall from and you should probably back up the hard drive you are planning to re-install/reformat.

The way I did it was like this on an 80 gig hard drive:

1. Boot from the windows XP disk.

2. Follow the prompts to install XP until your get to the XP partition manager screen.

3. Create a 12 gig partition for your XP install (follow the prompts on screen that explain how to do this if you don't know).
(delete previously made partitions if there were any. Follow the on screen prompts to do this)

4. Create 2x 20 gig partitions for data back up (my personal preference is to have most file types on separate partitions. One for games, one for videos, music etc, though you could just make your XP partition much bigger if you don't care)

5. Create a 10 gig partition for your Ubuntu (which you will install later).

6. Create a 2 gig partition for the Ubuntu Swap file.

7. Create a partition with the remaining space that you can later use as your FAT32 shared OS folder (there should be about 12 gigs left on the drive).

Still with me? Good.

Begin your XP installation as normal until XP is installed. Done.
Boot into windows, right click 'My computer' and on the menu that appears click on 'Manage'.
Maximize this window and then click on 'Disk management' which is on the little program tree on the left hand side of the screen. The disk management utility should load.

From within disk management you should be able to format the partitions you have just created. Your XP installation should be the first partition and will be a primary partition, the others will appear as 'unformatted'.
From here you can right click on the 2x 20 gig partitions and then select 'format' from the menu, make sure you have the right drive selected and format them as 'logical' drives, procede past the warning message and then format the 2 20 gig drives, one at a time to NTFS file system (unless you have other plans for them).

After formatting has completed this you should be left with the 10 gig, 12 gig and 2 gig partitions. Now is the time to restart your computer and boot the Ubuntu cd.

My copy of Ubuntu had a slightly different menu system to the ones that I have seen tutorials on, so I was kind of in the dark as what to do. But actually it is pretty straight forward. I selected 'Install or run Ubuntu from the cd' option, the first option on the list and the emulated version of Ubuntu booted up to the OS.

I then selected the install icon off of the desktop and followed the steps to the partition manager. From here I selected 'manual' and continued.
On the next screen it said 'scanning drives' and showed all of the available partitions, my newly installed XP showed up as 'Sda1' (YAY!)

I selected the unformatted 10 gig partition, set it up as ext3 with the mount point '/'

I then selected the unformatted 2 gig partition and set it up as 'swap'

Then I selected the unformatted 12 gig partition and set it up as 'FAT32' with the mount point '/Data'

Then I simply hit next and the install had begun, I played guitar for a little while and chanted 'Om mani padme hung' in tune with the chords and in a little while the installation was done.
Then I restarted my system.

When I restarted I decided to check my XP installation was still good, XP booted as normal and everything was sweet. (YAY!)
I then rebooted again to make sure that Ubuntu was working fine, at first I did get an error message about the screen refresh rate being out of range and I had no picture. So I hit reset on my computer and started Ubuntu in recovery mode, then on the command prompt entered 'startx' and Ubuntu booted normally and here I am writing this for you, the poor confused nerds of the world...lol

Anyway, I am well pleased that I got this to work, I use XP primarily for audio recording, so now I can strip down XP (get rid of all the non-audio applications and services) so that it is nothing more than a hard disk recorder for audio and I can hopefully use Ubuntu for everything else while taking advantage of the stability and security that I hear Linux based systems offer.
I hope that this is useful, and good luck to you!
John

---

### Post by GWoitena on 2007-04-29
You can quickly "reboot" XP by putting Windows into Hibernate mode.  From Ubuntu do a restart, select XP from Grub.  Windows will resume where you left off with all your programs already running without the time and hassle of rebooting.

---

### Post by goodtimetribe on 2007-06-11
I'd like to drop you a thanks for your quick and easy guide. I was kind of cautious about it, but it worked beautifully. thanks again.

\\:D/

---

### Post by tibetanpunk on 2007-09-10
You are very welcome, I am glad that you found the guide useful!
Just to add, I have since removed Ubuntu from my system...I was only really dipping my toe into the Linux water, but it was cool...Especially with Beryl running! I am fairly certain I will return to Linux on a more permanent scale, especially when XP becomes obselete..I have no interest in Vista.
If anyone follows this guide and then decides to get rid of their Ubuntu OS and go back to single boot XP, all they have to do is insert their XP cd (making sure that cdrom is primary boot device in the BIOS) and then enter into the recovery console. When it loads all you do is type 'fixmbr' and hit enter..This will rewrite the Master boot record and overwrite the GRUB bootloader that Ubuntu installs...Then you can safely erase the partitions that are Ubuntu related when you reboot into XP. Again, this is done through the 'Disk management' tool that is mentioned in the above guide and after this you will have your single booting XP back again.
Cheers!

---

### Post by timzak on 2007-09-10
Good job on the tutorial.

I have an alternative system that works well for those with a motherboard BIOS with a built-in boot menu.  On my computer, the BIOS shows a message on power-on that gives me the option to hit F2 to enter BIOS, or F11 to enter boot menu.

What I did was unplug all drives except the Windows drive, then installed Windows on it.  Then I unplugged the Windows drive, plugged in the Ubuntu drive, and installed Ubuntu.  Then I went into the BIOS and set the Ubuntu drive as the 1st boot device.  This way my system boots by default to Ubuntu.  If I ever want to boot into Windows, I hit F11 when I turn my computer on, then navigate to the drive with Windows and select it.  Windows boots.  

I like this because neither OS's boot loader knows about the other, so you don't have to worry about getting the Windows boot loader right, nor do I have to edit GRUB.

This only works if you install each OS on its own hard drive.

Cheers!

---

