---
title: "Natty. I want to uninstall Linux ,,,"
date: 2012-05-05
forum: New to Ubuntu
---

### Post by GiuHei3u on 2012-05-05
Hello and thanks in advance.
I want to uninstall linux and reformat the drive and then decide what linux to install.
How can I uninstall? thanks

---

### Post by Cheesemill on 2012-05-05
No need to uninstall first, just have whatever distro you choose format the entire drive when you install it

---

### Post by jerome1232 on 2012-05-05
Backup your personal data before hand, as it will get deleted when you install the distro of your choice to the entire drive.

---

### Post by GiuHei3u on 2012-05-05
> **Cheesemill said:**
> No need to uninstall first, just have whatever distro you choose format the entire drive when you install it

Well as much as I would like to do that I am going to make the OS dual, both Windows and Linux. Windows for my wife. So what is the best way to do that?

---

### Post by pqwoerituytrueiwoq on 2012-05-05
install windows 1st using what ever amount of space you want windows to have then install the desired linux distro

---

### Post by GiuHei3u on 2012-05-05
> **pqwoerituytrueiwoq said:**
> install windows 1st using what ever amount of space you want windows to have then install the desired linux distro

Perhaps I did not clarify myself so let me try again.
Natty is the entire OS on this computer. I want to completely uninstall it and reformat.
Once that is done I want to install WindowsXP and then later decide which linux version. But for now I only want to uninstall ubuntu, reformat, and install WindowsXP.

thanks!

---

### Post by LemursDontExist on 2012-05-05
> **gumshoegrant said:**
> Perhaps I did not clarify myself so let me try again.
Natty is the entire OS on this computer. I want to completely uninstall it and reformat.
Once that is done I want to install WindowsXP and then later decide which linux version. But for now I only want to uninstall ubuntu, reformat, and install WindowsXP.

thanks!

Just install windows.  

When you're installing windows there should be an option somewhere to partition your drive.  Tell it to erase the Linux partition and create a partition for Windows while leaving enough unpartitioned space for your new Linux installation.  Windows will 'uninstall' Linux for you by erasing the partition and overwriting the boot sector.  No Linux partition + no grub boot record = no trace of Linux on your machine.

---

### Post by GiuHei3u on 2012-05-05
> **LemursDontExist said:**
> Just install windows.  

When you're installing windows there should be an option somewhere to partition your drive.  Tell it to erase the Linux partition and create a partition for Windows while leaving enough unpartitioned space for your new Linux installation.  Windows will 'uninstall' Linux for you by erasing the partition and overwriting the boot sector.  No Linux partition + no grub boot record = no trace of Linux on your machine.

Ubuntu won't allow me. When I put XP in the drive and click on setup.exe the archive manager window opens with this statement,,,

Archive:  /media/VRMPVOL_EN/setup.exe
[/media/VRMPVOL_EN/setup.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /media/VRMPVOL_EN/setup.exe or
          /media/VRMPVOL_EN/setup.exe.zip, and cannot find /media/VRMPVOL_EN/setup.exe.ZIP, period.

---

### Post by coffeecat on 2012-05-05
> **gumshoegrant said:**
> Ubuntu won't allow me. When I put XP in the drive and click on setup.exe the archive manager window opens with this statement,,,

Don't try to run the XP install disc from inside Ubuntu. You have to boot from the Windows XP disc. Make sure your BIOS is set to boot from the optical drive first.

---

### Post by *^kyfds( on 2012-05-05
when you've finally installed windows XP, install whichever version you want using [wubi,]("http://www.ubuntu.com/download/desktop/windows-installer") which makesit far easier to uninstall when later on if change your mind.

good luck!

---

### Post by Cheesemill on 2012-05-05
You need to boot from the Windows CD, you can't run setup from within Ubuntu.

---

### Post by GiuHei3u on 2012-05-05
> **coffeecat said:**
> Don't try to run the XP install disc from inside Ubuntu. You have to boot from the Windows XP disc. Make sure your BIOS is set to boot from the optical drive first.

Thanks CoffeeCat.

---

### Post by iMurshaq on 2012-05-09
Put in the XP cd then turn off computer, turn it back on and push the F12 key repeatedly until it gives you an option to boot from CD-ROM drive. Then install like normal, good luck.

---

