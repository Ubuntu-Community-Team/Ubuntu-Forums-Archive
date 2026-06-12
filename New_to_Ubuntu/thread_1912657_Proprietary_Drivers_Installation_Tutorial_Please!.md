---
title: "Proprietary Drivers Installation Tutorial Please!"
date: 2012-01-21
forum: New to Ubuntu
---

### Post by Cu Rua on 2012-01-21
I have:
hp 635 photosmart digital camera
hp 7660 photosmart printer
Drivers for both on a CD
and no idea how to install them. hp refuses to provide Linux drivers of any sort. My drivers came with the stuff, presumably Windows format. I've hit every .exe file and haven't gotten any of them to do anything, and I'm all out of ideas. This stuff did work before when I was using Windows '98, but then I had Linux eat Windows and don't wanna mess with a shell if I can help it. 
I've never installed anything on Linux w/o the synaptic package manager, and I don't know command line. I'd like a painstaking step-by-step all purpose tutorial on installing programs; barring that, I'd just like to know what to do to get my camera and printer back up and running. Thanks!

---

### Post by alphacrucis2 on 2012-01-21
> **Cu Rua said:**
> I have:
hp 635 photosmart digital camera
hp 7660 photosmart printer
Drivers for both on a CD
and no idea how to install them. hp refuses to provide Linux drivers of any sort. My drivers came with the stuff, presumably Windows format. I've hit every .exe file and haven't gotten any of them to do anything, and I'm all out of ideas. This stuff did work before when I was using Windows '98, but then I had Linux eat Windows and don't wanna mess with a shell if I can help it. 
I've never installed anything on Linux w/o the synaptic package manager, and I don't know command line. I'd like a painstaking step-by-step all purpose tutorial on installing programs; barring that, I'd just like to know what to do to get my camera and printer back up and running. Thanks!

You shouldn't need any proprietary drivers for most digital cameras. Just plug the camera in. Import photos from the camera via a photo organiser like shotwell. Shotwell uses gphoto2 to import from a camera. Here is the list of supported cameras:

[http://gphoto.org/proj/libgphoto2/support.php](http://gphoto.org/proj/libgphoto2/support.php)

There are a number of other photo organiser programs available if you don't like shotwell.

---

### Post by Fernhill Linux Project on 2012-01-21
If you do have any problems after connecting your printer & camera you can find and run 'additional drivers' from the dash. As alphacrucis2 said you should not have any problems with the camera, but some printers may not work as easily, although I have not had any problems with HP printers.

---

### Post by 3rdalbum on 2012-01-21
Plug in the camera and it should appear as an icon on the Launcher on the left side of the screen. You'll also be asked what you want to do with the camera you've just plugged in (whether you want to look at the photos, etc).

The printer driver is already included with the system. Go to the top-right corner of the screen - there is a menu there that looks like a cog and an on/off switch. Click that and go to Printers. Click on the Add button and then go to New Printer. After a few seconds your printer will appear on the left side of the window and then you just need to click it, then click the Next button. Give the printer a name and click Next again, and that's pretty much it.

Just a thought: You're using the latest Ubuntu, right? If you're using an older version of Ubuntu that's older than your printer, then it probably won't have the driver. Make sure you're using the latest Ubuntu, which is Ubuntu 11.10.

---

### Post by Cu Rua on 2012-01-23
Feeling kinda stupid now.... I had the camera set to act like a disk drive instead of an imaging device, and picked up a tip at that link of supported cameras to switch to PTP format, so I did that and voila, it works. Using Ubuntu 8.04, btw, or at least that's what Firefox keeps telling me. Thanks for the help!

---

### Post by mastablasta on 2012-01-23
if you are using 8.04 edition you should consider an upgrade (at least to 10.04 LTS). 8.04 reached end of life and does not receive updates anymore.
 
here is how you check the version in GUI and termnal:
[https://help.ubuntu.com/community/CheckingYourUbuntuVersion](https://help.ubuntu.com/community/CheckingYourUbuntuVersion)

---

### Post by Cu Rua on 2012-02-10
> **mastablasta said:**
> if you are using 8.04 edition you should consider an upgrade (at least to 10.04 LTS). 8.04 reached end of life and does not receive updates anymore.
 
here is how you check the version in GUI and termnal:
[https://help.ubuntu.com/community/CheckingYourUbuntuVersion](https://help.ubuntu.com/community/CheckingYourUbuntuVersion)

>< not your fault, but it made my computer melt down. a LOT. had to use absurdly indirect methods to format the hard drive and reinstall 8.04. looking at a new computer now...

---

