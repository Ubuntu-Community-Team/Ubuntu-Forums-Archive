---
title: "Permissions of disk could not be determined"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by adelin on 2008-05-26
Hi. I have a problem. I am using utorrent with wine and I added the two partitions I have to use with utorrent. Everything worked fine until I installed a web design program and plugins. I did this:
sudo apt-get install quanta
sudo apt-get install kompare
sudo apt-get install kxsldbg
sudo apt-get install kimagemapeditor
sudo apt-get install cervisia
The program I installed Quanta Plus seems to work fine, but utorrent cannot access any of the files it was downloading before I installed the programs mentioned above. It gives the error Error:Write protected, so I try to go to my partitions and change the permissions but in the right click- permissions menu I get : The permissions of disk could not be determined. Two days ago I created a script from a forum that allows me to open anything as root by right clicking on it. I open my partition as root and the permissions appear to be fine as I had left them, with allow read and write, but when I am done I go back to right click permissions on the partition and nothing has changed. The same error message saying The permissions of disk could not be determined.
If you have a solution to my problem please write it step by step because I only have 3 days since I started using ubuntu so I don't know almost anything.
Thank you.

---

### Post by sayakb on 2008-05-26
Open the folder in a terminal and use:
```
sudo chmod +w filename
```Otherwise, at a terminal, do:
```
gksudo nautilus
```And then try to change the permissions using the GUI as you were trying earlier.

More on octal access-permissions: [http://bugclub.org/beginners/networking/chmod.html](http://bugclub.org/beginners/networking/chmod.html)

---

### Post by adelin on 2008-05-26
Thanks for the quick reply. Your first solution sudo chmod +w filename didn´t work but the second one gksudo nautilus allowed me to change my permissions but after closing that window I get the same error message in utorrent and when I right click the partition on my desktop in permissions I get the same error message The permissions of disk could not be determined.
As I imagine (I don´t really know what I´m saying because I´m new to ubuntu) the permissions are set but are not recognized.
Thanks. If you have any more solutions I would be very grateful.

Forgot something. I can access the partition. I can create, delete access or modify any file or folder in it. utorrent is the one that can´t access it.

---

### Post by adelin on 2008-05-26
I found the cause of my problem. Maybe this will help you help me. I have a USB Cdrom. I unplugged it to use it on another computer I have then I plugged it back in. One partition´s drive letter was replaced by the cdrom, now the cdrom is D.

---

### Post by adelin on 2008-05-26
All this posting took me half an hour, enough time to reinstall ubuntu. So that´s what I´m gonna do. Thanks anyway but I´ll just reinstall ubuntu.

---

