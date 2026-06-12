---
title: "Ubuntu on USB not being detected"
date: 2016-10-30
forum: New to Ubuntu
---

### Post by desbrow on 2016-10-30
Hey guys,

I've looked through old threads but cant find exactly what I'm after. I've been trying for days now to boot Ubuntu from USB onto my ASUS S500c on windows 10 currently.

I quite enjoy spending time figuring all this out, but this is now driving me insane lol

I have gone into BIOS and have changed 'secure boot control' to disabled.

Then, 'launch CSM' to enabled, and 'launch PXE OpRom' to enabled as well.

This then adds my USB as 'mass storage device' to the boot list, which i then moved to the top of the list and saved it all and restarted with the USB plugged in.

I then get a message saying 'missing operating system'.

I downloaded the iso file onto usb and formatted with usb intaller, so I think that is ok, however, unless I did something wrong here and it is not recognising the file on the USB, apart from that, I dont know.

Update, I tried on another laptop and I have the same problem, so I am assuming it is a problem with how I downloaded the iso.


I hope someone can help, thanks.

---

### Post by yancek on 2016-10-30
Did you do an md5 checksum of the iso after downloading to verify it?

> I downloaded the iso file onto usb and formatted with usb intaller

Not sure about that.  Why did you download to the usb?  You should just download to your hardrive and use software to create a bootable usb.  Not sure what 'usb installer' is?  Some of the more common software used to create a bootable usb would be the dd command on a Linux system or something like unetbootin.  On windows, you would use something like pendrivelinus or rufus.

---

### Post by desbrow on 2016-10-30
ok thank you, I'll have a look at those points.

---

### Post by desbrow on 2016-10-30
Hey yancek, thank you for your help, it was pretty much exactly what you said. I used software to create a bootable usb, but that didn't include the md5 checksum. I followed your advice and used rufus and it worked. Finally. 

Thanks a million dude.

---

### Post by oldrocker99 on 2016-10-30
Since your problem has been solved, please mark your thread as [SOLVED].

---

