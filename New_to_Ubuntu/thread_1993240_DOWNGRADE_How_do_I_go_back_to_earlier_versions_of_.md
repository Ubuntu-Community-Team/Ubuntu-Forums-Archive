---
title: "DOWNGRADE /How do I go back to earlier versions of Ubuntu?"
date: 2012-06-01
forum: New to Ubuntu
---

### Post by kesbetik on 2012-06-01
Hi, 

Since I upgraded to ubuntu 12 my system is so slow that I want to go back to an earlier version of ubuntu. However, when I try to boot from cd it does not boot from it, when I manually select the install from the cd the action is blocked by the present system. USB boot does not work either. When I choose 'other' source then default it does not update, stays the same 12.04 iso image as default to create the usb boot up. But even that wont boot from the usb device. (since an ubuntu is already present, and the recommended action of removing it is not possible or I do not know how 'delete' does not work for that)

Please advise. Thank you.

---

### Post by Paqman on 2012-06-01
> **kesbetik said:**
> However, when I try to boot from cd it does not boot from it

Does it just boot straight to your system on the hard drive? You might need to change your boot priority in BIOS to boot from the optical drive first.

---

### Post by deadflowr on 2012-06-01
This sounds like a bad iso image, as for when you boot from a live Cd/usb the current system on the hard drive is never mounted. the hard drive only gets mounted when you click on the install now button in the installation setup. Or manually, like when running a livecd desktop and you open nautilus and click on the device for the hard drive.

---

### Post by inashdeen on 2012-06-01
I agree with paqman. I have similar problem with my dell d420 . it seems that ubuntu 12.04 set to boot right from disk as first priority after installation.

---

### Post by Shadius on 2012-06-01
> **kesbetik said:**
> Hi, 

Since I upgraded to ubuntu 12 my system is so slow that I want to go back to an earlier version of ubuntu. However, when I try to boot from cd it does not boot from it, when I manually select the install from the cd the action is blocked by the present system. USB boot does not work either. When I choose 'other' source then default it does not update, stays the same 12.04 iso image as default to create the usb boot up. But even that wont boot from the usb device. (since an ubuntu is already present, and the recommended action of removing it is not possible or I do not know how 'delete' does not work for that)

Please advise. Thank you.

If your computer is slow with 12.04, you should try other distros like Lubuntu for example. My computer was slow when I installed 12.04 because of the Unity interface so I installed Gnome Tweak Tool and am now using Gnome Classic (No Effects). Worth a try, I supposed.

---

