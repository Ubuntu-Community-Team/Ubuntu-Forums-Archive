---
title: "[SOLVED] Instaling Binaries"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by Jesan Fafon on 2008-11-09
Hi, I'm almost brand new to Linux and Kubuntu and trying to get my head around the differences between it and Windows. 

So my question is, is it possible to install binaries for, example, a game or word processor? As in, get to appear in the games section of the applications?

I saw a post on here about this, but the external links are broken, which don't help me much. 

Thanks!

---

### Post by anjilslaire on 2008-11-09
Yes, you can either install them from Add/Remove Programs or Synaptic, or if you've downloaded a .deb file you can click on it to install. [Getdeb]("http://www.getdeb.net/") is a great place to get new apps that are not in Synaptic. 

In many cases, the installer will add a menu entry. If not, you can create a ilnk yourself manually.

---

### Post by Jesan Fafon on 2008-11-09
ok, what if i have a tar.gz with a binary file contained instead of source code????

I can't find anything on google about it, save the "compile from source" walk-throughs. 

thanks.

---

### Post by echovolutionx on 2008-11-09
:confused::confused::confused:

---

### Post by CJ Master on 2008-11-09
If the TC is talking about Ubuntu apps, then the obove poster is correct.

If your talking about running windows apps then you'll need wine. (Google WineHQ.)

---

### Post by Bölvaður on 2008-11-09
Well you can install the program, for an example etqw (with binary installer from id website), but it will not make item in the menus or be able to autofill in the terminal (place a luncher in /usr/bin).

For that you need .deb, which is technically a binary file. Executable binaryfiles are able to do it, but normally they dont make your life easier :)

---

### Post by HotShotDJ on 2008-11-09
> **Jesan Fafon said:**
> ok, what if i have a tar.gz with a binary file contained instead of source code????It might be easier to help you if you could be more specific.  Exactly WHAT binary?   In other words, please specify what software you want to install.

---

### Post by Jesan Fafon on 2008-11-09
if I approach the file from konsole, using ./Nero(other junk).bin it will run. 

But, is it possible to install this? or am I S.O.L. (sorry out of luck)

NERO 2.0
(Neuro Evolving Robotic Operatives)

---

### Post by anjilslaire on 2008-11-09
<double post>

---

### Post by Bölvaður on 2008-11-09
> **Jesan Fafon said:**
> ok, what if i have a tar.gz with a binary file contained instead of source code????

I can't find anything on google about it, save the "compile from source" walk-throughs. 

thanks.

you would run the file either as root (sudo) or normal user. It is wiser not to use sudo unless if it is necessary, even when installing programs it might not be the wisest.

First take the binary file to your desktop. Make it executable either from properties when right clicking or use "chmod u+x cool_installer" in the terminal.

Then you either double click it or run it from the terminal "./cool_installer"

remember to "cd" to the proper directory like: "cd Desktop" and use "ls" to check what files are where you are located atm.

---

### Post by Jesan Fafon on 2008-11-09
> **Bölvaður said:**
> you would run the file either as root (sudo) or normal user. It is wiser not to use sudo unless if it is necessary, even when installing programs it might not be the wisest.

First take the binary file to your desktop. Make it executable either from properties when right clicking or use "chmod u+x cool_installer" in the terminal.

Then you either double click it or run it from the terminal "./cool_installer"

remember to "cd" to the proper directory like: "cd Desktop" and use "ls" to check what files are where you are located atm.

Thanks!! That took care of me.

---

### Post by Bölvaður on 2008-11-09
mark thread [solved] and thank comments that helped out (it will help others that are searching to forums to quickly find which posts are helpful)

---

