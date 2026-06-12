---
title: "&quot;Failed to Create Kernel Channel&quot; Install Issues"
date: 2016-04-06
forum: New to Ubuntu
---

### Post by riley10 on 2016-04-06
Hello, I am very new to Ubuntu and the world of Linux as a whole so please bear with me. Recently I decided I was going to install Ubuntu on my desktop for everyday use. The method I chose was a USB boot stick which I would use to install on a freshly formatted HDD in my computer. The problem I am having though is that I do not load into the proper boot menu as shown by the [pictures]("https://imgur.com/a/2Dc6F") I took (Sorry for the bad quality). In addition to that, when I choose to install Ubuntu or try it, it blacks out my screen and says "failed to create kernel channel, -22". At this point everything kinda just freezes and I have to manually shut off my PC. I have googled solutions for this problem for hours at this point and all of them begin with the proper boot menu, the purple'ish one, so they are no help. I have also tried to attempt adding "nouveau.modeset=0" to the kernel parameters like many say to do, but I am either not typing it in the right place or it is not working. 

Some of my technical specs that might help:
Intel i5 4690k
Gtx 970 
Corsair Vengeance 1866mhz 2x8gb
Asus ROG Maximus VIII Extreme Mobo
2TB WD Black HDD

The versions of Ubuntu I have tried:
14.04.4-desktop-amd64
15.10-desktop-amd64

All help is greatly appreciated, thanks in advanced.

---

### Post by Bucky Ball on 2016-04-06
Welcome. Try this. When you boot from install media, you should get to a purple screen with an icon at the bottom. Hit any key. You'll get to the options screen. Hit F6 and choose 'nomodeset'. Continue with 'Try Ubuntu'. Any luck? You may be able to get there by hitting 'Advanced options' in the boot screen in your screen shot. 

How did you create the USB? You need free space to install Ubuntu to the hard drive. Nothing Windows can create can be used for Ubuntu install.

Did you 'check disk for defects' (one of the options at the boot screen in your screenshot)?

---

### Post by riley10 on 2016-04-06
I have tried 'nomodeset' and it just took me to a black screen. I created the USB with rufus and have tried a multitude of distros but to no avail. Also the drive I am trying to install it on was freshly formatted and has nothing on it. And when I check for defects it is the same error message.

---

### Post by Bucky Ball on 2016-04-06
Freshly formatted to what? You have NTFS or FAT partitions on there? Ubuntu won't install to them. Leave free, unallocated space for Ubuntu. This may not be your problem but something you should be aware of.

---

### Post by xxfireboy on 2016-05-19
Hello riley10,
I am building a new desktop and I'm using the same Mobo:Asus ROG Maximus VIII Extreme

I hope you have made much progress in getting Ubuntu install by now!
Maybe you could head me in the right direction in installing Ubuntu with
this Mobo, any pointers?

The number one reason I'm posting to your post is I have been searching all over
trying to find out if the Asus OC Panel II(OC Panel-Overclocking Command Center)
works under Ubuntu. I can't find anything on using the OC panel under Ubuntu/Linux.

Does the OC panel function outside the operating systems?
I have read the complete book that comes with the Mobo and OC panel, and the
only thing I can find regarding my quest is the book says to go to their
website to get the up-dated drivers, and all the drivers I have found are for windoz?

Please tell me you got Ubuntu installed and that I don't have to have windoz
for the OC panel to function properly or at all! Thanks in advance!fb

---

### Post by Bucky Ball on 2016-05-20
@xxfireboy: You'll greatly increase your chances of support by posting a new thread with a descriptive title about your problem. Good luck.

---

### Post by xxfireboy on 2016-05-20
Thanks Bucky Ball, that's what I'll do!

---

