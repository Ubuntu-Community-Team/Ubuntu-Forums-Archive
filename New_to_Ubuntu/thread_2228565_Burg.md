---
title: "Burg"
date: 2014-06-08
forum: New to Ubuntu
---

### Post by Damon_Harris on 2014-06-08
I have some problems:
  
[LIST=1]
[*]I Got Anger At Ubuntu and uninstalled it (I Have already installed windows 8.1)

[*]Now I cant access my hard drive because of my fast boot feature in Windows.
[/LIST]
  Now I thought of reinstalling Ubuntu to access my hard drive, but  while installinG it only shows 3 partitions of Linux I cant find the  Windows's partitons, 
  my fear is that it shows all the space including the space occupied  by Windows where I have to install Ubuntu (I mean if I install Ubuntu I  am afraid that my Windows data will be deleted.)
  I Have a live USB of Ubuntu and I need to install Burg on my PC (please provide me a step-by-step instruction)
  If you need any additional info, tell me.
  And I have a efi file of BURG

---

### Post by Rob Sayer on 2014-06-08
I'm not an expert on UEFI but I can categorically state that installing BURG is not going to help.  Besides, according to this:

[https://wiki.archlinux.org/index.php/BURG](https://wiki.archlinux.org/index.php/BURG)

it hasn't been maintained since 2010.  SO how the hell is it supposed to work with UEFI?

A common noob mistake is to think that if their ubuntu system isn't configured for some of their hardware that installing some program that is accesses it on the GUI level will fix it.  It won't.  I've seen this here with wireless issues mostly.  You need to figure out the underlying issues.

The first thing I'm curious about is that you say "[COLOR=#000000]I Have already installed windows 8.1[/COLOR]" but that you can't find your windows partitions.  I fear you may have deleted the windows partitions.  Some noobs select that install option because it looks easiest and then can't understand why they don't have windows anymore.

Boot from the live USB, open the terminal, and copy and paste this:

sudo fdisk -lu

and post the results here, in [CODE] tags.

---

### Post by Damon_Harris on 2014-06-11
1. I am not a noob
2. I am installing it for GUI
3. I am installing it for identifying windows
4. I didn't select install option, i selected "something else" option and did stuff which has to be done

---

### Post by Vladlenin5000 on 2014-06-11
Neither Ubuntu installer nor anything else is able to "see" the typical hibernated partitions resulting from fast boot. What follows is you have to actually shutdown Windows before proceeding. Here's what you should read before before even considering a dual-boot scenario with Windows 8: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2014-06-11
If you have UEFI then you also have gpt partitioning.

Post this:
sudo parted -l

If you want a nice gui with UEFI booting.
       Alternative to grub using refind or gummiboot
[https://wiki.archlinux.org/index.php/Beginners%27_Guide#For_UEFI_motherboards](https://wiki.archlinux.org/index.php/Beginners%27_Guide#For_UEFI_motherboards)
Alternative efi boot Manager for UEFI limited systems:
[https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd](https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd)
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)
[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)

---

