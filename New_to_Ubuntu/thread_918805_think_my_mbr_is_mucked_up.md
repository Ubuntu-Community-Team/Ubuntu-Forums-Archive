---
title: "think my mbr is mucked up"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by socialsupernova on 2008-09-13
I jump around from operating to operating system a lot. Things got kinda screwy after i installed leopard. It took me forever to install xp after that. windows wouldn't recognize my drives and i still don't know how i worked it out but i manged to get vista on it and i have been unhappily running it for a few months now. I guess you could say it's my default os which is a bummer. trying to learn as much as i can about ubuntu before that perrty ibex comes around. After installing hardy, I took the disc out and rebooted only to land on this: 

"Reboot and select proper boot device or insert boot media in selected boot device"

Since then i reinstalled ubuntu and at the very end of the installation prompt i went under some kinda advanced tab and installed some bootloader thing. Now upon reboot I get:

Error 17:cannot mount selected partition

I should have prefaced all of this with the I'm a total beginner to linux and know very little about it. Any advice? tryin to make this my Saturday project

---

### Post by bumanie on 2008-09-13
[Follow this]("http://ubuntuforums.org/showthread.php?t=224351") to reinstall grub from the live ubuntu cd or get super grub disk. Could also be that your bios has got the hard drive order wrong since you changed your disks around - check your bios settings too. [Check here too]("http://users.bigpond.net.au/hermanzone/p15.htm"), about 2/3 down the page is heaps of info. on grub errors + possible fixes

---

### Post by socialsupernova on 2008-09-13
I tried reinstalling grub and it did't work, I still got error 17. I tried reinstalling ubuntu again without doing the advanced bootloader and i still got the same result. I tried super grub disk and I'm not sure if i did everything right but it seemed pretty straight forward. still no go. I went into the bios and disabled all the other drives and im still not booting.

---

### Post by unutbu on 2008-09-13
Hi socialsupernova, welcome to the forums.
Please help us by providing the info requested here:
[http://ubuntuforums.org/showpost.php?p=5584686&postcount=465](http://ubuntuforums.org/showpost.php?p=5584686&postcount=465)

---

### Post by soxs on 2008-09-13
run testdisk and flush your mbr and then, afterwards reinstall grub into MBR again.. worked for me a couple of times.

---

### Post by socialsupernova on 2008-09-13
1. fresh installation problem
2. error after the count before the menu. i can get to the menu with the push of any button but neither the generic or the generic (recovery mode) work.
3. is the "GRUB command-line prompt" the menu is was referring to in #2?
4.```

   Device Boot      Start         End      Blocks   Id  System

/dev/sdc1            1         8666   69609613+    83  Linux
/dev/sdc2           8667       9039     2996122+   5   Extended
/dev/sdc5           8667       90393     2996091   82  Linux swap / Solaris

```
5. will edit this post with info soon. the computer is not connected to the internet and im not about to type all this.

---

### Post by unutbu on 2008-09-13
If you have a USB Flash drive, or a floppy drive, you can save the file on to the USB (or floppy) and then port it to a machine with an internet connection. 

If you are dual booting, and the other OS has an internet connection, I can give you instructions on how to copy the file over to a partition where the other OS can read it.

Or, if neither of the above is convenient, use the file browser to go to /boot/grub/menu.lst. Double-click it to open it up in a text editor. 
Scroll down 2/3 of the way, and look for a stanza that looks something like this:
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=03a507ee-cdac-4bd9-b438-eccd616b66ed ro 
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

```
Just post that.

---

