---
title: "Please confirm my attempt at dual boot w/W8.1 on SSD..."
date: 2014-05-12
forum: New to Ubuntu
---

### Post by CoronaRay on 2014-05-12
Hey all, brand newbie here,

When I installed W8.1 in my Samsung 840 240GB SSD, I used the entire allocated disk space.  I have 3 totally used partitions.  I did not leave myself any other free unallocated partitions space .

My question is:
1) Can I install Ubuntu in my SSD?  Will the Ubuntu installation process automatically shrink my W8.1 OS and create a new partition to install my Linux OS? 
2) Also, it is my understanding that in my new Ubuntu partition, that I will need other partitions for the UEFI and swap.  Is this possible being that that you can only have 4 primary partitions?  Won't my other partitions be converted in either logical or extended partition?

Note:
 Fast boot is turned off.
Secure boot is turned off.
My boot order has my flash drive 1st, SSD 2nd

Am I missing any thing else?  I am trying to insure a smooth Ubuntu installation.

Thanks in advance for your expertise.

---

### Post by CoronaRay on 2014-05-13
I tried installing Ubuntu by DVD without having partitioned my SSD and with having created a 40GB partition.  In both cases I did not see an Ubuntu icon, nor did I anything activate.  Windows 8.1 turned on as normal.  I took a look in my Disk Management and saw my new 40GB partition.  It still showed as 'Unallocated'.  However, Ubuntu did show as having been installed under 'Control Panel'.  So, I just uninstalled it.

Hmm, I guess I can only install Ubuntu and run the Demo from a a flash drive and not the DVD.

---

### Post by squakie on 2014-05-13
If you found ubuntu under windows contol panel, it means you did what is called wubi install which is sort of like "ubuntu on windows".  This is no longer supported - the installation may allow it but it is no longer supported and in particular with Windows 8.  True dual booting means 1 or more separate partitions for Ubuntu, going through the normal (not wubi) installation process and selecting that/those partitions to install to.  This will in turn, when finished and rebooted, provide you with a menu at boot time to select Ubuntu or Windows.  I'm not familiar if there are any (other than the obvious) differences in a SSD that would not make this possible with the SSD.

Since you also have Windows 8, you may want to read some of the many threads on the forum for dual-booting with Windows 8 as there are things you need to be aware of prior to starting the install.  Some types of hardware have instructions specific to them.

Also, when shrinking a Windows partition - in this case to make room for Ubuntu - that:

(1) in Windows, defrag the disk - a couple of times doesn't hurt.  This helps reduce the potential for data loss.
(2) the partition is shrunk using Windows and the Windows tools - like disk management
(3) reboot to Windows a couple of times to be sure any file system "problems" are fixed.  A lot of times after shrinking Windows will initially report a problem and then fix it.

Then you can move on to an install.

What I would suggest>

(1) defrag the disk in Windows
(2) shrink the Windows partition (sounds like you may have already done this)
(3) in the BIOS for your computer, turn off secure boot and turn off fast boot
(4) boot the live media - DVD or USB flash - and select the "Try Ubuntu" option.  Wait for Ubuntu to boot and be sure the screen is okay, hopefully wireless is okay (if not you can at least be prepared to install a driver (*not* the Windows driver) in Ubuntu for it), and in general things seem ok.  If not, stop at this point and post back with questions/problems.
(5) if you are still running from the live media, select "Install Ubuntu" on the desktop.  If not currently running from the live media, boot it and select the "Install Ubuntu" option.
(6) when it gets to the place in the installation where it asks for where you want to install Ubuntu,  select "Other".  This will bring up a GUI'd screen showing your disk(s) and partitions.  Select the new space you created and create a partition of say 2gb (just to start) and set the type to swap.  Add another new partition of 20GB or so as type ext4 and mount point "/".  For now (you can change this later) add another new partition of type ext4 and mount point of "/home".  Then continue on with the installation.  This will give you enough room for adding software since the root partition (the one whose mount point is "/" - root) is sized to at least allow some room.  The remaining 18gb (assuming I've done my math correctly) is where all of you files and data will go.  In the future, if you find you want to continue with Ubuntu, you may want to consider a larger disk to allow for more data, more programs, etc..

Don't worry about the primary/logical partitions "thing".  Windows 8 requires UEFI which requires a GPT (gui'd partition table) instead of the old MBR type.  There is no limitation on "primary" partitions with that.

If you don't see a menu for selecting Windows or Ubuntu upon reboot - post back as there are some things we can have you try.

Here's link to a thread by expert oldfred on uefi, dual boot, etc.:  [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

---

### Post by CoronaRay on 2014-05-13
[ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar1741485_2.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=1741485") 				 				 					 						 	[**[COLOR=#000000]squakie[/COLOR]**]("http://ubuntuforums.org/member.php?u=1741485") Thanks for your reply.  I was actually half way through last time but I backed out when I did know how to treat my partitions.  After having read your reply and watching one other video by a guy who virtually stated the same as you did, everything made perfect sense.  A couple of things:  1) You don't have to defrag an SSD (at least that is what I've read on other sites regarding SSDs.  2) I added a 18GB /, 16GB /home, a 200MB /boot and a 2GB swap.  

Everything starts up as expected.  I get the GUI start up that automatically reverts to Ubuntu unless I select Windows 8.1 with in 10 secs.

Thanks for your help.  I would still be struggling had you not posted.

Thanks again ~ Ray

---

### Post by LastDino on 2014-05-13
Actually, you could've benifited more if you had putted / and /home in same place (i.e Made only / with 34 GB), but that is now a mute point. Just keep a note for future, if you've anything less than 40-50 GB, it's better to keep / and /home in same partition.

Congrats and welcome to Linux world!

---

### Post by squakie on 2014-05-13
I'm just glad you've got it going now - glad I could help. 

If you're satisified with everything, please go to the top of the page, just above the 1st post, click on "Thread Tools" and then on "Mark this thread as solved" (I *think* that's the wording).

Enjoy Ubuntu, and don't be afraid to create threads for ANY questions you might have - that's what everyone is here for. ;)

---

### Post by squakie on 2014-05-13
Allowing the easiest way for maximum usage by system or user data - yes.  Updating to a new release - well, easier to have /home separate - but that's just a personal opinion ;)  All partition schemes are personal choice.

---

### Post by CoronaRay on 2014-05-16
After having read your suggestion of how I could have combined my / and /home in same place, I tried to go back and make those changes.  Of course, I screwed things up.  Fortunately, I had a back-up of my Windows 8.1 on another HDD and re-migrated it to my SSD.  I was basically able to recreate my entire set-up AND became pretty good now at how-to-set-up-Ubuntu.  This time I allocated 80GBs to my Linux partition instead of the 40GBs as before.  4GBs to my swap.  50GBs to my /.  400MB to my /boot.  

Needless to say, I was a little bummed out after I realized what I did but now everything is working better than ever.

I think now I can hit the 'SOLVED' button. :)

---

