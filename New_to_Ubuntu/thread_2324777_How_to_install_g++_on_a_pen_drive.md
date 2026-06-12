---
title: "How to install g++ on a pen drive"
date: 2016-05-16
forum: New to Ubuntu
---

### Post by Diogo_Gomes on 2016-05-16
I am starting to program in c++, and everything's all right at home, but in my school, where PC's also run ubuntu, they don't have g++ installed, and I can't do anything about it because I'm obviously not a admin. So I though there should be a way to install g++ and all the libs in a usb drive, and then just compile it from there, and do everything in that usb drive. Any ideas?

Just some more info: I already tried creating a live CD, but the PC's are really slow, and the motherboard has a well known issue, where you can't change the boot order. I also tried using online IDE's, but all the ones I've tried are crappy, and none of them allowed you to save your files (unless it was a paid service). Lastly, I would prefer if g++ could come in a 32-bit version, and my PC at home is running 64-bit...

---

### Post by oldrocker99 on 2016-05-16
You **might** ask the school admin to install g++ on the school computers; it's certainly something that programming classes need. I know that Unetbootin allows you to specify how much extra space on the thumb drive to be used for file storage, but only for Ubuntu.

---

### Post by Geoffrey_Arndt on 2016-05-16
Also - newest tool to create USB Flash-Stick bootable OS . . . [http://www.omgubuntu.co.uk/2016/05/etcher-usb-image-burner-tool-linux-open-source](http://www.omgubuntu.co.uk/2016/05/etcher-usb-image-burner-tool-linux-open-source) 

So, the best way to do this is to do an actual install on a 16 GiB or larger USB (v3 if available), or best solution yet is to get a Sansa USB v3 SSD  . . so, you have two external USB devices plugged in, the first has the Live iso image, and the second has the actual install with the bootloader file.   Of course, you still have the issue of is your "host PC" capable of booting from external USB port?   Must be able to change the firmware to allow for boot order update AND to recognize external usb hard drive (as that is what the SSD device may be recognized as).

But I agree with Oddrocker99 that best bet is to make a "sales pitch" to the school admin . . . seems like others would have this issue also???

PS:   the only time when 2 devices are concurrently plugged in is during the install process.  Thereafter it's just the device with the actual install (NOT a live usb by-the-way . . a full install'd device).

[https://www.sandisk.com/home/ssd/extreme-500-ssd](https://www.sandisk.com/home/ssd/extreme-500-ssd)

---

### Post by Diogo_Gomes on 2016-05-16
Regarding the sugestion of asking the school admins, I'm afraid that wouldn't work... It's an high school with no programming classes, and the IT department is nothing special... I should be the only one with that problem, so, they just won't do it (trust me, that's just how my school works).
As for the second option (creating a live usb) I've tried that, but when I went testing it, I couldn't change the boot order, so I looked it up, and apparently it's a known issue with that motherboard/BIOS, where you can't change the boot order. Also, the PCs are really slow booting up and shutting down, so the live usb would be a huge waste of time...

---

### Post by sudodus on 2016-05-16
In general, I would also suggest installing a full Ubuntu system into a fast USB 3 pendrive or SSD.

But here, well, I would think it is easier to make the school computer admin install g++ into their own system, than to help you boot the school computers with your own systems. They are probably happy, that it is hard (impossible?) to boot from USB.

---

