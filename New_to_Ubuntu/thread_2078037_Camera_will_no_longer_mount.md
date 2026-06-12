---
title: "Camera will no longer mount"
date: 2012-10-30
forum: New to Ubuntu
---

### Post by mph3 on 2012-10-30
I'm running 12.10.  My camera was successfully automounting, but I ran the following command and it no longer does:

**[COLOR="red"]sudo rmmod usb_storage[/COLOR]**

I ran the command based on a forum thread recommendation when trying to get past an error in the gphoto2 CLI.  I have not been able to find the way to undo the effect and go back to automounting.

I checked the automount settings in **[COLOR="Red"]dconf-editor[/COLOR]**, and they are set to true.  My USB flashdrive & my USB external harddrive both automount without any problem.

I also tried the following with no luck:

**[COLOR="red"]sudo modprobe usb_storage[/COLOR]**

Any help would be greatly appreciated.

---

### Post by shreepads on 2012-10-30
Can you point us to the forum thread that recommended this and do you connect the camera to the computer using a USB cable?

What new messages do you see in /var/log/syslog when you
a. Run sudo modprobe usb_storage
b. Connect the camera to the computer

---

### Post by HermanAB on 2012-10-30
It seems that you are doing rmmod and modprobe without actually knowing what you are doing.  Run lsmod to see whether the relevant module is loaded.  Then bear in mind that the mounting/unmounting of removable media is done by your desktop environment, so you may have to log out/in to get it to see the camera again.

---

### Post by NikTh on 2012-10-30
Hi ,

you have to see the messages in dmesg and see whats wrong. 

The rmmod and modprobe commands you ran , are valid only for one session. 
So Unplug your camera (I assume is a USB-WebCam) reboot your PC , login to Ubuntu and then attach the WebCam. 
Then open a terminal and give this command 
```
dmesg | tail -n 30
```this command will produce 30 lines in your terminal that are debugging lines. What kernel sees when you plug your WebCam. 

If you post them here , do not forget to put the results between these brackets **[noparse]```
the results here
```[/noparse]** so can be easy to read.

Thanks

---

### Post by mph3 on 2012-10-30
It appears the problem is with my camera itself.  I just discovered it had stopped functioning in general.  I tried a different camera, and it did mount.  Thank you for the quick response & suggestions.

---

