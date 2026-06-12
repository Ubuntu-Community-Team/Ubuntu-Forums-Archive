---
title: "Issue Booting into Ubuntu for the First Time"
date: 2019-07-29
forum: New to Ubuntu
---

### Post by niikolaslav on 2019-07-29
Hi, I have installed the latest version of Ubuntu on my PC. When I try to boot into it I get this (Refer to Link). I'm not sure why this is, and I have no clue how to fix it. I don't know if it's because of my Nvidia Geforce GTX 750 Ti, but I'm stuck at this screen. Waiting doesn't fix it either. What do I do?

Image: [https://ibb.co/mTv1vkz](https://ibb.co/mTv1vkz)

---

### Post by SeijiSensei on 2019-07-29
Can you boot successfully from the installation medium by choosing Try Ubuntu?

---

### Post by niikolaslav on 2019-07-29
Yes, I can.

---

### Post by oldfred on 2019-07-29
I now am not sure what may be issue.
It always was that you do not have nVidia driver and have to boot with nomodeset boot parameter.
But newest Ubuntu will now install nVidia driver if you check the box to install restricted extras & drivers.

So did you install nVidia driver or do you need it.
Can you boot with nomodeset?

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[URL="http://ubuntuforums.org/showthread.php?t=1613132"]http://ubuntuforums.org/showthread.php?t=1613132
[/URL]
 #What is installed, once booted
dkms status 
    
If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351) 
    [URL="http://ubuntuforums.org/showthread.php?t=1613132"]
[/URL]

---

