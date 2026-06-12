---
title: "dual boot issue"
date: 2013-03-20
forum: New to Ubuntu
---

### Post by Ian Wilkinson on 2013-03-20
I have installed ubuntu allongside windows7  64bit on seperate hdd, on reboot sysem would only see and boot to windows os, after using boot repair via live disk grub reinstall and grub update, on reboot the system now shows ubuntu grub and boots to ubuntu  the option to boot to windows partiton is not visable, tried using windows repair disk to repair boot files no joy, here is some info update grub threw up.  generating grub. cfg...       found linux image:boot/vmlinuz-3.5.0-17-generic    found initrd image: /boot/initrd.img 3.5.0-17-generic    found memtest86+ image: /boot/memtest86+bin     error: ddf1:wrong# os devices in raid set "ddf1_ssdraid" [1/2] on /dev/sdd done.   hope this helps if any more info is needed let me know

---

### Post by oldfred on 2013-03-20
Do you have RAID, or was a drive every RAID, or was system Intel SRT (UltraBook)?

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by Ian Wilkinson on 2013-03-20
[http://paste.ubuntu.com/5629389](http://paste.ubuntu.com/5629389)             to answer your question on  raid   i'm not sure,  i have multiple hdd in a system that has raid, but  as i understand raid the drives need to be the same size for raid to  work properly, if i'm not right please let me know   all the hdd  installed on my system are different sizes and brands, so as far as i  was aware raid was not enabled, could the ubuntu instalation of enabled  this?  hope this helps  i think i can disreguard intel srt   this is an  amd desktop  system, if you need any more info just ask

---

### Post by oldfred on 2013-03-20
It looks like this drive sdd was once RAID. Drives retain the meta-data. And then tools will not work on RAID drive as they should not if it really is a RAID drive.
> 
ERROR: ddf1: wrong # of devices in RAID set "ddf1_SSDRAID" [1/2] on /dev/sdd

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sdd

It looks like you have grub in every drive. I would reinstall a Windows boot loader to your Windows drive.

After removing RAID and booting, you will have to run this to get os-prober to add Windows to your grub menu.

sudo  update-grub

---

### Post by Ian Wilkinson on 2013-03-21
ok checked to see if raid is enabled in bios  it is not,     booted to live disk and ran the code provided   	 	 	 	   ian@ian-GA-MA780G-UD3H:~$ sudo dmraid -E -r /dev/sdd  
 [sudo] password for ian:  
 Do you really want to erase "ddf1" ondisk metadata on /dev/sdd ? [y/n] :y  
 ERROR: ddf1: seeking device "/dev/sdd" to 46094490533888  
 ERROR: writing metadata to /dev/sdd, offset 90028301824 sectors, size 0 bytes returned 0  
 ERROR: erasing ondisk metadata on /dev/sdd  
 ian@ian-GA-MA780G-UD3H:~$  
    rebooted and updated-grub  the same error message is still showing

---

