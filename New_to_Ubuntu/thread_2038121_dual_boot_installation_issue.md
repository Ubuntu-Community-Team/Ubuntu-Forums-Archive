---
title: "dual boot installation issue"
date: 2012-08-05
forum: New to Ubuntu
---

### Post by salehko on 2012-08-05
Hello,
Just recently bought a new Dell Inspiron 14z on which I'm trying to install Ubuntu in order to dual boot alongside Windows 7.

When booting from the Ubuntu 12.04 LTS live cd and navigating through the first couple of frames I get to the "Installation types" screen which is blank, with no devices listed:

[http://img109.imageshack.us/img109/7430/installationtype.png](http://img109.imageshack.us/img109/7430/installationtype.png)

None of the buttons are click-able other than "Quit", "Back" and "Install Now". Clicking "Install Now" fails with the message "No root file system is defined. Please correct this from the partitioning menu". Currently the partitions look like:

[http://img9.imageshack.us/img9/9095/fdisk.png](http://img9.imageshack.us/img9/9095/fdisk.png)

Some googling suggested that it may have to do with the RAID configuration which is currently,

[http://img254.imageshack.us/img254/1964/dmraid.png](http://img254.imageshack.us/img254/1964/dmraid.png)

I'd like to do a simple install of Ubuntu, even if that means just shrinking /dev/sda3 to make enough space. But shrinking /dev/sda3 manually results in the same thing, an Installation Type screen with no devices, and then failure. The closest 'solution' I've found is:

[http://abbotm.wordpress.com/2011/10/25/installing-dual-boot-win7-ubuntu-on-a-ssd-system-with-raid-for-data-drives/](http://abbotm.wordpress.com/2011/10/25/installing-dual-boot-win7-ubuntu-on-a-ssd-system-with-raid-for-data-drives/)

I'm hoping that someone will be able to offer a simpler solution. Thanks!

---

### Post by oldfred on 2012-08-05
RAID is normally part of a server and Ubuntu offers RAID support with the server install or the alternative installer. You can use the liveCD and add the RAID drivers, but they still are not part of the liveCD. Do not use gparted on RAID as it does not work as you have found out.

These users uninstalled the RAID and made the SSD a separate drive.
 Intel Smart Response Technology & Dell XPS
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)

If you do not want to remove the RAID try the alternative installer. It is not a liveCD.

[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)

If you are using liveCD to review drives add this:
# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.

sudo apt-get install mdadm

---

### Post by salehko on 2012-08-06
excellent, 

[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155) 

worked perfectly, computer is now dual-booting correctly, etc. Thanks for your help.

---

### Post by jsundqui on 2012-09-27
I have a new 14z also and want to dual boot with ubuntu

You say you followed the instructions at [http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155) and now it works perfectly.

However, following those instructions, it looks like the Intel RST is disabled.  However, that is a great feature when booting into windows.  Is it true that the only way to dual boot with machines with Intel RST is to actually disable it? 

That would be a shame.

Does the Intel RST RAID (fake RAID?) configuration have to incorporate the whole sda?  It's been a while since I set up RAID1 on my server so I don't recall if RAID could be set up between just certain partitions.  I think in Linux software RAID it can, but perhaps not with Intel RST.

---

### Post by asymptoticFault on 2012-09-28
I just completed a dual boot setup on my *Inspiron 17R SE* which also has the *IRST* (1TB HDD + 32GB SSD).  I followed the instructions on the post you mentioned however I did not follow them exactly.  The real key seems to be removing the raid metadata with the [FONT=Courier New]dmraid[/FONT] command ([FONT=Courier New]sudo dmraid -E -r /dev/sda[/FONT]) and I only ran it against [FONT=Courier New]sda[/FONT] and not [FONT=Courier New]sdb[/FONT] as well.  In fact running the [FONT=Courier New]dmraid[/FONT] command was the only step I took and sure enough the installer was able to detect all drives and partitions perfectly.

Now, as to your question about whether or not dual boot will work with *IRST* enabled, in my experience, yes it will!  After reading this thread and others I was asking myself the same question.  Everyone seemed to have solutions for disabling it and getting *Ubuntu* installed but what if you still want *IRST* enabled because it is a nice feature and you paid for it so why not use it.  Since I didn't seem to find any answers as to whether it would still work I just took the plunge to see what would happen.  Turns out re-enabling the *IRST* is very simple and quick once you've booted back into windows.  Below are the steps to re-enable it with screenshots to help.

To start I will assume you have run the [FONT=Courier New]dmraid[/FONT] command and have successfully installed *Ubuntu*.
[LIST=1]
[*]Restart the machine.  You will see a post screen for the *Intel Rapid Storage Technology Configuration Utility* that does not normally appear.  It is appearing because it has detected that there is something wrong with the RAID setup as can be seen on the screen under *Status* for the *Cache Drive* and it says it's *'Disabled'*.  Don't worry about this, it is normal because we have removed the raid metadata and we don't have to do anything about it here so just allow it to continue and load up *Grub*.
[*]Select your windows entry from *Grub*.  Hopefully you have one, I didn't because it turns out *IRST* also interferes with *Grub2* doing it's job to detect other OS's.  Turns out the easiest way to resolve this is to just boot back into *Ubuntu*, run the same [FONT=Courier New]dmraid[/FONT] command again and then run [FONT=Courier New]sudo update-grub[/FONT].  With the raid metadata removed again the [FONT=Courier New]os-prober[/FONT] should be able to detect windows and you should see it from the output of the [FONT=Courier New]update-grub[/FONT] command.  Restart again and select windows.
[*]Once windows is started, launch the *Intel Rapid Storage Technology* program from the start menu, by either typing it into the search or selecting *All Programs > Intel > Intel Rapid Storage Technology*.
[*]Once the program is launched, select the *'Accelerate'* tab/button at the top and you should see something similar to this.


[IMG]https://lh5.googleusercontent.com/-r5P1uKqp0CA/UGVYiJG76II/AAAAAAAABlA/b5P8CP0lfAw/s800/screen1.png[/IMG]
[*]Click *'Disassociate'*.  You will be presented with this dialog.


[IMG]https://lh4.googleusercontent.com/-hhdJl4N8xJk/UGVYiMHSVVI/AAAAAAAABk4/m_lyhDfRX78/s800/screen2.png[/IMG]
[*]Click *'Yes'*.  The association has been removed and acceleration disabled.


[IMG]https://lh3.googleusercontent.com/-LMe17XRFHpM/UGVYiAbxNyI/AAAAAAAABk8/qD_kolShGKc/s800/screen3.png[/IMG]
[*]Click *'Select device'*.  You will be presented with this dialog.


[IMG]https://lh3.googleusercontent.com/-9XnuR8mu7hg/UGVYiqVDxfI/AAAAAAAABlE/Dm59W0hFPrs/s800/screen4.png[/IMG]
[*]Select the drive you want to accelerate from the drop down, in my case there was only one.  Select *'Enhanced mode'*, this was the default on my machine.  Click *'Ok'*.  The association should be restored and acceleration re-enabled.


[IMG]https://lh3.googleusercontent.com/-Ynt_aBjcUUs/UGVYi18--zI/AAAAAAAABlM/uZ05ichx5PM/s800/screen5.png[/IMG]
[/LIST]


That's it.  I'm not sure if a restart is required for the caching/acceleration to really take affect but that's it for the configuration.  So it boiled down to really just two things to get the dual boot working on my machine:

[LIST=1]
[*]Use the [FONT=Courier New]dmraid[/FONT] command in *Ubuntu* anytime you need to scan for drives and partitions; such as for [FONT=Courier New]update-grub[/FONT] or when installing *Ubuntu*.
[*]Use the *IRST* program in windows to recreate the association and re-enable acceleration.
[/LIST]


Hope this was helpful.  It worked on my machine and since you have the same setup from *Dell* I'm guessing it will for you too.  It certainly took me several hours of frustration to figure out but then I am very new to Linux and dual booting.

---

### Post by jsundqui on 2012-10-02
> **asymptoticFault said:**
> Hope this was helpful.  It worked on my machine and since you have the same setup from *Dell* I'm guessing it will for you too.  It certainly took me several hours of frustration to figure out but then I am very new to Linux and dual booting.
Saying this is helpful is an understatement!  Thanks for the incredibly detailed description.  I will have try to find a time when I have a stretch of free time available to try it out.  Even though I am not new to Linux and dual booting (started with Slackware downloaded to floppies in 1996!), a lot of this seems to require intense concentration to not screw things up.

---

### Post by asymptoticFault on 2012-10-04
You are very welcome!  Let me know if this works for you.  I did my best to be thorough since I had just been through this same issue and wanted to get all the steps documented.  Good luck!

---

### Post by Baladya on 2012-10-14
> **asymptoticFault said:**
> You are very welcome!  Let me know if this works for you.  I did my best to be thorough since I had just been through this same issue and wanted to get all the steps documented.  Good luck!

Hey man looks like each one used a diff way to get Ubuntu installed. Can you just quickly write up the steps to get it installed in the first place (before enabling the IRST)

---

### Post by asymptoticFault on 2012-10-16
The installation process is well documented here, [_Ubuntu Installation Guide_]("https://help.ubuntu.com/12.04/installation-guide/i386/index.html").

However, I can provide an overview of the steps I took which follow those for creating a dual-boot system installed on a single hard drive.  Everything is standard here with the caveat of the *IRST*.  You will need to use the [FONT="Courier New"]dmraid[/FONT] command prior to running the *Ubuntu Installer* so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

With that in mind, here are the steps:

[LIST=1]
[*]Re-partition your drive to make room for *Ubuntu*.  There are several ways to do this.  I used the *Windows Disk Management* tool to shrink the main *Windows* partition.  The process is documented here, [_Easily Shrink a Volume on a Windows 7 Disk_]("http://technet.microsoft.com/en-us/magazine/gg309169.aspx").


[*]Boot into the *Ubuntu Live CD*.  I believe it will ask you if you want to install or try *Ubuntu*, click "Try Ubuntu".


[*]Open a terminal.


[*]Run the command [FONT="Courier New"]sudo dmraid -E -r /dev/sda[/FONT]


[*]Run the desktop installer; I believe there is an icon on the desktop to launch it.  There is a basic overview of the desktop installer here, [_Installing Ubuntu Desktop_]("http://www.ubuntu.com/download/help/install-ubuntu-desktop").


[*]When you come to the step for partitioning you'll select the "Something else" option.  I forgot what the screens look like after this but basically you want to select the unallocated partition that resulted from shrinking the *Windows* partition and create the *Ubuntu* partitions in it.  I only chose to create the [FONT="Courier New"]root (/)[/FONT] and [FONT="Courier New"]swap[/FONT] partitions and didn't bother with creating separate partitions for [FONT="Courier New"]/home[/FONT], [FONT="Courier New"]/usr[/FONT], [FONT="Courier New"]/var[/FONT] & [FONT="Courier New"]/tmp[/FONT].  Again I don't remember exactly what the screens say but I remember the installer making it very straight forward.


[*]Once you're finished creating and selecting the partitions just follow the rest of the steps and you're done.


[*]Refer to my previous post for re-enabling the *IRST*.
[/LIST]

---

### Post by Baladya on 2012-10-18
> **asymptoticFault said:**
> The installation process is well documented here, [_Ubuntu Installation Guide_]("https://help.ubuntu.com/12.04/installation-guide/i386/index.html").

However, I can provide an overview of the steps I took which follow those for creating a dual-boot system installed on a single hard drive.  Everything is standard here with the caveat of the *IRST*.  You will need to use the [FONT=Courier New]dmraid[/FONT] command prior to running the *Ubuntu Installer* so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

With that in mind, here are the steps:

[LIST=1]
[*]Re-partition your drive to make room for *Ubuntu*.  There are several ways to do this.  I used the *Windows Disk Management* tool to shrink the main *Windows* partition.  The process is documented here, [_Easily Shrink a Volume on a Windows 7 Disk_]("http://technet.microsoft.com/en-us/magazine/gg309169.aspx").
[*]Boot into the *Ubuntu Live CD*.  I believe it will ask you if you want to install or try *Ubuntu*, click "Try Ubuntu".
[*]Open a terminal.
[*]Run the command [FONT=Courier New]sudo dmraid -E -r /dev/sda[/FONT]
[*]Run the desktop installer; I believe there is an icon on the desktop to launch it.  There is a basic overview of the desktop installer here, [_Installing Ubuntu Desktop_]("http://www.ubuntu.com/download/help/install-ubuntu-desktop").
[*]When you come to the step for partitioning you'll select the "Something else" option.  I forgot what the screens look like after this but basically you want to select the unallocated partition that resulted from shrinking the *Windows* partition and create the *Ubuntu* partitions in it.  I only chose to create the [FONT=Courier New]root (/)[/FONT] and [FONT=Courier New]swap[/FONT] partitions and didn't bother with creating separate partitions for [FONT=Courier New]/home[/FONT], [FONT=Courier New]/usr[/FONT], [FONT=Courier New]/var[/FONT] & [FONT=Courier New]/tmp[/FONT].  Again I don't remember exactly what the screens say but I remember the installer making it very straight forward.
[*]Once you're finished creating and selecting the partitions just follow the rest of the steps and you're done.
[*]Refer to my previous post for re-enabling the *IRST*.
[/LIST]



Actually I meant the steps of turning of Acceleration and changing the RAID in the BIOS and whether u did that or not :P Anyways You installed Linux on ur HDD or SSD?

---

### Post by asymptoticFault on 2012-10-18
I did not take any steps to directly turn off acceleration nor did I do anything in the BIOS.  The steps I just described combined with my post on re-enabling acceleration is literally everything I did to get the dual boot working with *IRST* enabled for *Windows*.

---

### Post by Baladya on 2012-10-20
> **asymptoticFault said:**
> I did not take any steps to directly turn off acceleration nor did I do anything in the BIOS.  The steps I just described combined with my post on re-enabling acceleration is literally everything I did to get the dual boot working with *IRST* enabled for *Windows*.

Ok cool :). Did you install Linux on the HDD or the SSD?

---

### Post by asymptoticFault on 2012-10-20
The main *Windows* partition is on the HDD (sda), so that's the partition I re-sized and where I installed *Ubuntu*.

---

### Post by Baladya on 2012-10-22
> **asymptoticFault said:**
> The main *Windows* partition is on the HDD (sda), so that's the partition I re-sized and where I installed *Ubuntu*.

Aha... What if I wanna install it on the SSD? I was thinking of trying to install it on the SSD and at the same time enabling IRST for Windows but read that you should atleast devote 18 GB for the IRST. Could I just re-partition the 8 GB and the 22 GB and make them 19 GB (IRST) and 11 for "/" (and the swap and /home on the HDD) or will I ruin the RAID configuration and not be able to switch IRST on again?

Really appreciate ur help man :)

---

### Post by asymptoticFault on 2012-10-22
Theoretically it should be possible to install the root partition on the SSD, however I have no experience with this or dividing Linuxs' partitions among multiple hard drives.  Also I'm not sure if you would even need to re-partition the SSD since on my install I think 22GB of it were unallocated.  I do not know the details of how IRST works but if it's setup to expand its partition as needed could cause problems if there is another partition in the unallocated space.  I would look more into IRST and how it is using the SSD before proceeding because it seems to me that SSD might be quite volatile since it is intended to be for cache.

---

### Post by Baladya on 2012-10-22
> **asymptoticFault said:**
> Theoretically it should be possible to install the root partition on the SSD, however I have no experience with this or dividing Linuxs' partitions among multiple hard drives.  Also I'm not sure if you would even need to re-partition the SSD since on my install I think 22GB of it were unallocated.  I do not know the details of how IRST works but if it's setup to expand its partition as needed could cause problems if there is another partition in the unallocated space.  I would look more into IRST and how it is using the SSD before proceeding because it seems to me that SSD might be quite volatile since it is intended to be for cache.

Alright thanks a lot man :)

---

### Post by The Thunder Chimp on 2013-01-29
> **asymptoticFault said:**
> I just completed a dool boot setup on my *Inspiron 17R SE* which also has the *IRST* (1TB HDD + 32GB SSD).  I followed the instructions on the post you mentioned however I did not follow them exactly.  The real key seems to be removing the raid metadata with the [FONT=Courier New]dmraid[/FONT] command ([FONT=Courier New]sudo dmraid -E -r /dev/sda[/FONT]) and I only ran it against [FONT=Courier New]sda[/FONT] and not [FONT=Courier New]sdb[/FONT] as well.  In fact running the [FONT=Courier New]dmraid[/FONT] command was the only step I took and sure enough the installer was able to detect all drives and partitions perfectly.

Now, as to your question about whether or not dual boot will work with *IRST* enabled, in my experience, yes it will!  After reading this thread and others I was asking myself the same question.  Everyone seemed to have solutions for disabling it and getting *Ubuntu* installed but what if you still want *IRST* enabled because it is a nice feature and you paid for it so why not use it.  Since I didn't seem to find any answers as to whether it would still work I just took the plunge to see what would happen.  Turns out re-enabling the *IRST* is very simple and quick once you've booted back into windows.  Below are the steps to re-enable it with screenshots to help.

To start I will assume you have run the [FONT=Courier New]dmraid[/FONT] command and have successfully installed *Ubuntu*.
[LIST=1]
[*]Restart the machine.  You will see a post screen for the *Intel Rapid Storage Technology Configuration Utility* that does not normally appear.  It is appearing because it has detected that there is something wrong with the RAID setup as can be seen on the screen under *Status* for the *Cache Drive* and it says it's *'Disabled'*.  Don't worry about this, it is normal because we have removed the raid metadata and we don't have to do anything about it here so just allow it to continue and load up *Grub*.
[*]Select your windows entry from *Grub*.  Hopefully you have one, I didn't because it turns out *IRST* also interferes with *Grub2* doing it's job to detect other OS's.  Turns out the easiest way to resolve this is to just boot back into *Ubuntu*, run the same [FONT=Courier New]dmraid[/FONT] command again and then run [FONT=Courier New]sudo update-grub[/FONT].  With the raid metadata removed again the [FONT=Courier New]os-prober[/FONT] should be able to detect windows and you should see it from the output of the [FONT=Courier New]update-grub[/FONT] command.  Restart again and select windows.
[*]Once windows is started, launch the *Intel Rapid Storage Technology* program from the start menu, by either typing it into the search or selecting *All Programs > Intel > Intel Rapid Storage Technology*.
[*]Once the program is launched, select the *'Accelerate'* tab/button at the top and you should see something similar to this.

(here be an image)
[*]Click *'Disassociate'*.  You will be presented with this dialog.

(here too)
[*]Click *'Yes'*.  The association has been removed and acceleration disabled.

(encore)
[*]Click *'Select device'*.  You will be presented with this dialog.

(bis)
[*]Select the drive you want to accelerate from the drop down, in my case there was only one.  Select *'Enhanced mode'*, this was the default on my machine.  Click *'Ok'*.  The association should be restored and acceleration re-enabled.
(ter)
[/LIST]
 That's it.  I'm not sure if a restart is required for the caching/acceleration to really take affect but that's it for the configuration.  So it boiled down to really just two things to get the dual boot working on my machine:

[LIST=1]
[*]Use the [FONT=Courier New]dmraid[/FONT] command in *Ubuntu* anytime you need to scan for drives and partitions; such as for [FONT=Courier New]update-grub[/FONT] or when installing *Ubuntu*.
[*]Use the *IRST* program in windows to recreate the association and re-enable acceleration.
[/LIST]


Hope this was helpful.  It worked on my machine and since you have the same setup from *Dell* I'm guessing it will for you too.  It certainly took me several hours of frustration to figure out but then I am very new to Linux and dual booting.

Wow, thanks! 
I think we really need a print post feature.

---

### Post by anujtripathi on 2013-02-09
I had done a dual boot on my inspiron 14z following the steps above. Everything went fine for 3 months. Recently, my laptop started to restart after the dell logo and didn't even reach the dual boot screen.
When I called the dell support they asked me to change setting from ISRT to AHCI and I was able to reach the dual boot screen, from where I am able to boot into Linux. But now when I try to boot windows, I see Windows logo followed by a blue screen and a reboot.

Changing the settings back to ISRT takes me back to the loop of dell logo followed by blank screen and then back to dell logo.

Has anyone faced this issue ? This problem started happening suddenly. I am not sure what went wrong here. Any help will be Golden.

TIA

---

### Post by zoum26 on 2013-02-10
I have a dell inspiron 14z too and your issue worry me....

Did you try to reinstall linux using the dmraid command again? Or just delete linux with the linux live CD to see if windows still works?

---

### Post by cornleader on 2013-03-11
I did pretty much the same thing but completely messed up my iRST. I have the same machine, 7720 SE. So caching, rapid start and dual boot is working via Grub?

---

### Post by cornleader on 2013-03-14
Anyone using iRST on a dual boot setup?

This post states the rapid storage is working but I want to know if rapid storage AND rapid start are working. I want both!! :D lol

---

### Post by pheni004 on 2013-06-13
I followed what asymptoticFault described, but I am unable to run "sudo update-grub".

I installed Scientific Linux 6.4 on my partition and I have been using a live version of Ubuntu to follow his steps. When I use the command "sudo update-grub", Ubuntu says it cannot find the canonical path of /cow

Is there any helping me since I have SL6.4 instead of Ubuntu on the partition? Or should I look elsewhere for help?

Thanks!

---

### Post by oldfred on 2013-06-13
You cannot run sudo update-grub from a liveCD, but only from inside your install. That may be why it is giving error messages.

---

### Post by asymptoticFault on 2013-07-31
Wow, didn't know I was missing all the posts on this thread, could've sworn I had email notifications for it.  Sorry for the extremely delayed response for anyone that was waiting on an answer from me.  I had been neglecting my *Ubuntu* install for several months :(  My main push to get it installed originally was to root and unlock my *GSIII*, since many of the tools to do so are written for* Linux*.  After I finished that little project I didn't have as much drive to tinker with *Ubuntu*, I know shame on me.  Recently I've began booting into it again though and am going to try to make a stronger effort to really learn *Linux*.

Anyway, as I eluded to previously, I do still have a working dual boot configuration with *Windows 7* and *Ubuntu 12.04 LTS*.  The *IRST* is operational as well.  I believe the *Intel Rapid Start* is working as well because the machine does boot up quite quickly, though I will have to check my computer to be sure.

***anujtripathi***
That is certainly a strange issue you are having with the boot loop.  Interesting that you can get into *Linux *when you switch to *AHCI *and not *Windows*.  It might make sense that if *Windows *was installed/configured with the *IRST *that it wouldn't be able to boot without it.  Maybe try reinstating the *Windows* bootloader instead of *Grub*, or simply reinstall *Grub* with something like [Super Grub Disk]("http://www.supergrubdisk.org/super-grub-disk/").

***cornleader***
What exactly is wrong with the *IRST*?  Are you able to boot into *Windows *and access the *IRST *configuration?  Caching, rapid start and dual booting is all working fine via *Grub *as far as I am aware, although the caching and rapid start have nothing to do with *Grub *or *Linux*, *IRST *is exclusively *Windows *as far as I know.

Thank you ***oldfred ***for responding to ***pheni004***.

I will try to keep a better eye on this thread for any other questions regarding my dual boot configuration.  I am sorry for any issues anyone else has had attempting to create this configuration, but as these things go I can only vouch for my experience and make no guarantees for the process I used.  However, given the same hardware and initial configuration from *Dell *I would think others would be able to achieve this dual boot configuration as well.

---

### Post by riccardosl45 on 2014-02-19
> **asymptoticFault said:**
> The installation process is well documented here, [_Ubuntu Installation Guide_]("https://help.ubuntu.com/12.04/installation-guide/i386/index.html").

However, I can provide an overview of the steps I took which follow those for creating a dual-boot system installed on a single hard drive.  Everything is standard here with the caveat of the *IRST*.  You will need to use the [FONT=Courier New]dmraid[/FONT] command prior to running the *Ubuntu Installer* so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

With that in mind, here are the steps:

[LIST=1]
[*]Re-partition your drive to make room for *Ubuntu*.  There are several ways to do this.  I used the *Windows Disk Management* tool to shrink the main *Windows* partition.  The process is documented here, [_Easily Shrink a Volume on a Windows 7 Disk_]("http://technet.microsoft.com/en-us/magazine/gg309169.aspx"). 
[*]Boot into the *Ubuntu Live CD*.  I believe it will ask you if you want to install or try *Ubuntu*, click "Try Ubuntu". 
[*]Open a terminal. 
[*]Run the command [FONT=Courier New]sudo dmraid -E -r /dev/sda[/FONT] 
[*]Run the desktop installer; I believe there is an icon on the desktop to launch it.  There is a basic overview of the desktop installer here, [_Installing Ubuntu Desktop_]("http://www.ubuntu.com/download/help/install-ubuntu-desktop"). 
[*]When you come to the step for partitioning you'll select the "Something else" option.  I forgot what the screens look like after this but basically you want to select the unallocated partition that resulted from shrinking the *Windows* partition and create the *Ubuntu* partitions in it.  I only chose to create the [FONT=Courier New]root (/)[/FONT] and [FONT=Courier New]swap[/FONT] partitions and didn't bother with creating separate partitions for [FONT=Courier New]/home[/FONT], [FONT=Courier New]/usr[/FONT], [FONT=Courier New]/var[/FONT] & [FONT=Courier New]/tmp[/FONT].  Again I don't remember exactly what the screens say but I remember the installer making it very straight forward. 
[*]Once you're finished creating and selecting the partitions just follow the rest of the steps and you're done. 
[*]Refer to my previous post for re-enabling the *IRST*. 
[/LIST]


hi, what command is needed to install metaadata?

[FONT=Courier New]sudo dmraid -E -r /dev/sda 

[FONT=arial]is to remove but opposite?[/FONT][/FONT][FONT=arial] [/FONT]

---

### Post by oldfred on 2014-02-19
@riccardosl45
Please do not keep posting the same question in multiple threads. You already have your own thread. If you do not get an answer after 24 hours, you can bump it again to be at top of list.
Most users do not look at solved threads as they are solved.

[http://ubuntuforums.org/showthread.php?t=2206488](http://ubuntuforums.org/showthread.php?t=2206488)

---

