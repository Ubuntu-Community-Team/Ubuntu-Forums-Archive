---
title: "(SOLVED) Missing thread? How To Disable OS_PROBER In Grub?"
date: 2013-03-06
forum: New to Ubuntu
---

### Post by ken0069 on 2013-03-06
Back a couple of years ago I posted a thread in here titled "It's Grub Again" and the discussion was how to stop Grub from installing on my Windows drives on a multi-boot system.  Another member here showed me how to disable OS-PROBER and that took care of my problem and over the last couple of years I've used that thread to modify all 3 of my systems to get rid of Grub controlling boot selection.  

So here I am installing a clean copy of 12.04 on what use to be a Mint 12 box and now I can't find that post??

So can someone tell me again how to stop Grub's OS-PROBER from looking for Windows drives to mess up?

Thanks,

Ken

---

### Post by ajgreeny on 2013-03-06
I'm not sure I completely understand what you are trying to do but I presume you are using the windows bootloader system to boot into Ubuntu, and not grub; or that is what you want to happen. If not, how do you manage to boot to ubuntu when grub is not controlling the boot selection?

If I am correct, I think you should be able to put grub on the ubuntu partition instead of the MBR of the first disk, where it is installed by default, by choosing Something Else at disk preparation stage of the installation.

Also to stop grub searching for and finding other OSs, you can remove the execute flag from the executable file with command ```
sudo chmod -x /usr/bin/os-prober
```

---

### Post by ken0069 on 2013-03-06
Thanks for your reply.  

I've had problems in the past when Grub got installed on my Windows drives and I do not want that to happen again, ie, Windows wouldn't boot without the Linux drive being connected to the system.  Since I don't want Windows to be dependent on Linux I disable the os-prober after the initial install of Ubuntu without the Windows drive connected.  That way NOTHING from Ubuntu/grub gets installed on that Windows drive.  

So Grub does get installed and only sees Ubuntu so there's no grub menu that comes up at boot up.  I change boot drives in BIOS and boot to whichever drive I want.

So I'll try your code to see if that will stop Grub from trying to install on the Windows drive.  

Thanks,

Ken

---

### Post by ken0069 on 2013-03-06
BAD NEWS!  Didn't work and I lost that Windows load and all the data on that drive yet again??  :confused::frown:  I'm done for the night.  Will regroup and post more details in the morning!  Grub has been the curse of my life where Windows is concerned!!

---

### Post by lisati on 2013-03-06
> **ken0069 said:**
> Back a couple of years ago I posted a thread in here titled "It's Grub Again" and the discussion was how to stop Grub from installing on my Windows drives on a multi-boot system.  Another member here showed me how to disable OS-PROBER and that took care of my problem and over the last couple of years I've used that thread to modify all 3 of my systems to get rid of Grub controlling boot selection.  

So here I am installing a clean copy of 12.04 on what use to be a Mint 12 box and now I can't find that post??

So can someone tell me again how to stop Grub's OS-PROBER from looking for Windows drives to mess up?

Thanks,

Ken
Here's your thread: [http://ubuntuforums.org/showthread.php?t=1850660](http://ubuntuforums.org/showthread.php?t=1850660)

---

### Post by Xgen on 2013-03-07
By removing execute permissions from individual files in the /etc/grub.d/ folder disables them. As I use only a custom grub2 and theme, I always remove the permissions from 30_os-prober (and memtest just because...) through root nautilus OR 'sudo chmod -x /etc/grub.d/30_os-prober'.

---

### Post by mikewhatever on 2013-03-07
> **ken0069 said:**
> Thanks for your reply.  

I've had problems in the past when Grub got installed on my Windows drives and I do not want that to happen again, ie, Windows wouldn't boot without the Linux drive being connected to the system.  Since I don't want Windows to be dependent on Linux I disable the os-prober after the initial install of Ubuntu without the Windows drive connected.  That way NOTHING from Ubuntu/grub gets installed on that Windows drive.  

So Grub does get installed and only sees Ubuntu so there's no grub menu that comes up at boot up.  I change boot drives in BIOS and boot to whichever drive I want.

So I'll try your code to see if that will stop Grub from trying to install on the Windows drive.  

Thanks,

Ken

Disabling the OS probber wouldn't affect where Grub is installed in any way. Either change the default location (/dev/sda) to something else, or disconnect the hdd with Windows when installing Ubuntu.

---

### Post by oldfred on 2013-03-07
+ on mikewhatevers comments

If you just do a a default install of Ubuntu it installs grub to sda which usually is the Windows drive. With multiple hard drives you need to use Something else or manual install. Then you get the option on where to install grub2's boot loader.
       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

Grub also remembers where to re-install on major updates. You can check if that is your sda drive or sdb drive, but it will be drive model not sda or sdb.
      
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by ken0069 on 2013-03-07
> **mikewhatever said:**
> Disabling the OS probber wouldn't affect where Grub is installed in any way. Either change the default location (/dev/sda) to something else, or disconnect the hdd with Windows when installing Ubuntu.

Yup, I always disconnect other drives when installing Ubuntu or anything else for that matter.  Ask me how I learned that one!

OK so after working on that Windows XP drive most of the afternoon yesterday and part of today I finally got the partition tables rebuilt and it's booted up now and seems to be working fine!  It's been exciting times around here for the last 24 hours and this is my FIRST successful partition table repair ever on a Windows load!!  I mean even Ubuntu couldn't read that drive!!

And I think I figured out what happened as I did NOT run the update grub command after I did the initial chmod command in terminal.  I just rebooted with the Windows drive connected and it was all down hill from there!

Hopefully it will be ok now but I'll wait until tomorrow before I mark this one solved.

Thanks for the help ppl,

Ken

---

### Post by ajgreeny on 2013-03-08
Just to make things easier for you next time (I hope), note that you do not need to remove or disconnect the windows drive when you install Ubuntu; it is very much easier if you simply choose the **"Something Else"** option at disk preparation stage (formatting of partitions etc etc).  At the bottom of that page the installer asks you where you want the bootloader files (grub) to be installed.  Just make sure you choose the same disk that you have installed Ubuntu to (/dev/sdb usually if you have two disks, note not a partition such as /dev/sdb1), and you can then simply choose to boot from the second hard disk from your BIOS setup.

If you do that, the windows bootloader will remain untouched on sda, but windows only, of course, will boot from the windows bootloader if you use sda as the first boot-device.  Grub will be on sdb, and there will then be no need to disable os_prober, as you will then be able to boot either OS from grub, if sdb is your first boot-device.

---

### Post by ken0069 on 2013-03-08
Probably be a while before I do another clean install on any of my boxes as I just replaced Mint 12 with Ubuntu 12.04 to get the long term support.  Now all three multi-boot systems are running 12.04.  

I don't normally swap around much once I get things like I want them.  Only reason I went to Mint to begin with was because I hate "Unity" but now that Mate is out and works reasonably well I came back to Ubuntu.  

Here's an FYI for ya.  One of my 3 boxes has 6 hard drives in it and all of them are bootable.  Ubuntu, Vista, Win 7, Win XP, Win XP x64 and a 1TB storage drive with a small bootable Windows XP partition.  I use BIOS to select the boot drive.  The other two don't have but 2 bootable drives in them.   Main reason for the 6 drives is because I do some computer repair for some old folks in my neighborhood so I like to have an operating system on my computer that matches what I work on.  

Ennywho, thanks again all for the help

Ken

---

