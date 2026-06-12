---
title: "Creating Windows 7 USB stick"
date: 2014-01-15
forum: New to Ubuntu
---

### Post by gavint522 on 2014-01-15
im trying to get windows 7 back on my computer i have the iso downloaded and everything even have blank dvd-rw's and a blank 8gb usb but i cant seem to get it to burn to a cd or install to the usb what do i do i need to run ubuntu 13.10 on the side but windows for everyday usage

---

### Post by grahammechanical on 2014-01-15
I am confused. What OS image are you trying to burn to either DVD or USB memory stick, is it Ubuntu 13.10 or Windows 7 or both.

I have burnt many Ubuntu ISO images to DVD disks and USB memory stick. I recently burnt a Windows 8 developer pre-view edition to DVD. My method is to use File Manager. Browse to the ISO image. Select it and right click the image and select Burn to Disk. It should be item 12 in the menu. Have the DVD disk or USB stick in the drive or port.

Regards.

---

### Post by gavint522 on 2014-01-15
it wont go past the starting to record part then it crashes

---

### Post by gavint522 on 2014-01-15
but im using ubuntu 13.10 and im trying to get windows 7 iso to a usb or dvd

---

### Post by Habitual on 2014-01-15
unetbootin in a repo near you.

---

### Post by gavint522 on 2014-01-15
i tried unetbootin also i dont know what im gonna do

---

### Post by Habitual on 2014-01-15
after inserting the drive open a terminal and type 
```
mount
``` and look for the /dev/xyz device that represents your USB drive.
then

In terminal try:
```
dd if=/path/to/image.iso of=/dev/USB
```

---

### Post by impliedconsent2 on 2014-01-15
> **Habitual said:**
> unetbootin in a repo near you./usefuloff

**gavint522: ** Go to this question and answer and see if it is helpful for what you are asking: [http://askubuntu.com/questions/289559/how-to-create-a-windows-8-bootable-usb-stick-with-ubuntu](http://askubuntu.com/questions/289559/how-to-create-a-windows-8-bootable-usb-stick-with-ubuntu)
[COLOR=#000000]


[/COLOR]

---

### Post by plurga on 2014-01-15
mm , do as I understand , u want to make u pc dualboot , right ??

[http://askubuntu.com/questions/6317/how-can-i-install-windows-after-ive-installed-ubuntu](http://askubuntu.com/questions/6317/how-can-i-install-windows-after-ive-installed-ubuntu)

or 

do u want to know , how to burn a dvd ??

[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-ubuntu](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-ubuntu)

---

### Post by mörgæs on 2014-01-15
Next time please use a more informative thread title.
Changed.

---

