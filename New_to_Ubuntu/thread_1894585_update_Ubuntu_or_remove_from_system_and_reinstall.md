---
title: "update Ubuntu or remove from system and reinstall"
date: 2011-12-12
forum: New to Ubuntu
---

### Post by shultzbaby on 2011-12-12
I just inherited  a computer that has a dual boot option for Ubuntu. However my version is outdated and cannot be updated automatically. After trying and failing to manually update, and since I have no blank CDs, my question is this.
Would it be a viable option to use windows to remove Ubuntu completely, restore the bootloader, and then download  te latest version of Ubuntu? I have the iso file downloaded but cant figure out any way to flash it without burning a cd. Please help! I will follow up this post with more detailed technical info in a bit.

---

### Post by RealityMaster on 2011-12-12
perhaps this will help

[http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html)

---

### Post by shultzbaby on 2011-12-13
well i just trashed my brand new computer thanks to this guide:
[http://www.makeuseof.com/tag/nongeeks-guide-safely-uninstall-ubuntu-dualbooting-machine/](http://www.makeuseof.com/tag/nongeeks-guide-safely-uninstall-ubuntu-dualbooting-machine/)
cant boot anything now.
and since im not the original owner i dont have the windows discs or keys that came with it.
i am livid now.
so, now that my computer is f'ed, can anyone point me to a guide to formatting my disks and installing ubuntu so i have an OS to use on my comp? im so pissed, i am a tech savvy person but this is really driving me nuts. has anyone ever tried using a phone's sd card to install ubuntu onto a computer? or i guess i can find a way to make a cd, but idk id rather not wait days until i have an opportunity. man i feel like a noob today.

---

### Post by Bucky Ball on 2011-12-13
If you have another machine, download the ISO, make a CD, boot from it, choose to manually install when you get to the partitioning section and make your new partitions there. If you want Windows on there, install that first on a partition big enough for it. 

You had no problems in the first actually. Windows can't remove Ubuntu (EXT*) partitions as it has no idea what they are. If you had Windows on a partition and the rest of the drive usable, that is what you want. You can partition (or delete the existing Ubuntu partitions) with the Ubuntu install CD. Oops. Live and learn, consider it like that and welcome to the forums. ;)

---

### Post by bodhi.zazen on 2011-12-13
> **shultzbaby said:**
> I just inherited  a computer that has a dual boot option for Ubuntu. However my version is outdated and cannot be updated automatically. After trying and failing to manually update, and since I have no blank CDs, my question is this.
Would it be a viable option to use windows to remove Ubuntu completely, restore the bootloader, and then download  te latest version of Ubuntu? I have the iso file downloaded but cant figure out any way to flash it without burning a cd. Please help! I will follow up this post with more detailed technical info in a bit.

You can always use the desktop .iso to make a bootable, live flash drive.

See unetbootin

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

unetbootin runs in windows and linux.

---

### Post by shultzbaby on 2011-12-13
When installing Ubuntu from a CD or USB, will it give me the option to format my drive? And if I do so, will it also delete device drivers ie my monitor?

---

### Post by cortman on 2011-12-13
> **shultzbaby said:**
> When installing Ubuntu from a CD or USB, will it give me the option to format my drive? And if I do so, will it also delete device drivers ie my monitor?

Yes to both, but Ubuntu comes bundled with drivers for most peripherals.

---

### Post by shultzbaby on 2011-12-13
Good. Looks like thats ehat ill be doing after work today.

---

### Post by shultzbaby on 2011-12-13
Another quick question, will it also delete the USB drivers? Wouldnt this make the USB boot useless if something goes wrong?

---

### Post by migs73 on 2011-12-13
No it'll be fine, you can run a USB boot even without a hard drive.
I think there are rudimentary drivers for the USB in your BIOS, which is what is used in this case.

---

### Post by Docaltmed on 2011-12-13
The BIOS will manage the communication with the USB ports to the degree that is necessary to get the Ubuntu installation drive up and running.

The only problem may occur if your BIOS is not configured to recognize the USB flash drive to be one of the boot drives. Usually the computer checks down the line until it finds a drive that can tell it what to do, usually HDD > Optical > USB. That's not always the case, though. So if you are finding that your USB flash drive is not getting recognized, you need to hit a key during the initial boot sequence to get you into the BIOS management, from which you can designate the boot drive of choice.

The key you hit on startup can vary a lot. Some systems it's F2, some F12, some Esc; usually there's a little notice on the bottom of your screen that flashes on for a brief second or two which tells you how to get to your BIOS. I usually have to do 2-3 aborted restarts before I get it right.

---

### Post by cortman on 2011-12-13
> **shultzbaby said:**
> Another quick question, will it also delete the USB drivers? Wouldnt this make the USB boot useless if something goes wrong?

The basic IO "drivers" are stored in the BIOS, which is in memory chips soldered to the motherboard, and will remain no matter what you do to the hard disks.

---

### Post by shultzbaby on 2011-12-13
one more question. i dont have an actual usb stick, but i do have an sd card reader that connects via usb. would this work as well?

---

### Post by Dlambert on 2011-12-13
It should as long as you set up the SD card using UNETBOOTIN. :)

---

### Post by shultzbaby on 2011-12-13
Well guys I ended up just Googling "install Ubuntu via USB" and followed the official instructions, everything worked without a hitch. UI was super sloooow so I updated the nvidia drivers and now my system is rock solid. Thank you so much for the prompt feedback. I have a desktop again yay!!!! :D

---

