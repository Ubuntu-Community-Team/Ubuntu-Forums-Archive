---
title: "camera doesn't mount"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by tony.morse on 2008-08-11
When I plug in my new fujifilm f480 digital camera, ubuntu 7.10 says a digital camera has been detected and asks if I want to import the pictures, if I click on Import Photos it opens the dialog, loads camera drivers, and then says PTP invalid object handle. The camera also fails to appear in my computer.  My other camera (a fujifilm F650) works fine for importing pictures etc, but is broken and cant take pictures any more.

Does anyone know why my new camera doesn't mount properly and more importantly what I can do to fix this?  

I can't even swap cards as the F650 only uses XD cards while the F480 has a high speed SD card in it.  I tried putting the XD card in the f480 but got the same problem so it's definitely the f480 failing to mount rather than the card

I tried fdisk -l but there is no sign of the f480 camera, it only reads my hard drives.

Please help!!

---

### Post by dca on 2008-08-11
First try opening 'F-Spot' from the 'Applications -> Graphics' from main menu bar, see if the camera is listed in the drop-down...

---

### Post by dca on 2008-08-11
Wait a minute, I just re-read and you say you're running 7.10?  Hmmm, lemme' look into this 'cuz I don't know if F-Spot will get the photos...  Usually in 8.04, in the 'removable drives' settings a check-mark is placed by the camera and it's command is 'f-spot-import' or something there-abouts.  Perhaps removing that and unchecking box will allow for camera to be mounted as block device.  Also, you can see if your camera has a setting for PTP in its communications settings which should allow to be seen as a block device.

---

### Post by tony.morse on 2008-08-11
I tried F-Spot, it says no cameras detected, BTW the auto import is gthumb

---

### Post by alienexplorers on 2008-08-11
My camera a Vivatar 5050 is not listed by name, but is listed as a mass storage device under f-spot and gthumb.  Did you try to see if yours is listed like this.

---

### Post by tony.morse on 2008-08-12
Thankyou Thankyou Thankyou, F-spot can see my camera as a pdp device if I switch it on in play mode rather than just power on... very strange but that will do!!

---

