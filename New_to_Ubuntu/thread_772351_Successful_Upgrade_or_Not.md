---
title: "Successful Upgrade or Not?"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Arch Parsons on 2008-04-28
Hello,

I did the auto-upgrade from 7.2 to 8.04 last night.  It stopped after loading all the files and prompted me if I wanted to upgrade. At one point after that it reported insufficient disk space.  Which partition is the main program in? The cleanup step and automatic restart did not complete automatically.  when I rebooted the OS did load. It reported restricted drivers for my NVidia 7300GS video card. I don't know how to set my resolution for the desktop to fit the screen.  Right now I have to use my mouse to scroll across to see all the desktop. My question is this: "Where do I go from here to ascertain if a clean install or rollback is needed?"  I have had Gutsy Gibbons for a few months, but never have figured out how to do very much with it.  How do I ascertain whether or not my upgrade is a bad one and what, if anything, has to be redone? I tried administration upgrades but no further upgrades were shown.

---

### Post by hyper_ch on 2008-04-28
You went on despite it saying there is insufficient diskspace?

Well, if you have not done much with it then I'd suggest a clean installation would be a lot better than trying to fix that.

---

### Post by hyper_ch on 2008-04-28
*double post*

---

### Post by Arch Parsons on 2008-04-28
Thanks for the reply. I don't recall being given a choice as to whether or not to go on. I'm not sure because it was in the middle of the night when I got up to check it.  I think 
the message popped up for a aecond and then the process continued.  The thing is that all seems well now.  I didn't realize that I was in recovery (safe) mode the first time. That may have been the reason for the restriced driver icon for the NVidia card. Perhaps, being that everthing seems ok despite the error messages that occurred during installation, I shouldn't be looking for trouble.  Is there any way to confirm that the upgrade went well, even though it seems to be working fine now? How do I find the amount of disk space remaining where the program files are located? Is there a way to do a manual cleanup that wasn't shown as being done automatically.

---

### Post by Arch Parsons on 2008-04-29
The only problem I have incurred so far is inability to access the Synaptic Package Manager.  I get this error when I try: [B]"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."[/B] I tried 'dpkg --configure -a' in terminal but nothing changed.  I reported the issue as a bug.  I don't know if this indicates a need to reinstall or not.  Is there an easy step by step guide to uninstalling and reinstalling?  I have no idea what to do with the partitions I set up for 7.2.  I don't even know how to tell how much free space is left.  Perhaps I go back into Windows and try Acronis Disk Director to see that info. I have a copy of the alternate cd to burn, but I have no idea how to use it at the stage I am now. Thank you in advance for any comments.

---

### Post by Arch Parsons on 2008-04-29
I tried sudo dpkg --configure -a as suggested from another thread and got the message back, "insufficient space on device."  So how do I go about cleaning things up so that there is space?

---

### Post by wtigerks on 2008-04-29
I NEED HELP i did the upgrade and i can not get compiz emerald to work in 8.04 i hope some one can help

---

### Post by Arch Parsons on 2008-04-29
Hi wtigerks, Perhaps you should start your own thread to avoid confusion here with two different issues ongoing in the same thread. I haven't had a reply here for a couple of days.  Getting back to my previous reply about disk space, I have 1.9 GB swap partition and two EXT3 partitions one of only 47 mb which has 41 mb used up and another of 53 GB that has 7 GB used up. Evidently the problem is in the small EXT3 partition.  I also have a small unallocated partition of 7.8 mb. Should I resize and/or reformat any of these partitions? Thanks again for any suggestions.

---

### Post by meindian523 on 2008-04-29
Please also mention mountpoints of your ext3 partitions.Infact,it would be best if you posted fdisk -l and df -h.

---

### Post by Arch Parsons on 2008-04-29
arch@arch-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              53G  6.4G   44G  13% /
varrun                1.4G  100K  1.4G   1% /var/run
varlock               1.4G     0  1.4G   0% /var/lock
udev                  1.4G  104K  1.4G   1% /dev
devshm                1.4G   12K  1.4G   1% /dev/shm
lrm                   1.4G   38M  1.4G   3% /lib/modules/2.6.24-16-generic/volatile
/dev/sda5              46M   40M  3.6M  92% /boot

fdisk -l entered into terminal did not return a result

---

### Post by forestpixie on 2008-04-29
Did it tell you how much space it needed - I did see one similar thread where the upgrade said how much room it needed.

It would appear that there is not enough room in your /boot partition, whether you have any old kernels in there that can be deleted - or even if it's a good idea I'm not sure, but I'm pretty sure that is where you're problem lies.

Perhaps resizing it and stealing a bit of sda6 would work.

---

### Post by Arch Parsons on 2008-04-29
Thanks for the reply.  No, it didn't say anything like that.  To be sure everything runs smoothly, I would like to do a clean install using the alternate cd which I have burned.  Can you guide me through that process or point me to a step by step guide that you may know of for someone like myself who has a messed up upgrade? Is there such a thing as a roll-back or an un-install for 8.04?  I have Windows XP and Vista on separate partitions on this drive as well. Now, if you feel there is a much simpler way to fix what I have please tell me. The first problem I have discovered so far is inability to access synaptic package manager.  I get the error:  E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report. I did send in a log report on this, but I don't know if they have time to assist each user who submits a bug report. I find it a little peculiar that I ran out of space after following recommended guidelines in sizing my original partitions. I could easity have made the boot partition much larger.

---

### Post by Arch Parsons on 2008-04-29
I increased the size of the boot partition to 2 GB. It loaded a lot of stuff at bootup that never happened before.  The only line that showed fail was something to do with swap.  Now can I redo the upgrade directly by just inserting the alternate cd or what should be my next step?

---

### Post by Arch Parsons on 2008-04-29
I accessed synaptic package manager by typing sudo dpkg --configure -a, I probably could have done that before I increased the partition size if I had used sudo. Do you think my upgrade is ok now that I've increased the partition size of the boot partition?  Are there any things I should or can do to test the installation?

---

### Post by Arch Parsons on 2008-04-29
Sorry for the side track but I tried to install a package called AWN from this page: [http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml](http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml)  When I rebooted all I get is the background image and no menu bar on the top.  I used the first method and tip 3 to remove the Gnome panel.  Is there an easy way to get the menu bar back?

---

### Post by forestpixie on 2008-04-30
Where are you now then - have you upgraded or are you trying to do a clean install. If you're still getting the dpkg error then I would say the upgrade hasn't completed.

I only know of 1 alternate install guide it's here - [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

As far as the size of the /boot partition why did you do one in the first place.

---

### Post by fraser_m on 2008-04-30
As for the gnome-panel problem, just run 'gnome-panel'. Easy. You might need to turn it off as trash in System Monitor.

---

### Post by Arch Parsons on 2008-04-30
Thanks very much for the replies. I am in the middle of nowhere now.  As I said, I lost the menu bar after trying to install that AWN add-on (posted above). I got rid of the dpkg error by using sudo before the suggested command line. Not being able to access terminal or anything else, I tried inserting the alternate cd.  I clicked upgrade and after a time the upgrade process stopped and said no further updates were needed.  As I said I still have no menubar, and right-clicking on the background does not present the option to restore the menu bar. Is "menu-bar" the proper name for it?  Is there a way to bring up the terminal so that I can  run 'gnome-panel' The installation seemed to be ok up until I decided to try that AWN thing. The only thing I noticed different after increasing the size of the boot partition is that on every reboot a list of files opened is displayed before the background screen appears.  All load OK except one line mentioning something about mounting which says "Fail"  I would appreciate any help in getting that menu bar back.  The worse case scenario would be the clean reinstall. Seems to me I need the menu bar to do anything. Forestpixie, I don't know what you mean when you ask, "As far as the size of the /boot partition why did you do one in the first place?"  Are you asking why did I create a boot partition?  I simply followed a step by step guide for installing 7.2

---

### Post by forestpixie on 2008-05-01
Have you tried to rigt click and add a panel? I assume that will get it back into current sessions. AFAIK if the laternate cd says there are no upgrades to do then that's it.

---

### Post by meindian523 on 2008-05-01
+1 for that.Right click on your remaining panel and select new panel.You will have to add all the window lister,workspace switcher and other customized stuff you put in there though.To bring up a terminal,press Alt+F2 and type ```
gnome-terminal
```That's a terminal for you.

---

### Post by Arch Parsons on 2008-05-01
Actually, once I got into usr/bin and opened gnome-panel everything went back the way it was. I tried various Ctrl and Alt key combinations until I accessed the files.  From there it wsa just a matter of entering usr/bin/gnome-panel in the "address" bar.   I will start a new thread if I see any evidence that the installation is not a good one.  I did submit a bug report on the "insufficient space" error message, and the conclusion was that this was an erroneous message. Thanks again to everyone.

---

### Post by Arch Parsons on 2008-05-01
I don't see "mark solved" in thread tools??

---

### Post by forestpixie on 2008-05-01
That's gone due to return - don't know the expected arrival date though.

Glad you're sorted though :)

You could mark it the old way - edit first post and add [SOLVED] to title

---

### Post by nowshining on 2008-05-01
yah in thread tools there is NO solved, I confirm it on my end to. :)

---

