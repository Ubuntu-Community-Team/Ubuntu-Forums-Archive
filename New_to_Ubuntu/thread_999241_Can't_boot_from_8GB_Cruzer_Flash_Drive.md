---
title: "Can't boot from 8GB Cruzer Flash Drive"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by pet_the_ibex on 2008-12-01
Hi,

I have Ubuntu 8.10 on my flash drive and should be able to boot it and run it like it's on my hard drive, but there is no option to boot from it at my bios boot screen. Here are the four boot devices:

1.USB Memory (nothing is detected)
2.DVD drive
3.HDD
4.FDD

Is there any way I can get more boot options? I have a Toshiba A-105 S4034 laptop, and am using the factory settings, and haven't updated my BIOS. What could possibly make my PC read the flash drive?

Thank you, 
-Lee

---

### Post by bobnutfield on 2008-12-01
On most Toshiba laptops that are newer than 3-5 years, you can press F12 at the very first screen when the laptop is powered on.  Then, a new screen appears giving you various boot device options.

---

### Post by pet_the_ibex on 2008-12-01
Hello bobnutfield,

Thanks for telling me that. The problem is, I do press f12 and get to the boot screen. Those four items I displayed are the only options I have. Even USB memory isn't reading anything.

---

### Post by bobnutfield on 2008-12-01
> **pet_the_ibex said:**
> Hello bobnutfield,

Thanks for telling me that. The problem is, I do press f12 and get to the boot screen. Those four items I displayed are the only options I have. Even USB memory isn't reading anything.

If you are getting that screen, then the USB stick should boot if it is properly installed.  What do you get when you choose the USB memory to boot from?  What error do you get?

---

### Post by pet_the_ibex on 2008-12-01
I get a flashing cursor, then my computer loads Windows XP. The boot program completely ignores the flash drive. 

Sorry for not clarifying. :(

---

### Post by halitech on 2008-12-01
did you just copy the ISO file over to the flash drive or how did you put ubuntu on it?

---

### Post by pet_the_ibex on 2008-12-01
I installed it with the utility found in the System folder(?), and it asked me how much file space I wanted to allocate to it. I gave it about 2.5 gigs of space to work with, and it set out working, copying everything I needed from my Live CD to my memory stick.

If I have "USB memory" as a boot option, does that mean I can even boot from an external USB hard drive?

---

### Post by bobnutfield on 2008-12-01
I think halitech has your answer.  If you just installed to the USB disk, you would have to have a boot manager also installed.  If you did not install Grub to the USB disk when you installed, then this is the action you would get.

---

### Post by pet_the_ibex on 2008-12-01
Halitech and bobnutfield, thanks a lot! I will try again, and install grub. I will be back shortly.

---

### Post by bobnutfield on 2008-12-01
> 
If I have "USB memory" as a boot option, does that mean I can even boot from an external USB hard drive?

Yes, that means you are booting from the USB port and if anything attached there is bootable, it will boot there.

---

### Post by pet_the_ibex on 2008-12-01
Thank you. 

I have a problem, still. (This is pretty neat, messing with computers. :) )
I go to System->Administration->Create a USB startup disk and run that program. I didn't see a GRUB selection option.

---

### Post by bobnutfield on 2008-12-01
Sorry for that suggestion, as I made it assuming you were installing the system from the CD as you would to any other hard drive.  If you are using the USB install from the System menu, it does not have a separate Grub option for that install.

---

### Post by pet_the_ibex on 2008-12-01
Thanks. Now I am concerned. Where would I put GRUB if I installed from system menu while running live cd. Or should I use another method to install to my USB stick?

---

### Post by halitech on 2008-12-01
here is some interesting information

[http://tombuntu.com/index.php/2008/11/12/create-a-bootable-usb-drive-the-easy-way-in-ubuntu-810/](http://tombuntu.com/index.php/2008/11/12/create-a-bootable-usb-drive-the-easy-way-in-ubuntu-810/)

from what I'm reading, you need to have either the cd or the ISO on your hard drive.

---

### Post by pet_the_ibex on 2008-12-01
> **halitech said:**
> here is some interesting information

[http://tombuntu.com/index.php/2008/11/12/create-a-bootable-usb-drive-the-easy-way-in-ubuntu-810/](http://tombuntu.com/index.php/2008/11/12/create-a-bootable-usb-drive-the-easy-way-in-ubuntu-810/)

from what I'm reading, you need to have either the cd or the ISO on your hard drive.

Yes, this is true. I have the CD, and created a startup disk, yet when I boot the flash drive, all that displays on the screen is a blinking cursor, followed by the windows startup screen. I have no idea what I'm doing wrong. 

Do you think it has anything to do with my DVD drive? Should I use a CD drive to make the disk? I remember I couldn't get Ubuntu running by burning an ISO file on my DVD burner-- I had to use my mom's CD drive before it would work.

---

### Post by halitech on 2008-12-01
if you were having trouble burning the ISO originally then yes, I would try another drive on another machine as it could be drive related.

---

### Post by pet_the_ibex on 2008-12-01
Thanks again to both of you! I have decided it's a DVD drive problem. Should I buy a cheap CD/RW drive to plug in to my USB port so I can mess around with Linux, or would that be unnecessary?

---

### Post by halitech on 2008-12-01
if you feel up to it, an internal drive would be cheaper and faster. and you don't need a cd drive but it does make life more fun :)

---

### Post by pet_the_ibex on 2008-12-01
Yes, CD drives can come in handy. :)

Well, what's bad is this: the only drive that works is, in fact, connected to a computer with only 256 megabytes of RAM in it. So I can't get into the live environment. Man, I don't know what to do short of building a PC or upgrading my mom's RAM. Oh well. It's time to read that CompTIA A+ 2006 book. :)

Thanks again, to both of you. You have been extremely helpful.

---

### Post by halitech on 2008-12-01
if you were local I'd give you 2 or 3 out of the stock I have here for free but shipping would probably cost more then buying a new one locally.

---

### Post by pet_the_ibex on 2008-12-01
Thanks for the offer!

---

