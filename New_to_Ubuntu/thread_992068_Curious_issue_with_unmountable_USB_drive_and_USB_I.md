---
title: "Curious issue with unmountable USB drive and USB Image Writer"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by spaceholiday on 2008-11-24
Firstly, I've searched the forums and not found my specific issue, so here I am!  Hullo!
Ok, I've got an Aspire One and am trying to install the Ubuntu Netbook Remix on it from a fresh 8.04 install.  Booting from a USB key is no problem (hence the fresh install), but when I put a USB key in the system after boot, I get an error message:
[IMG]http://img377.imageshack.us/img377/9575/screenshotaz7.png[/IMG]

I found this out when opening USB Image Writer, which the [UNR wiki]("https://wiki.ubuntu.com/UNR#Using%20Usb%20Imagewriter") suggests for UNR installation.  I opened the program and it prompted me to insert a device to which to write.  I did so and received the error message pictured above.  I closed out of Image Writer, tried putting in a USB key, and got the same message.  When I go to Places, the key shows up, but when I try to mount it I get the same message.

So, out of curiosity, I left the key plugged in and opened Image Writer.  It worked!  It found the device and I was able to write the UNR image to it successfully:
[IMG]http://img147.imageshack.us/img147/9442/screenshot1re9.png[/IMG] 

Odd, but okay.  So my questions, then:
Why did that work, and more importantly,
How can I get my netbook to auto-mount USB drives in the future?  It has no problem when I connect a USB mouse; I haven't tried a printer or any other peripheral hardware yet.

Thanks in advance.

---

### Post by spaceholiday on 2008-11-24
bumpity-bump...

---

### Post by approaching on 2009-07-07
I am having a similar issue, but with a few differences. The write failed entirely, and now i can't mount the flash drive. I am fairly certain that it is showing up as a card reader because the drive isn't reporting any space. Like, it is using up the usb, but the capacity is 0. It has also said something to the effect that i should insert a volume into it.

But more problematic than that is that gParted isn't even recognizing it to try and format it so it is usable again. Windows and Mac are having similar issues reading the card, so it isn't system specific. Something bad happened to the drive when it was being written to by ImageWriter.

---

### Post by LewRockwell on 2009-07-07
> **spaceholiday said:**
> bumpity-bump...

I just put Ubuntu 9.04 Jaunty on an Acer Aspire One AOA-150-1864

Right now I've got it triple=booting with Windows XP Professional SP3 and also Puppy Linux 4.2.1 and I've got five more logical partitions for five more *nix distros

The Ubuntu and Puppy were both loaded using a crappy old cd-rom drive out of a desktop and one of these([http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062](http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062))

*****(10-10-09:Note that recent product reports seem to indicate that there is an electrical problem when using this device with SATA drives that may cause damage/destruction to your equipment...we are in the process of an analysis and investigation into this issue and so far we believe a design flaw does indeed exist)***(10-11-09:We have determined that a design defect DOES EXIST and an extender should be used between the power connector and the adapter so you can cut the red wire to stop the 5 volt connection that is damaging/destroying various components INCLUDING MOTHERBOARDS...An advisement has been sent to CoolMaxUSA but feel free to remind them!)*****

All work wonderfully

---

