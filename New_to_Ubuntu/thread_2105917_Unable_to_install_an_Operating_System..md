---
title: "Unable to install an Operating System."
date: 2013-01-17
forum: New to Ubuntu
---

### Post by anup1234 on 2013-01-17
Hi so here is the situation.
  I had installed 2 OS’s on my machine i.e. Windows XP and Fedora,I wanted to uninstall fedora and at that time dint know how to uninstall it (nor do now) so I formatted that drive( using mouse )which had fedora installed in it through windows XP. 
  During start up it GRUB appears on my machine giving me the OS choice 1)fedora 2)XP
  **How do uninstall GRUB ? **
  Also after this I tried to re-install windows XP but it dint install instead (after the message “Hardware is inspecting your Hardware….” It did nothing ,just screen gone blank) at first I thought it must be an CD issues but after trying with number of Windows XP bootable CD’s it dint work.
  Also I tried to create new partition using GParted Live CD but it also failed (showed buffered I/O error etc)
  System details incase if needed:
  RAM 1gb,160gb SATA hdd,core2duo,mercury MB
  **_My guess_**
  something is wrong with my Hard disk (especially MBR or any sector corrupted )
  **_what I want to know_**
  **what and where is the exact problem? **
  **How to solve it?**
  **Any additional tips always welcomed..**
  **Please try to elaborate as much as possible.**
  **(Appreciate your time and thanks for reading.)**

---

### Post by oldfred on 2013-01-17
Welcome to the forums.

Were you planning on installing Ubuntu?

Fedora often installs to LVM which is a different partitioning and needs extra drivers to be seen from Ubuntu.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)


Not sure if it sees Fedora in its LVM install or not.

       
 An easy way [OS-Uninstaller] Safely remove Windows, Ubuntu... in 1 clic ! 
[http://ubuntuforums.org/showthread.php?t=1769489](http://ubuntuforums.org/showthread.php?t=1769489)
[https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

---

### Post by anup1234 on 2013-01-17
> **oldfred said:**
> Welcome to the forums.

Were you planning on installing Ubuntu?

Fedora often installs to LVM which is a different partitioning and needs extra drivers to be seen from Ubuntu.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)


Not sure if it sees Fedora in its LVM install or not.

       
 An easy way [OS-Uninstaller] Safely remove Windows, Ubuntu... in 1 clic ! 
[http://ubuntuforums.org/showthread.php?t=1769489](http://ubuntuforums.org/showthread.php?t=1769489)
[https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

thanks for reply,
problem here is I am not able to boot a Live CD also (as i tried to boot throuch GParted live and it showed me various "buffer I/O errors" etc) so i am guessing UBUNTU Live CD also won't boot.

---

### Post by audiomick on 2013-01-17
It might be a good idea to run memtest and see if your RAM is ok. That is an option on  the Ubuntu live CD. I think you have to make it go to the menu. As it runs up, you get a purple screen with two icons at the bottom. I think hitting any key will make it go to the menu. I'm not quite sure because I always use the cursor arrow keys.

You need to let memtest run for a while, like a couple of hours. It should show zero errors. If it shows any errors at all you have a RAM problem.

---

### Post by sandyd on 2013-01-17
Also, make sure your motherboard is ok, (i.e. no busted capacitors, replug all sata connectors, .etc .etc). If your CD/DVD drive is SATA as well, it sounds like your SATA controller/connectors are having issues...

-----------------------------------------
nvm - not reading properly
[s]
Run a Ubuntu LiveCD, open a terminal, and post back with the output of the following commands. You have to have internet.
```

sudo apt-get install smartmontools
sudo smartctl -i /dev/sda
sudo smartctl --test=short /dev/sda
#Get out of your chair, walk around for 5 minutes, and come back before continuing
sudo smartctl -a /dev/sda
```
The commands will evaluate the health of your HDD via its SMART status (unless your drive is too old and doesn't support SMART)[/s]

---

### Post by anup1234 on 2013-01-17
thanks I'll carry out Memory test and will see if RAM is good.

---

### Post by anup1234 on 2013-01-17
> **sandyd said:**
> Also, make sure your motherboard is ok, (i.e. no busted capacitors, replug all sata connectors, .etc .etc). If your CD/DVD drive is SATA as well, it sounds like your SATA controller/connectors are having issues...

-----------------------------------------
nvm - not reading properly
[s]
Run a Ubuntu LiveCD, open a terminal, and post back with the output of the following commands. You have to have internet.
```

sudo apt-get install smartmontools
sudo smartctl -i /dev/sda
sudo smartctl --test=short /dev/sda
#Get out of your chair, walk around for 5 minutes, and come back before continuing
sudo smartctl -a /dev/sda
```The commands will evaluate the health of your HDD via its SMART status (unless your drive is too old and doesn't support SMART)[/s]


ok will try it hope it helps,thanks.

---

