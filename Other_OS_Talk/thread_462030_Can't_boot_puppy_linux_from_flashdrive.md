---
title: "Can't boot puppy linux from flashdrive"
date: 2007-06-02
forum: Other OS Talk
---

### Post by Dark-Ace on 2007-06-02
I got it installed and everything but i use dell and when i go and select USB device as my boot device it says "Selected USB device not available. press F1 to retry,F2 to run setup utility" now i'm not really sure if its all in my usb but i have a Dell E310 with 2 usb in the front and 3 in back.

---

### Post by elfstone214 on 2007-06-02
> **Dark-Ace said:**
> I got it installed and everything but i use dell and when i go and select USB device as my boot device it says "Selected USB device not available. press F1 to retry,F2 to run setup utility" now i'm not really sure if its all in my usb but i have a Dell E310 with 2 usb in the front and 3 in back.

It may be trying to access the wrong usb device, try removing the non-OS usb. Also when I tried booting puppy linux for the first time it also would not recognize my usb drive so I read some where they recommend deleting the whole partition in the usb drive, creating a new FAT16, reformatting it, and then you need to select flag it as "boot". Proceed to install puppy linux in it and try rebooting again.

---

### Post by Dark-Ace on 2007-06-02
Well there really aren't any others on besides mouse,keyboard, and cam so i don't know why it would access that and the usb device boot selection only pops up when i have my flashdrive.

---

### Post by elfstone214 on 2007-06-02
> **Dark-Ace said:**
> Well there really aren't any others on besides mouse,keyboard, and cam so i don't know why it would access that and the usb device boot selection only pops up when i have my flashdrive.

oh sorry, I thought you said you had 2 usb flash drives connected.

Try reinstalling it but first do the partition/reformat using gparted during the installation process as I wrote above and make sure you flag the partition as "boot" using "manage flags" by right clicking on the partition. It was one of the recommended things to do but unfortunately I don't remember where I read it. I did it and it is booting just fine here.

---

### Post by toomuchcomputertime on 2008-06-03
I am also having problems booting from my 2 G flash drive. I am using wakeupup2, but it is not seeing my SCSI flash drive. Can anyone tell me how to fix this? Thanks.

---

### Post by cardinals_fan on 2008-06-03
I have tried three operating systems on two flash drives on four computers in all twenty-four possible combinations, and have NEVER succeeded in booting from a flash drive.  Go figure.

---

### Post by JESSU on 2008-06-03
I have tried using pendrive linux and it didnt work for me. I followed all the steps from some site but after the spash there was no GUI.

Has anyone sussfully booted linux from a pendrive?

---

### Post by toomuchcomputertime on 2008-06-03
I have booted puppy linux on my flash drive on our powerspec, but nothing else. I have tried several dells, hp, gateway...
Thanks.

---

### Post by melrom on 2008-06-04
I use a dell XPS, and I've never had a problem booting Puppy from a flashdrive. 

I referenced this website: [http://www.pendrivelinux.com/2006/03/25/puppy-linux-on-usb/](http://www.pendrivelinux.com/2006/03/25/puppy-linux-on-usb/)

Which it sounds like you did too, so I'm not sure. You tried different USB ports?

---

### Post by toomuchcomputertime on 2009-01-28
I just found this thread again, I use puppy regularly on pendrives, and it works great. [Here]("http://puppylinux.com/flash-puppy.htm") is  link to a page that explains it quite clearly. I use MiPup2 with a wakepup2 floppy disk (if needed). To use a different flash drive, just copy/move the files over.

---

### Post by pmicheal on 2009-01-30
> **elfstone214 said:**
> It may be trying to access the wrong usb device, try removing the non-OS usb. Also when I tried booting puppy linux for the first time it also would not recognize my usb drive so I read some where they recommend deleting the whole partition in the usb drive, creating a new FAT16, reformatting it, and then you need to select flag it as "boot". Proceed to install puppy linux in it and try rebooting again.


I've tried your Idea but I'm not successful. anybody knows the best solution? I've 2.0GB Kingston USB 2.0 Flash drive.

[Linux Archive]("http://www.linux-archive.org/")

---

### Post by smartboyathome on 2009-01-30
> **pmicheal said:**
> I've tried your Idea but I'm not successful. anybody knows the best solution? I've 2.0GB Kingston USB 2.0 Flash drive.

I am running puppy fine on my DataStick Sport. I did install an alternate MBR on there though (I can't remember which distro told me to do it, sorry). It said that some USB drives require that alternate MBR to be installed in order to work.

---

### Post by Plumtreed on 2009-02-01
I used Puppy's 'install'>'Universal Installer' in 4.1.2 on a Sansdisk 2GB Cruzer and it worked OK. I had no trouble changing the BIOS order on a fairly recent machine, however.

Google for 'UNetbootin' it may help you boot to a flash drive.

---

