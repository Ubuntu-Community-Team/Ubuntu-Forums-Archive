---
title: "[SOLVED] Can't get HP printer working."
date: 2008-07-23
forum: New to Ubuntu
---

### Post by Whatrymes on 2008-07-23
Hey:

I can't get my HP Photo smart C6280 printer working. I keep trying the installer from HP ([http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)) but the terminal keeps saying it can't open it. So I tried using Linux to install drives via system/administration/printers but I don't understand the language. My computer is wireless, the printer is Ethernet cable to a wireless router.

Ps. I swear I've tried both methods before and they worked fine, hum.

Ed

---

### Post by halitech on 2008-07-23
so the printer is a network printer? do you know the IP address for it?

---

### Post by Whatrymes on 2008-07-23
Yes

---

### Post by UbuntuNerd on 2008-07-23
check here they seem to be talking about the same printer

[http://ubuntuforums.org/showthread.php?t=638170&page=2]("http://ubuntuforums.org/showthread.php?t=638170&page=2")

---

### Post by Whatrymes on 2008-07-23
No. His links are the ones I've tried. I'd like to use Ubuntu's setup but I don't know the language (Absolute Beginer). Can I be given a walk through.

Ed

---

### Post by halitech on 2008-07-23
since you know the IP address, lets try to walk through it.

1. open Printing - System - Administration - Printing
2. Click New printer
3. Select AppSocket/HP Jet Direct
 a. Enter the IP address where it says Hostname, leave the port at 9100
Click Forward
4. Select HP in the list of printers in the database and click forward
5. Find Photosmart c6180 and select it and click forward
6. fill in printer name, location and readable name and click apply.

if this all works out, you should have a functioning printer

---

### Post by rockstarrem on 2008-07-23
> **Whatrymes said:**
> Hey:

I can't get my HP Photo smart C6280 printer working. I keep trying the installer from HP ([http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)) but the terminal keeps saying it can't open it. So I tried using Linux to install drives via system/administration/printers but I don't understand the language. My computer is wireless, the printer is Ethernet cable to a wireless router.

Ps. I swear I've tried both methods before and they worked fine, hum.

Ed

Hello,

Try chmodding the HPLips file. I had to: chmod 777 hplips file 

Replace "hplips file" with the actual hplips file then run the installer. Don't run it as root either.

---

### Post by Whatrymes on 2008-07-23
Thanks Halitech, that was it.

Ed

---

### Post by halitech on 2008-07-23
glad it worked for you :)

don't forget to mark the thread solved if its working.

---

### Post by Whatrymes on 2008-07-23
I don't know how to do that.

---

### Post by halitech on 2008-07-23
up at the very top, you should see thread tools, click that and it should give you an option as mark solved.

---

### Post by Gobbie on 2008-08-29
> **rockstarrem said:**
> Hello,

Try chmodding the HPLips file. I had to: chmod 777 hplips file 

Replace "hplips file" with the actual hplips file then run the installer. Don't run it as root either.

I've got this problem too but I've got no idea about chmodding.  Could someone spell it out for me please?!

---

### Post by Gobbie on 2008-09-01
Bump

---

### Post by o.besner on 2008-09-01
"Chmodding" is to use the command chmod to modify the permissions of a file

let's say you want to have the rights to execute "Thisisatest.sh" on your Desktop

type in a console "cd Desktop"
then "sudo chmod 777 Thisisatest.sh"

---

