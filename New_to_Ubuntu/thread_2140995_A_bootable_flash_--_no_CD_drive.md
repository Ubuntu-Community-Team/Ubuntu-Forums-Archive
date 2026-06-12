---
title: "A bootable flash -- no CD drive"
date: 2013-05-01
forum: New to Ubuntu
---

### Post by AnneL on 2013-05-01
I am really an absolute beginner and need some guidance before I even try to download any linux files.

Is it possible to make a lightweight ubuntu (probably lubuntu) bootable flash stick for an old laptop 256 MB using for this purpose another laptop, namely a Windows8 netbook which has no CD drive? (I want to find out what is wrong with the old laptop which won't boot from hard drive and refuses to read Windows recovery CD. I have no bootable CD either.) I mean I can't use any CD drive for making ISO and then transferring it to a flash stick. I would like to write down "something" straight to the flash stick using my netbook and then use that stick to boot my old laptop. Can it be done? If so, where can I find any instructions? Until now I have found only recommendations to use CD as "a trans-shippment point". Maybe I should look not to lubuntu but to some other distribution?

---

### Post by 2F4U on 2013-05-01
Lubuntu, as any other *buntu, can be put as live system on a USB stick and either used as live system or installed from there onto hard disk. Instructions on how to do it from different operating systems are available here:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Kopkins on 2013-05-01
You need more than 256 MB for a flash drive.The images are 600+ MB. You can put it straight on a USB drive though. [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Once you have made the USB stick you just have to get the computer to boot from usb. Does the old laptop have 256MB memory? you might have trouble running the live system or even just booting from USB.

---

### Post by AnneL on 2013-05-01
2F4U, thank you for your reply. Do you mean that ubuntu files on a bootable flash key are just the same as on a bootable CD?

---

### Post by AnneL on 2013-05-01
> **Kopkins said:**
> You need more than 256 MB for a flash drive.The images are 600+ MB. You can put it straight on a USB drive though. [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Once you have made the USB stick you just have to get the computer to boot from usb. Does the old laptop have 256MB memory? you might have trouble running the live system or even just booting from USB.
I have heard that even 128MB may be enough for some distributions. I mean RAM. Of course, the flash key will be 2 GB...

---

### Post by Jason Kuzhively on 2013-05-01
This is a comparison between Ubuntu 12.04, Lubuntu 12.04, Xubuntu 12.04 and Kubuntu 12.04: [http://mylinuxexplore.blogspot.in/2012/04/ubuntu-1204-vs-xubuntu-1204-vs-kubuntu.html](http://mylinuxexplore.blogspot.in/2012/04/ubuntu-1204-vs-xubuntu-1204-vs-kubuntu.html)

I personally prefer Xubuntu because I have had *zero *problems with it. Go with 12.04.
Download the ISO of the Ubuntu Flavour you selected. Get UNetbootin from [http://unetbootin.sourceforge.net/&#8206;](http://unetbootin.sourceforge.net/&#8206;) and open it. The rest is pretty simple, you'll figure it out.

There is no Linux OS that I know of which is 256 MB. Most are about 600+ MB.

---

### Post by AnneL on 2013-05-01
Thank you for the links! Very informative article!

---

### Post by Cheesemill on 2013-05-01
One thing to look out for is that your old laptop might not even support booting from a USB stick. You may have to find a machine you can burn a CD from to do the installation.

---

### Post by AnneL on 2013-05-01
I run Unetbooting from my netbook but I dont want it changing anything on my netbook. How can I prevent it from installing a bootloader? Please! I don't see any chance to avoid installing bootloader on my netbook!.. Why does it want to reboot my netbook after copying all files to the flash key?

I have chosen DamnSmallLinux which require only 128MB RAM.

---

### Post by AnneL on 2013-05-01
It seems it can boot from usb --I can see this option when I press F12 when powering.

---

### Post by ajgreeny on 2013-05-01
I was just going to suggest DSL or puppy as alternative OSs, but see you have already got DSL.  Puppy is also worth a look, I suggest.

Good luck!

---

### Post by AnneL on 2013-05-01
> **ajgreeny said:**
> I was just going to suggest DSL or puppy as alternative OSs, but see you have already got DSL.  Puppy is also worth a look, I suggest.

Good luck!
Thank you!

---

### Post by Jason Kuzhively on 2013-05-01
You can't 'avoid' installing bootloader. Bootloader is a piece of code that runs before any operating system is running. Bootloader is used to boot the operating system so don't worry, it isn't gonna do anything harmful to your Netbook. I think you should edit your first post and include the specs of your Netbook...

---

### Post by Jason Kuzhively on 2013-05-01
One more thing: Can you go to your BIOS Settings by pressing the appropriate button, then go to the "Boot" tab and let me know what are the options in there? If you have any problems while installing DSL from your USB then let me know, I've been in your position so I can help you :)

---

