---
title: "Install problem"
date: 2017-12-22
forum: New to Ubuntu
---

### Post by bkelly7769 on 2017-12-22
Environment:  Windows machine with gamer mother board.  There are four SATA drive slots, two used for Windows and the third planned for Ubuntu.  I don't want to shared boot, just select the appropriate drive and go.  I should trust the shared boot system but just don't.
Ubuntu has been downloaded and is on a DVD with the file named: ubunto-16.04.3-desktop-amd64.iso.  Size is 1,550,400 KB
With the dvd inserted it boots to Adriane Knopix.  Looks quite primitive.  Says nothing about Ubuntu.  I had it install to a SATA hard drive and wound up with the same thing.

What do I need to do different?

---

### Post by DuckHook on 2017-12-22
:confused:

How did you download the image? Do so from here: [https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop)

Use torrent if you can because it is more reliable and less impact on the servers.

It is scarcely imaginable that you get Knopix with an Ubuntu download. Is it possible you made a mistake? Downloaded from the wrong site? Burned the wrong image to DVD? Make sure you check MD5 checksum: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Installing is a different matter. I no longer know how to install into a Windows machine. It's been years since I've used Windows and things have changed greatly. I vaguely know that one must turn off secure boot and fast boot, even if you are installing on a completely separate HDD/SSD. You may even wish to disconnect your Windows HDDs during install for more safety.

General cautions still apply: back up all data and have Windows recovery disks made and nearby.

Anything dealing with any form of Windows dualism (I know you're not dual booting) will have to wait for someone more knowledgeable with Windows.

---

### Post by oldfred on 2017-12-22
What specific motherboard. And what video card/chip?
Some require special settings.

UEFI or BIOS install, motherboards in last 5 years are all UEFI, but have CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

I prefer to use flash drives as then you can reuse them if not quite right or you want a newer ISO. When I used DVD, I burned a lot of coasters (bad burns).

You do want to use Something Else install option if multiple drive and multiple install.

      
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader (only works with BIOS install)
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing) 

If UEFI see link below in my signature.

---

### Post by leunam12 on 2017-12-23
What you have to do is go to the official Ubuntu website and download the official
Ubuntu ISO, and verify your download, as suggested by DuckHook; then, you have to unplug
the Windows drive and install Ubuntu while you computer only sees one drive. After
the installation is successful you have to uninstall the os-prober because if you update GRUB
or use apt autoremove the os-prober will see that you have Windows and will create an entry
for it and it may cause problems. Then you may connect your Windows drive again and 
at boot time invoke the temporary boot menu to choose what operating system you want to boot.

---

### Post by bkelly7769 on 2017-12-29
Sorry about the delay, holidays and all.  Read the posts, went back to the site and figured out that I had not made a proper disk.  Right click on the downloaded file and let Roxio burn a proper disk.  It booted into Ubunto.  One of the options was to check the disk so I selected that one.  Did not work well.  The monitor kind of looked like a hex dump, dense with characters in rows, except that only a random 10% of the pixels were present.  None of the characters were readable, just formatted like characters with mostly blank between rows.  Filled about half the screen then stopped.
I had downloaded the same file again, from the Ubuntu site so I burned another disk with the second downloaded file.  Same result.

The file name from my download directory is:

ubuntu-16.04.3-desktop-amd64.iso

I will try burning to a blu-ray disk and see if that matters.  Any chance of that helping?

---

### Post by oldfred on 2017-12-29
I now prefer flash drives, as in past I burned so many coasters(bad DVDs) for one reason or other. Usually user related. 

Not sure if Blue Ray even works?

What video card/chip? Sounds like a video issue.

You many need nomodeset, but then when installed install a proprietary driver.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by RobGoss on 2017-12-30
I do suggest making a complete backup of your system before you go any further, not knowing the installation process can and will, be troublesome in done incorrectly

---

### Post by leunam12 on 2018-01-01
What happens if you just launch the installer instead of trying to check the disk?

---

