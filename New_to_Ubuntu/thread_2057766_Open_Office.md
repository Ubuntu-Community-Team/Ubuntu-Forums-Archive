---
title: "Open Office"
date: 2012-09-14
forum: New to Ubuntu
---

### Post by Jackalyn on 2012-09-14
Ok and on to the next problem. 

I have open office downloaded as a tar.gz file. I can extract the files and it is all there. What I cannot do is to actually install it. Can someone walk me through how? Thank you. It is Apache Open Office 3.4.1 and on Ubuntu 12.4.

I have tried to put a command into the terminal, but that just made it so Libre open from the dashboard even though it was a command for Open Office!

Thanks.

---

### Post by Jakin on 2012-09-14
Libre Office and Open Office are the pretty much the same, im not sure it'll let you install both.

But anyway There is a much easier way to do it than that.

sudo add-apt-repository ppa:upubuntu-com/office
sudo apt-get update
sudo apt-get install openoffice

---

### Post by Lars Noodén on 2012-09-14
Are you sure you want OpenOffice.org?  LibreOffice is in the repositories and is therefore much easier to install.  It's also gaining a bit of a lead over OOo in terms of development.

---

### Post by newb85 on 2012-09-14
Agreed.  Unless you have some reason you need to use OpenOffice instead of LibreOffice, you should stick with LibreOffice.

---

### Post by shreepads on 2012-09-14
> **newb85 said:**
> agreed.  Unless you have some reason you need to use openoffice instead of libreoffice, you should stick with libreoffice.

+1

---

### Post by Jackalyn on 2012-09-15
> **shreepads said:**
> +1  Can't get' readability' add on to work in Libre and I need it.

---

### Post by Hagar Delest on 2012-11-15
You can install AOO  and LibO with the .debs downloaded directly from the official web sites. Note that this way you can install and run both applications in parallel. But you need to remove the packages coming with the Ubuntu out of the box configuration first.

See: [[Ubuntu] Installing OOo on Debian and Co.](http://forum.openoffice.org/en/forum/viewtopic.php?f=74&t=68)

---

