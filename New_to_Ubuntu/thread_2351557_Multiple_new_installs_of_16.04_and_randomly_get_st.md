---
title: "Multiple new installs of 16.04 and randomly get stuck while trying to boot into 16.04"
date: 2017-02-04
forum: New to Ubuntu
---

### Post by ricciolo on 2017-02-04
Hi, I dual booted my laptop (ASUS Zenbook Flip UX360CA) with Windows 10 and Ubuntu 16.04. I installed Ubuntu 16.04 from a bootable USB. After the initial install, I was prompted to restart my computer, after which I was able to log in start customizing features. I turned off the computer, and when I went to start it again, I got a black screen after choosing Ubuntu (from grub). Because I was impatient, I turned the computer off and on again; I was able to get in this time. I ran Boot Repair, but I'm not sure that fixed the issue because it says that it couldn't mount /dev/sda2 (which, according to fdisk, is a Microsoft reserved partition). I just don't want to run into a kernel panic down the road or have Ubuntu sometimes be able to boot and other times not. I also don't want to have to keep turning my computer on and off. 

I also tried running Boot Repair from the USB, which didn't work (same issue as previously described). The link for that is here: [http://paste2.org/ajxgnFkD](http://paste2.org/ajxgnFkD). 

I've done some Googling and people are saying the black screen at start-up may be due to the Nvidia graphics card, but I think mine is an Intel one (according to the results from ls /sys/class/backlight). 

I've reinstalled multiple times with the same problem (and making a new bootable USB). I've also tried deleting the Ubuntu partition and starting from scratch.

---

### Post by oldfred on 2017-02-04
Boot-Repair shows error on both Microsoft reserved & bios_grub type partitions as they are unformatted and Linux partition tools seem to not like unformatted partitions. That is not a problem.

If you go into UEFI boot menu, often f10 for f12, check your manual can you boot the ubuntu entry?

Some Asus need a boot parameter:
 Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3)
[https://ubuntuforums.org/showthread.php?t=2327570](https://ubuntuforums.org/showthread.php?t=2327570) 

This is now older Ubuntu version, and 16.04 should be better.

 Asus UX303UB hardware problems - a list  15.10
[http://ubuntuforums.org/showthread.php?t=2319066](http://ubuntuforums.org/showthread.php?t=2319066)

---

### Post by ricciolo on 2017-02-06
If I press F2 (and get to the BIOS screen), I can boot into Linux. When I get the grub menu, I can also see Ubuntu as one of the boot options. The biggest issue I'm running into now is that when I select Ubuntu from the grub menu, sometimes Ubuntu doesn't start; I just get a black screen. However, if I turn the computer off/on and boot into Ubuntu again, I'm able to see the log in screen. I don't understand why that's happening.

**edit: **To recap, I should try to add "pci=nomsi" to the grub configuration file? Do I have to do that at the grub menu, or can I do that once I log in and run sudo update-grub? Sorry to ask so many questions. I just really don't want to mess with grub and then end up not being able to boot at all...

---

### Post by oldfred on 2017-02-06
You can test if the pci=nomsi entry works as you boot. But that is just for that boot only.
Add it just like the instructions for nomodeset.

But if always needed you want to permanently add it to grub's menu.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) 


 sudo nano /etc/default/grub 
sudo update-grub

---

### Post by ricciolo on 2017-02-11
I did some more googling/research, and the black screen is a graphics card issue. If I wait after selecting Ubuntu from the grub menu, then the login page comes up and I can use the computer normally.

---

### Post by oldfred on 2017-02-11
#To see what video you have:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA

---

