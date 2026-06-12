---
title: "Problems installing"
date: 2016-10-28
forum: New to Ubuntu
---

### Post by yosabbylo on 2016-10-28
I have installed various distros of Linux on several machines before, but this time, I'm having a lot of trouble. I have an old Dell Latitude D620 that i got from my boss and first thing i did after I got it was wipe the drive with DBAN. Now , there is nothing on it. I have an iso of Ubuntu burned onto a disk and set the Bios of the machine to boot from the cd/dvd drive ONLY. Now when i boot the machine, i hear the disc drive fire up like its trying to do something only for it beep a couple seconds later and say there is nothing to boot from.
I had the Bios perform a check on itself to make sure that everything is working properly, but I haven't been able to get anything to work yet. 

I must say that this was the second route i decided to take. First thing I did was try and boot from a USB with the image on it, and that didn't work either. I was quick to abandon this method because it is one that im not really familiar with. I don't know if i have to prepare it or anything to be used as a boot device.

This is the first time I have ever had a problem installing Linux Operating systems on a machine like this. Can anyone help me out please!!?? Thanks

---

### Post by howefield on 2016-10-29
It is unlikely to be a bad image download or burn but it as you appear to be having issues booting from the DVD, it is probably the first thing to rule out.

Have you checksummed the download and burned image ?

---

### Post by HermanAB on 2016-10-29
The same image that you burned to a DVD will also work on a USB thingy.  For the last few years, Ubuntu images are dual mode and will boot from either.  Simply copy it byte for byte with dd or rawrite to the USB device.  The days of needing unetbootin and other conversion programs are long gone.

---

