---
title: "[SOLVED] Ubuntu live CD"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by EvanRogers on 2008-10-05
OK so i messed up my computer while i was messing with the partitions on my hard drive, so now im on my mothers computer and i need to know:

If i burn the ubuntu live cd to a cd could i boot my computer with it and install ubuntu? (i have error 15 on GRUB at startup)

If the answer is no then what could i do? i already tried supergrub but i couldn't get it to work at all.

If the answer is yes then what kind of burnable CD should i get, my mom is going to pick 1 up for me and i told her to get me a 800mb Data cd-rw disk. Is that ok?

Please take you're time to answer my questions as i need to get my computer back up and running with Ubuntu as my OS because it is awesome.

---

### Post by bobnutfield on 2008-10-05
Yes you can.  You can also install to your hard drive via the live cd.  Just make sure when you burn the CD you burn it as an .iso image, not as a file.

---

### Post by EvanRogers on 2008-10-05
> **bobnutfield said:**
> Yes you can.  You can also install to your hard drive via the live cd.  Just make sure when you burn the CD you burn it as an .iso image, not as a file.

So yes i can burn it to a 800mb data cd-rw? yes i can boot my computer from the cd even tho i can't get past the bootloader (grub error 15)?

So to burn it as a iso image i have infra recorder and i have the .iso file saved to my desktop is that ok?

---

### Post by Huji on 2008-10-05
You can, but don't be 100% sure that you can restore all your partitions using only the Ubunutu live CD. If you have damaged your partition table, you may have a hard time to restore the data in the affected partitions.

---

### Post by EvanRogers on 2008-10-05
> **Huji said:**
> You can, but don't be 100% sure that you can restore all your partitions using only the Ubunutu live CD. If you have damaged your partition table, you may have a hard time to restore the data in the affected partitions.

I am fine with that, will it just do a clean install of ONLY Ubuntu? because i had it dual booted with win xp but i wanted it to be ubuntu only because i never used xp anymore. I just want a clean new install of ubuntu.

---

### Post by Therion on 2008-10-05
Make sure you do a slow burn of the CD.

But yes, you can select "Install - Use Entire Disc" from the LiveCD and the Ubuntu install will then automatically reformat and repartition the entire hard drive leaving you with Ubuntu as your only operating system.

---

### Post by bobnutfield on 2008-10-05
> **EvanRogers said:**
> So yes i can burn it to a 800mb data cd-rw? yes i can boot my computer from the cd even tho i can't get past the bootloader (grub error 15)?

So to burn it as a iso image i have infra recorder and i have the .iso file saved to my desktop is that ok?

Yes, the Grub error only affects your internal drive, not the live cd.  The live cd will not be affected by it as it will not even read it.  Yes, the live cd is just under 700mb, so an 800mb cd is fine.

---

### Post by EvanRogers on 2008-10-05
> **bobnutfield said:**
> Yes, the Grub error only affects your internal drive, not the live cd.  The live cd will not be affected by it as it will not even read it.  Yes, the live cd is just under 700mb, so an 800mb cd is fine.

OK, so now that i know all of that, what do i have to do to get the computer to boot from the cd? because like i said all i get is GRUB

Error 15...Please Wait

then it hangs there.

---

### Post by bobnutfield on 2008-10-05
You will need to go to your BIOS and select the CD/DVD drive as the first boot drive.  Some systems allow you to press F12 at POST time to boot from the CD drive, but if not just select it in your BIOS.

---

### Post by timjohn7 on 2008-10-05
> **EvanRogers said:**
> OK, so now that i know all of that, what do i have to do to get the computer to boot from the cd? because like i said all i get is GRUB

Error 15...Please Wait

then it hangs there.

Put the live CD into your CD Drive
Restart your computer 
At some time during the initial startup process you should get a message re BIOS Setup and Boot Options (depending on your BIOS).  On my Fujitsu Siemens Laptop I push F12 for boot options.
Select your CD drive
You should get the Ubuntu Splash Screen & Installation menu.
Select Run or Install Ubuntu and follow the prompts
Welcome to Ubuntu.

---

### Post by taqkavar on 2008-10-05
when the computer starts go to your BIOS setup ( usually it says what key to press to enter the setup etc: del,F12 , F1 and ... ) then change your boot order and have CDROM as the first device to boot off of. 

Then proceed with the installation and when asked about partitioning choose Entire Disk, Remember that you will loose all your data if you do so. so if you need anything, copy them do an external drive/USB key or something.

---

### Post by EvanRogers on 2008-10-05
Thanks guys you answered all my questions and once i get my burnable cd i'll be back on ubuntu.

---

