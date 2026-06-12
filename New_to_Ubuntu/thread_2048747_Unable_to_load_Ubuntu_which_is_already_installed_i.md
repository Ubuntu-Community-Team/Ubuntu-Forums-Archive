---
title: "Unable to load Ubuntu which is already installed in my laptop"
date: 2012-08-27
forum: New to Ubuntu
---

### Post by kanti123 on 2012-08-27
Hi Every one,

I was using Ubuntu in my lap along with windows 7,but when i installed virtual machine to use windows xp in windows 7 for specific needs, from then i was unable to load the Ubuntu which used to ask when i switch on the laptop , i am unable find what is the problem and drives are still present ..

So Please Help me regarding this , i have important files in Ubuntu which should be recovered.

Thanku In Advance :p

---

### Post by NikTh on 2012-08-27
Hi , 
did you install ubuntu via wubi (from inside windows) or a regular dual-boot (with grub bootloader) ? 
Thank you.

---

### Post by kanti123 on 2012-08-27
Hi,

It was installed using regular dual-boot (with grub bootloader).

---

### Post by Mark Phelps on 2012-08-27
From what you say, it sounds like the install overwrote the drive MBR so that the GRUB code got removed.

IF you only want to recover your file in the Linux filesystem, just boot from a LiveCD or LiveUSB and copy the files to another partition or to an external drive.

If you want to restore boot for Ubuntu, you will need to reinstall GRUB.  The instructions are in the link below:

[http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by kanti123 on 2012-08-28
hey mark thank u for solution , but if i reinstall my Grub does it  effect my windows7 ??

---

### Post by Bashing-om on 2012-08-28
kanti123;

  Linux is very smart, grub boot-loader will detect the windows operating system and chain load accordingly (no experience with virtual machine, so do not know how the boot code will load) / We are only operating on the MBR and no operations will touch the actual operating system's files.....

  Advice: Read and Heed the above listed link..great tutorial....

[INDENT]ask and thou shalt be given <==BDQ

[/INDENT]

---

### Post by kanti123 on 2012-08-28
Hey Thanku Every One For the Solution,It was a great Help..:guitar:

---

