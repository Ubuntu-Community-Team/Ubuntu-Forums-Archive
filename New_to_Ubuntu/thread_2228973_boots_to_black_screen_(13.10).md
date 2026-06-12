---
title: "boots to black screen (13.10)"
date: 2014-06-10
forum: New to Ubuntu
---

### Post by tobi4 on 2014-06-10
I'm working off a Dell desktop that someone else owned before me. They claim it worked completely fine for them, but when I boot the computer it says "kubuntu" and then goes to a completely black screen (no mouse or typing cursor). You can type, but normal linux commands do nothing. The only things I can make happen are restarting (control-alt-delete) and making a login prompt appear, but I don't know the username or password.

I've tried reinstalling the OS from a flash drive (I don't have a blank CD or a CD drive to write with on my laptop, a mac). The files show up fine on my computer (I used unetbootin) but when I try to boot the Dell from it (using the F12 quick boot-change menu), it says the drive failed. When I change the BIOS to boot from the flash drive before the hard drive, it says "no bootable devices."

I'm really not sure what to do from here....

---

### Post by oldrocker99 on 2014-06-12
On my laptop, unetbootin-created USB sticks have given me the same error. Try Ubuntu's own Startup Disk Creator, if you can.

---

### Post by kc1di on 2014-06-12
try doing the download and burn it to your usb stick again with new download.  format the stick first.

---

### Post by tobi4 on 2014-06-12
Called Dell and it sounds like it's a hardware problem. Thanks guys!

---

### Post by kc1di on 2014-06-13
Hope you can get is sorted -good Luck.

---

### Post by mörgæs on 2014-06-13
I'm not convinced that there's a hardware problem.

If you have Nvidia graphics you could try adding the **nomodeset** boot option. Sounds more or less like the classical Nvidia problem.

Sometimes a new BIOS is necessary in order to boot from USB. Which Dell are we dealing with?

13.10 is soon running out of support so better to try 14.04 from a CD (Lubuntu) or DVD (other Buntus).

---

### Post by squakie on 2014-06-13
+1.  It definetly sounds like a graphics driver problem, particularly if you could get to a text-mode login (terminal window).   i would try nomodeset as well, and there are other boot-time opions to try as well.

---

