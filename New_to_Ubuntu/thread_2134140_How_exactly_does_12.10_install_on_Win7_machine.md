---
title: "How exactly does 12.10 install on Win7 machine?"
date: 2013-04-10
forum: New to Ubuntu
---

### Post by bruce73 on 2013-04-10
I installed 12.10/64 on my Win7/64 machine by downloading the setup file  from the website. It went flawlessly (installing my wireless printer  was a 3-hr challenge, but I got it sorted). I have a dual - boot option  screen, but I'm wondering how exactly does it get installed and run. Is  it on its own partition or does it run from a ram disk or a virtual  machine of some type?  I also downloaded the IMG file. Should I have used that to install?  I definitely wan to keep Ubuntu on my machine.


Also, I can see my external USB  drives, but none of my internal hard drives (I have 3, one of which is  partitioned with my Win7 installation, the remainder a separate  partition for video files). Is there any way to access these  drives, as I  have a ton of video on them?

---

### Post by Impavidus on 2013-04-10
With a setup file it sounds like wubi. Help page on wubi: [https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

There are two ways to install Ubuntu on a system with windows 7 too: wubi and true dual boot. The wubi installation uses a virtual partition, that is nothing more than a file in an ntfs partition used by windows. Therefore wubi depends on the windows file system. A true dual boot has a real partition of its own. Wubi is meant to try Ubuntu for a longer period. The advantages of wubi are that you don't have to partition your drive and that you can easely uninstall it. On the downside, it depends on the windows file system, sacrificing some reliability, and is limited in the available disk space. It is not a virtual machine or using a ram disk.

If you are sure you want to keep Ubuntu, I recommend you use a true dual boot. You can migrate wubi to a partition of its own ([https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)), but if you haven't done much yet it's better to do a fresh install. You'll need the .iso image, burnt to a disk or usb drive. Read [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) and [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing).

(Note: be careful when reading tutorials from the web. help.ubuntu.com are the official help pages, other sites recommended from these fora are reliable too, some others are not.)

---

### Post by Sandertje on 2013-04-10
hmmm... my initial answer was wrong! sorry! impavidus has the better answer!

---

### Post by bruce73 on 2013-04-10
@Impavidus: Thank you for the info and advice.  Yes, it was a wubi install (I can see Ubuntu in Windows Add/Remove). It was just that I was surprised to see a dual boot menu when I restarted, so I wasn't sure if it had created it's own permanent partition or not.  I only just installed 12.10 yesterday and I've already downloaded the ISO (700+ MB) file, so I will do a fresh install. I have plenty of room on my main hard drive (125 GB+ free). I'll read the info from the links you posted and get back if I have any follow-up questions. :)

Oh, one more question: I have Win7/64. I installed 12.10/64 yesterday. I'm figuring that's the way to go with a permanent installation, right? The trouble I had installing my printer yesterday was the only linux drivers I could find on Brother's site were 32-bit. I finally found a command that I could use which, I believe, installed some libraries so that I could use those 32-bit drivers (I may be wrong about that, all of this is still pretty much Greek to me...).  Are 64-bit linux drivers hard to find from 3rd party vendors?  Would a 32-bit installation be better in the long run?

I lied, I have one final question: how large a partition is recommended? 50GB? 75GB? I don't anticipate a large amount of user files, but I don't want to have to re-partition down the line.

---

### Post by Zill on 2013-04-10
> **bruce73 said:**
> ...The trouble I had installing my printer yesterday was the only linux drivers I could find on Brother's site were 32-bit. I finally found a command that I could use which, I believe, installed some libraries so that I could use those 32-bit drivers (I may be wrong about that, all of this is still pretty much Greek to me...).  Are 64-bit linux drivers hard to find from 3rd party vendors?  Would a 32-bit installation be better in the long run?...
If you are new to Linux my best advice is to note that "Linux is not Windows" and that *many* things are done differently here. ;-)  While you *may* occasionally need to search the Web for a specific driver, this is not usually necessary as very many drivers come with your Ubuntu installation as standard.  Any additional ones are often downloaded and installed automatically without much user interaction other than approving this action!  For instance, when I connected my Brother HL-2130 printer to the USB port, Ubuntu automatically suggested the right driver and then went and installed it.  This is a totally different approach to that used by Microsoft Windows but is, IMHO, far better - it just takes some getting used to. ;-)

I strongly suggest that you install your new system with the computer connected to your router via an ethernet cable.  If the router has been correctly configured this should mean that you have full internet access from the outset.  This will be invaluable in the initial configuration of your system, including the various graphic, wireless and printer driver downloads that Ubuntu will try to find.

Once you have your system up and running, if Ubuntu does not automatically configure the correct printer driver, just post back the exact model here and someone should be able to help.

Regarding 32 vs 64 bit, my view is that *if* your PC has less than 4GB of RAM (as mine have!) then 32-bit "just works" without any hassle.  If you do have more than 4GB of RAM then 64-bit is probably the best version - but this may generate a few more problems to solve!

---

### Post by bruce73 on 2013-04-10
@Zill: My machine is on a home network, so, yes, connected to a router.  I tried to simply install my Brother MFC-J430W (wireless), but there were no drivers applicable (except the generic, text-only one). That's why I ended up using the 32-bit drivers on Brother's site, but had to do so via terminal command line. Ubuntu could see the printer on the network, but I couldn't print. Anyway, long story short, I got it working. 

My bigger problem now is that I've done a permanent install of 12.10, but I can't get the system to boot into it (no dual boot menu).  I suspect this has something to do with the way Win 7 was installed (that 100MB partition before the C: drive).  I need to hunt in the forum for a solution (this must be a common problem).  If you can point me to a specific topic, please do. :)

---

### Post by oldfred on 2013-04-10
With multiple drives & multiple installs it is worthwhile to run this to see exactly what is where. You can add the ppa to your installer and run it from the live mode.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by bcbc on 2013-04-10
It has nothing to do with Windows 7 and everything to do with where you installed the Grub bootloader. You most likely picked a partition instead of the drive (/dev/sda).
To fix it boot from a live CD, mount your new Ubuntu partition, and install grub. Normally your ubuntu partition is /dev/sda5, but if not change this:

```
sudo mount /dev/sda5 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```

If you're not sure, then either pass back the result of (note it's lower case -L)
```
sudo fdisk -l
``` 

or run a canned repair tool like boot-repair.

---

### Post by bruce73 on 2013-04-10
Thanks. I started a separate thread in the Installation forum thinking it might be more appropriate and visible there, but you guys are quick! So I've already run the tool and posted the url over there.  I appreciate the info, though. I did run fdisk, and it shows sda6 (Linux) & sda7 (Linux swap).

---

