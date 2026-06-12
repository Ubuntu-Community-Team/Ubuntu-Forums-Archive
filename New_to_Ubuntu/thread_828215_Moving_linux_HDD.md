---
title: "Moving linux HDD"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by Karakh on 2008-06-13
Hi guys. I have a computer with 2 HDDs:

HDD1: XP (work)
HDD2: Ubuntu (mint 5.0)

And I basically need to remove the second HDD without affecting the XP drive. and place it in another (almost) Identical box.

Is it possible to do this without formating either drive? I could (if it's my only option) format the Linux drive, but the XP drive needs to be untouched. 

Will I be able to get the original box to boot directly to XP?

Thanks guys.

---

### Post by gr4nf on 2008-06-13
You could simply move the HD physically.

If you are adverse to doing that, you could simply put the following things:
/home
/root (if there's anything inside)
/pmi (if you have one)
and /etc
all in an external volume, and then install ubuntu on the other computer, and put thos files in it.

---

### Post by burakerenn on 2008-06-13
Sure system will work properly if you just remove 2nd harddrive (linux one), but probably grub will give an error and won't open. If it happens you'll need to boot computer with your XP cdrom, go to recovery console and type fixmbr . It'll recreate windows' boot loader.

---

### Post by Karakh on 2008-06-13
Sorry, I should have added that when I remove HDD2 from the original box, I get a grub error (error 21 if I remember correctly) I assume that grub was installed on HDD2.

---

### Post by stchman on 2008-06-13
> **Karakh said:**
> Hi guys. I have a computer with 2 HDDs:

HDD1: XP (work)
HDD2: Ubuntu (mint 5.0)

And I basically need to remove the second HDD without affecting the XP drive. and place it in another (almost) Identical box.

Is it possible to do this without formating either drive? I could (if it's my only option) format the Linux drive, but the XP drive needs to be untouched. 

Will I be able to get the original box to boot directly to XP?

Thanks guys.

GRUB wrote a boot installer to the HDD1 drive.  That is easy enough to remove using the fdisk /mbr command using a DOS boot disk.

When you put the second HDD2 drive in a nother PC if you with to use the Linux installation you will need to reinstall GRUB.

---

### Post by Karakh on 2008-06-13
OK, I just tried fixmbr in recovery mode, and when I restarted, I got an NTLDR error.

As for stchmans suggestion, I neither have a DOS boot disk, or a floppy drive.

---

### Post by Karakh on 2008-06-13
I just found this possible solution, but I want your expert opinions before I try it, I really can't afford to lose the XP HDD.



   1.  Insert the Windows XP bootable CD into the computer.
   2. When prompted to press any key to boot from the CD, press any key.
   3. Once in the Windows XP setup menu press the "R" key to repair Windows.
   4. Log into your Windows installation by pressing the "1" key and pressing enter.
   5. You will then be prompted for your administrator password, enter that password.
   6. Copy the below two files to the root directory of the primary hard disk. In the below example we are copying these files from the CD-ROM drive letter "E". This letter may be different on your computer.

      copy e:\i386\ntldr c:\
      copy e:\i386\ntdetect.com c:\

   7. Once both of these files have been successfully copied, remove the CD from the computer and reboot.

---

### Post by Hospadar on 2008-06-13
> **Karakh said:**
> I just found this possible solution, but I want your expert opinions before I try it, I really can't afford to lose the XP HDD.



   1.  Insert the Windows XP bootable CD into the computer.
   2. When prompted to press any key to boot from the CD, press any key.
   3. Once in the Windows XP setup menu press the "R" key to repair Windows.
   4. Log into your Windows installation by pressing the "1" key and pressing enter.
   5. You will then be prompted for your administrator password, enter that password.
   6. Copy the below two files to the root directory of the primary hard disk. In the below example we are copying these files from the CD-ROM drive letter "E". This letter may be different on your computer.

      copy e:\i386\ntldr c:\
      copy e:\i386\ntdetect.com c:\

   7. Once both of these files have been successfully copied, remove the CD from the computer and reboot.

I've had success with this method, just be sure not to delete those files after you copy them.  It'd be best to go in after with windows and make them hidden after you get things working.

---

### Post by Karakh on 2008-06-13
It didn't work..... I'm back to getting a Grub error when I remove HDD2. Any ideas?

---

### Post by logos34 on 2008-06-13
boot back into the xp install cd recoovery console, but this time do

**fixboot c:**

---

