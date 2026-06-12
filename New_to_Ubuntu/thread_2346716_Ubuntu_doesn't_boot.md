---
title: "Ubuntu doesn't boot"
date: 2016-12-17
forum: New to Ubuntu
---

### Post by lefterios on 2016-12-17
Hey guys!
I'm trying some time to get ubuntu working on my laptop(Asus N552VX) but always something goes wrong. At first the installation stuck in loading screen and the pc froze. I rebooted some times and tried again and then it finally started the installation. I was able to install ubuntu without a problem but there were many bugs (browsers were very slow, booting and shutting down time was very long). Something did'nt go well. I then tried to install other linux distributions:
Debian seemed good and installed well but after first reboot it would'nt boot.
MintOS basically the same.
And then I tried also lubuntu and kubuntu. Lubuntu didn't boot after installation and kubuntu didn't load the installation.
This is very weird as I have installed Ubuntu in other computers and it works fine.
Is there a problem with the computer? Does it need any specific steps? If you need some other info about hardware or the bugs that exist tell me but I don't think that really matters...:confused:
Any help would be appreciated and sorry for the total noob questions.
Also I'm dual booting with Windows 10.

---

### Post by oldfred on 2016-12-17
Most of the newer Asus seem to need boot parameters.
With nVidia you may need nomodeset to install & first boot, or until you install nVidia driver into actual install.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[URL="https://wiki.ubuntu.com/Kernel/KernelBootParameters"]https://wiki.ubuntu.com/Kernel/KernelBootParameters

      [/URL]
 ASUS ROG GL552VW-CN104T
[http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters](http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters)
Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3)
[https://ubuntuforums.org/showthread.php?t=2327570](https://ubuntuforums.org/showthread.php?t=2327570)
Installing 15.04 on Asus N550JX, boot parameters required
[http://ubuntuforums.org/showthread.php?t=2293394](http://ubuntuforums.org/showthread.php?t=2293394) 
    [URL="https://wiki.ubuntu.com/Kernel/KernelBootParameters"]
[/URL]

---

### Post by lefterios on 2016-12-21
> **oldfred said:**
> Most of the newer Asus seem to need boot parameters.
With nVidia you may need nomodeset to install & first boot, or until you install nVidia driver into actual install.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[URL="https://wiki.ubuntu.com/Kernel/KernelBootParameters"]https://wiki.ubuntu.com/Kernel/KernelBootParameters

      [/URL]
 ASUS ROG GL552VW-CN104T
[http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters](http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters)
Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3)
[https://ubuntuforums.org/showthread.php?t=2327570](https://ubuntuforums.org/showthread.php?t=2327570)
Installing 15.04 on Asus N550JX, boot parameters required
[http://ubuntuforums.org/showthread.php?t=2293394](http://ubuntuforums.org/showthread.php?t=2293394) 
    [URL="https://wiki.ubuntu.com/Kernel/KernelBootParameters"]
[/URL]

Thanks for the help that worked! But still when I sut down the laptop it simply doesn't... There is just a black screen. Also touchpad doesn't work. Is there any way to find drivers for Linux?

---

### Post by oldfred on 2016-12-21
Did you install a nVidia driver?
You need nomodeset as boot option until you install nVidia driver. Other boot parameters may still be required.

I have seen threads on touchpads, not even sure of models, but have not followed those. Best to search forum and if no results that work, post new thread with that in title.

---

