---
title: "USB will not launch Ubuntu 12.04 Installation Process"
date: 2013-01-24
forum: New to Ubuntu
---

### Post by DZDB on 2013-01-24
I successfully downloaded the Ubunto 12.04 installation file (ubunto-12.04 1-desktop-1386.iso) file on my usb formatted (32-bit) flashdrive. The particulars of my custom built computer are as follows:
 
MB: Asus M5A78L-M LX
RAM: 8 GB
Operating System: None - I am trying to install Ubuntu 12.04
 
BIOS Priority Boot Order: 1) USB 2) Hard Disk
Note: I don't have a CD/DVD drive
 
 
More Information:
The BIOS sees the USB drive, the Hard Drive, and the RAM.
 
 
I insert the flash drive (loaded with the Ubunto Installation file) in a USB port (I have tried several different USB ports). I then turn on the computer. And then I always get the following message:
 
"Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key".
 
So my question is how do I resolve this issue?

---

### Post by Timpster on 2013-01-24
DELETE all ubuntu related files from the flash drive

Show hidden files and delete the .disk folder

And anything that has ubu in the name and anything with the same date / time

Install Unetbootin

Click disk image in unetbootin
Select the Ubuntu iso
Select your flash drive
Click ok

Reboot and enjoy

If it doesn't work re download ubuntu

Also check out redshift
Just install it from ubuntu software center or other programs
Add a startup application

redshift -t 6500:4700 -g 0.73

Enjoy
The -g 0.73 makes things dark things darker and brighter things stand out more
It's called gamma
You can use this to make the screen a more green color if it's too red

redshift -t 6500:4400 -g 0.9:1.0:0.9
Redgamma:greengamma:redgamma
So there is a LOT of options to change if you need to so have fun and don't strain your eyes at night

Hey when you set redshift for the first time
After about an hour stop the process
Go to system monitor and end redshift
A smoother way is to run it in the terminal and press ctrl c haha

---

### Post by DZDB on 2013-01-27
Teamster, although belated your post solved my issue.  Thank you so much.  I am a complete newby and I was intially floored by the phrase "Install Unetbootin".  I had no idea what Unetbootin was.  However I Googled "Unetbootin" and then went to the following website:
 
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
 
There I found the detail instructions that I needed to create my bootable Ubuntu 12.04 USB Flash Drive.
 
Once again Teamster, thank you.

---

