---
title: "Old laptop won't boot, &quot;GRUB loading... Error 18&quot;"
date: 2012-02-15
forum: New to Ubuntu
---

### Post by colours67 on 2012-02-15
Hello, everyone. I've read similar threads about this problem but I'm not sure what to do specifically.

I borrowed an old laptop (pre 2005) from my sister. Years ago, she installed a version of ubuntu onto a hard drive partition, and I think an ubuntu "safe mode" onto another one. There's Windows XP partition as well.

I've been using the Windows partition. Everything was working well.

Then a week ago, I tried to turn on the computer and almost immediately it says[INDENT][I]GRUB stage 1.5.

GRUB Loading, Please Wait
Error 18[/I]
[/INDENT]It refuses to boot. It just sits at the screen. I can't type anything. It's just that screen. Restart and restart - the same error.
I don't know what version of ubuntu it is, but I know it was downloaded before 2006.

**I read in the other threads that I need to download a "live cd". Can someone give me a link? ** I really don't understand what I'm supposed to download - grub, grub-legacy or re-install ubuntu or what?

So okay after that then, do I just put the CD in and restart the computer? is there something I need to type?

---

### Post by oldfred on 2012-02-15
Error 18 is from grub legacy, new installs use grub2.
[http://members.iinet.net.au/~herman546/p15.html#18](http://members.iinet.net.au/~herman546/p15.html#18)

How much memory does computer have. New versions require more memory to work well, but there are some lighter weight versions of Ubuntu.

this from somewhat older version.
[https://help.ubuntu.com/10.10/installation-guide/i386/minimum-hardware-reqts.html](https://help.ubuntu.com/10.10/installation-guide/i386/minimum-hardware-reqts.html)

[http://www.ubuntu.com/](http://www.ubuntu.com/)
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Lubuntu, which uses the LXDE desktop environment, targeted at "normal computers" with 128 MB
With 512Mb of RAM and almost any processor, Lubuntu will perform more than adequately out-of-the box. 
I'd suggest to check amjjawad's thread (Lubuntu One Stop Thread) and you'll find many useful information.
[http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)
Lubuntu is an Operating System that is using LXDE.
[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)
Lubuntu one stop thread - amjjawad
[http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)

---

### Post by colours67 on 2012-02-15
?
Are you saying I download a new version of ubuntu to a CD?
So I put the CD into the laptop, restart, and the computer will boot up?

---

### Post by snowpine on 2012-02-15
What does your sister want, considering it is her laptop? :)

---

### Post by colours67 on 2012-02-15
She has a brand new laptop. She just gave this old laptop to me to use because I didn't want to buy a new one.

Thanks for replying over at [linuxquestions]("http://www.linuxquestions.org/questions/linux-newbie-8/old-laptop-wont-boot-grub-loading-error-18-a-929538/") too.
I still don't understand what I should do. Most of the other threads I've read - and it seems **oldfred** here - seem to say I need to make an ubuntu live cd - presumably re-install ubuntu. ??
But at linuxquestions, you guys are saying I just need to repair the Windows bootloader and everything will be fine, all the files will be there, etc. ??

---

### Post by oldfred on 2012-02-15
If you just want Windows you can reinstall the Windows boot loader. If error is not just grub, but system then Windows may not work either.

If you have the XP disk, just run the fixMBR command from the repair screen.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Since you were in the Linux forum and not a Windows forum, we assume you wanted to repair Ubuntu. If version is that old, it would not be easy to update, so a new install probably would be required. Yes, you can boot from a liveCD and have a working system. CD is slower than from a hard drive.

---

### Post by colours67 on 2012-02-15
Can you explain why I can fix the boot-up problem by re-installing the *Windows *bootloader when the screen says "*GRUB *loading... Error 18" ?
So I can leave ubuntu alone and re-install the Windows bootloader and Windows will be okay? So ubuntu might not boot anymore but I can access Windows (where my files are!!) ?

---

### Post by snowpine on 2012-02-15
> **colours67 said:**
> 
So I can leave ubuntu alone and re-install the Windows bootloader and Windows will be okay? So ubuntu might not boot anymore but I can access Windows (where my files are!!) ?

Exactly, you got it. :)

---

### Post by click4851 on 2012-02-15
course you could try superGrubdisk and repair the bootloader.

---

### Post by oldfred on 2012-02-15
If you really want to know how computers and Windows boot in MBR type drives this has lots of info. If you just want some idea review the pictures.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

