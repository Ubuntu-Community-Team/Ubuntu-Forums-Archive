---
title: "How to remove another linux partition and keep ubuntu?"
date: 2012-07-16
forum: New to Ubuntu
---

### Post by User1101 on 2012-07-16
I have installed linux mint on half of my hard drive and ubuntu 12.04 on the other half. Now i want to remove linux mint and "reclame" that space for my ubuntu, how do i do this? :confused:
 
Also when i try installing nmap and g++ on ubuntu it says:
E: package nmap has no instalation candidate...
 
 
Thanks...

---

### Post by bobsan on 2012-07-16
Depending on how you set it up. If Ubuntu controls boot and is on the left to the Mint partion, then you can simply boot from a live usb (Ubuntu or Mint or anything that has gparted), use gparted to delete the Mint partition and then expand the adjacent Ubuntu partition to the right (may be your Ubuntu ./home partition, or just Ubuntu if you don't have a ./home partition) It may take a while. After that boot into Ubuntu and in the terminal run "sudo update-grub".  

To be absolutely clear you should provide a screenshot of your setup.

---

### Post by TheFu on 2012-07-16
> **User1101 said:**
> I have installed linux mint on half of my hard drive and ubuntu 12.04 on the other half. Now i want to remove linux mint and "reclame" that space for my ubuntu, how do i do this? :confused:
 
Also when i try installing nmap and g++ on ubuntu it says:
E: package nmap has no instalation candidate...
Thanks...

This boot-info script [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) will help you determine which partitions are used by each OS.  

Then you can simply mount the "mint" partition from inside Ubuntu and remove all the files you don't want.  If you have HOME directory files that you'd like to retain, copy them over to the HOME on Ubuntu first.

If you aren't already doing this, it is a really good idea to have 3 partitions for a Linux desktop.
1) The OS - usually /
2) HOME - /home
3) Swap

In the old days, we'd create partitions for /usr/local and /var too, then mount all the programs over the network for /usr to save space across 5-200 machines.

If you want to play with interesting file systems, you might want /boot to be a different partition too since booting isn't supported from every file system available. If you are using EXT4, this doesn't matter at all.

Sorry - that was probably more than you wanted.

To clean up the old Mint install from the grub menu, look for a grub howto on that. Be certain you are using the correct howto for your exact version of grub. I know it is confusing to me.

Concerning nmap, I'd run 'sudo synaptic' and search for nmap in the list of programs. It was available in my LXDE based Ubuntu Server install. No PPA needed.  For g++, you might want to install the meta-package 'build-essential' instead, but g++ should be installable alone. I see it here.

---

### Post by User1101 on 2012-07-17
> **TheFu said:**
> This boot-info script [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) will help you determine which partitions are used by each OS. 
 
Then you can simply mount the "mint" partition from inside Ubuntu and remove all the files you don't want. If you have HOME directory files that you'd like to retain, copy them over to the HOME on Ubuntu first.
 
If you aren't already doing this, it is a really good idea to have 3 partitions for a Linux desktop.
1) The OS - usually /
2) HOME - /home
3) Swap
 
In the old days, we'd create partitions for /usr/local and /var too, then mount all the programs over the network for /usr to save space across 5-200 machines.
 
If you want to play with interesting file systems, you might want /boot to be a different partition too since booting isn't supported from every file system available. If you are using EXT4, this doesn't matter at all.
 
Sorry - that was probably more than you wanted.
 
To clean up the old Mint install from the grub menu, look for a grub howto on that. Be certain you are using the correct howto for your exact version of grub. I know it is confusing to me.

 
Thanks a lot for that man, i just recently made the sitch from all Windows to now windows and linux, windows more for my gaming and other stuff. Linux on the other hand is wonderfull for programming and cyberphorensics. 
 
> 
Concerning nmap, I'd run 'sudo synaptic' and search for nmap in the list of programs. It was available in my LXDE based Ubuntu Server install. No PPA needed. For g++, you might want to install the meta-package 'build-essential' instead, but g++ should be installable alone. I see it here.

 
I dont know why nmap and g++ did that, but after i updated the entire OS with it's update manager it ran the commands again and this time it gave no such error.:-k
 
Thanks man... :)

---

### Post by TheFu on 2012-07-17
> **User1101 said:**
> I dont know why nmap and g++ did that, but after i updated the entire OS with it's update manager it ran the commands again and this time it gave no such error.:-k
 
Thanks man... :)

No problem.

You should always **apt-get update** and  **apt-get  dist-upgrade** to get current versions of things before trying to install new software unless you really, really know what you are doing.  I do this weekly when I have a few hours should something happen. 99% of the time, nothing bad happens, unless a Xen kernel update happens, then it is a 20% chance I'll be backing out to an older kernel. On all my non-Xen machines, I can't remember the last issue that prevented doing other things first.  I'm still trying to recover from a Win7 update 2 months ago that broke HDMI and sound for me.

If you don't want to get a new kernel (if one is available), just use   **apt-get upgrade** instead. Kernel updates require a reboot to become active.

Running  **apt-get update** daily doesn't harm anything, but I think doing an upgrade daily is a little too much hassle for me.

Glad to help.  There are so many times when others have helped me here. It is nice to give a little payback when I can. That doesn't happen too often. I don't really know all that much, especially about desktops since I stopped using the default Ubuntu desktop about 3-4 yrs ago due to bloat.

Marking this thread as [SOLVED] would help others.

---

### Post by YannBuntu on 2012-07-20
> **User1101 said:**
> Now i want to remove linux mint and "reclame" that space for my ubuntu, how do i do this?

You can uninstall any OS (Mint, Ubuntu, Windows, ...) via this little tool: [https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

[IMG]http://pix.toile-libre.org/upload/original/1340275988.png[/IMG]

---

### Post by NikTh on 2012-07-20
> **YannBuntu said:**
> You can uninstall any OS (Mint, Ubuntu, Windows, ...) via this little tool: [https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)



=D>=D>=D>

I didn't know about this tool. 
Thanks YannBuntu.

---

