---
title: "Problem installing ubuntu"
date: 2018-10-06
forum: New to Ubuntu
---

### Post by dan7028 on 2018-10-06
I'm a complete newbie so the solution to this is probably painfully obvious.

I'm trying to dual boot win 10 and ubuntu. I've created the live USB to install ubuntu from and i can get to the install menu that lets me choose if i want to try ubuntu or install it. However whichever option i select i get a black screen for a few seconds before the ubuntu loading screen appears for about 10 seconds. After this instead of either letting me install ubuntu or try it out i am taken back to the initial menu asking me whether i want to try ubuntu or install. I have tried using 3 different USB drives and that hasnt made a difference. 

Im using a hp envy laptop if that makes a difference.

Any help would be appreciated

---

### Post by Autodave on 2018-10-06
Did you disable *fastboot* in the bios?  That must be done.  Also, did you do a defrag and then create a partition while in Windows?

---

### Post by oldfred on 2018-10-06
What exact model HP Envy?
What video card/chip?

Have you updated UEFI from HP? And if SSD updated firmware?

---

### Post by dan7028 on 2018-10-07
Thanks for the reply. I have disabled secure boot in bios and disabled fastboot from within windows, i cant see a fastboot option within the bios. I have also created a new partition from within windows but i didnt defrag as the laptop has an SSD.

---

### Post by dan7028 on 2018-10-07
The model is HP ENVY 13-ah0003na and it has an mx 150. I haven't tried updating the UEFI yet so ill try that next and see if that solves the problem.

---

### Post by oldfred on 2018-10-07
With an nVidia card/chip you need nomodeset to boot live installer & first boot after install or until you install the nVidia driver from Ubuntu repository.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[URL="http://ubuntuforums.org/showthread.php?t=1613132"]http://ubuntuforums.org/showthread.php?t=1613132

      [/URL]
 If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351) 
    [URL="http://ubuntuforums.org/showthread.php?t=1613132"]
[/URL]

---

