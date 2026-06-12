---
title: "Scanner not working"
date: 2012-04-20
forum: New to Ubuntu
---

### Post by Nath A on 2012-04-20
[SIZE=3]I have a  Cannon MF4412 printer/scanner/photocopier..I have ubuntu 11.10 installed on my pc
The printer seems to be working fine....But the scanner is not...I installed Xsane...but when i run it ....it says 
'NO DEVICES AVAILABLE ' even though the printer is connected...
I kindly help me out...
thanks in advance
Amit
[/SIZE]

---

### Post by ixtok on 2012-04-20
The only luck I have had getting my cannon multi function printer/scanner to work as a scanner was to download drivers from the Canon-Asia support area. Go to [http://www.canon-asia.com]("http://www.canon-asia.com")and find the  debian scanner driver for you series printer. I downloaded and decompressed it. I opened the terminal and navigated to the directory containing the decompressed file and found the file install.sh. I used the command ```
sudo ./install.sh
``` and it installed the driver. To scan I have to enter ther terminal and type ```
scangearmp
``` and the scanner comes to life. I am  not a newbie but rather a novice user so someone with more knowledge could probably tell you how to do this easier.

---

### Post by Nath A on 2012-04-20
> **ixtok said:**
> The only luck I have had getting my cannon multi function printer/scanner to work as a scanner was to download drivers from the Canon-Asia support area. Go to [http://www.canon-asia.com]("http://www.canon-asia.com")and find the  debian scanner driver for you series printer. I downloaded and decompressed it. I opened the terminal and navigated to the directory containing the decompressed file and found the file install.sh. I used the command ```
sudo ./install.sh
``` and it installed the driver. To scan I have to enter ther terminal and type ```
scangearmp
``` and the scanner comes to life. I am  not a newbie but rather a novice user so someone with more knowledge could probably tell you how to do this easier.
Thank you for prompt reply. I have seen the site that shows drivers for the printer only and not for the scanner on Cannon's website. Please tell me what should I do

---

### Post by tmaranets on 2012-04-20
Some printers aren't really nice/cooperative with Ubuntu. I have a Cannon MP620 that hates when I try to print something off Ubuntu. Try moving the files you want to print to a online cloud storage so can access them from another computer. Then print off the files from that computer.

---

### Post by Nath A on 2012-04-20
Can i use wine to use windows compatible drivers on  ubuntu 11.10 for my scanner???

---

