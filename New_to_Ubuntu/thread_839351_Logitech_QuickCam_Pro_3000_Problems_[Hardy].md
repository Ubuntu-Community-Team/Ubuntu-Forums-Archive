---
title: "Logitech QuickCam Pro 3000 Problems [Hardy]"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by abhiroopb on 2008-06-24
(In Gutsy) I was using a random camera which worked out of the box, which was great. However, the quality was terrible. But it worked at least. I tried messing around with the PWC drivers and UVC tools ([http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)) for the logitech I had but nothing seemed to work. I upgraded to Hardy and thought I would try out the Logitech again. I plugged it in and lo and behold it worked with skype. However, I unplugged it plugged it back in and it just stopped working! Sometimes it shows up when I do **lsusb** sometimes it doesn't:

```

$ lsusb
Bus 001 Device 007: ID 046d:08b0 Logitech, Inc. QuickCam 3000 Pro [pwc]

```

Any suggestions?

Thanks

---

### Post by abhiroopb on 2008-06-25
Bump!

---

### Post by cariboo on 2008-06-25
I've ot a Logitech Quickcam Messanger, I've been looking for a driver for it. All links to the driver for this webcam, even on Logitech's web site lead to a 404 error. It seems the only place you can get a driver for this device has diappeared. If anyone has a copy of the spca5xx driver, I would really appreciate if they could post it in this forum

---

### Post by markbuntu on 2008-06-25
I've got a Logitech Quickcam Communicate STX and figured out needed to get V4l instead of V4l2 to get it to work. That's all I did, installed V4l with Synaptic plugged it back in and it worked. V4l2 did not find my camera in Ekiga but V4l did.

---

### Post by rburkartjo on 2008-06-26
abh, i have the quickcam pro 9000 never could get it to work in gutsy. but in hardy i downloaded the program "cheese" from applications/add remove and works okay. hopefully if you install and open cheese it should recognize your webcam/cheesemaker

---

### Post by abhiroopb on 2008-06-27
Thanks a lot for the suggestions, I will try them out once I have the camera again (I packed it away for the holidays, and using the bad one again) but if there are any more ideas, do let me know!

---

