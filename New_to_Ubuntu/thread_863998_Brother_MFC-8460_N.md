---
title: "Brother MFC-8460 N"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by jrev on 2008-07-19
Hi,
Where can I look for hardware compatibility in this forum ?

I have a photocopier linked to a computer with double boot ubuntu 8.04 and windows XP
This machine works fine with windows XP 
The Brother site doesn't mention Ubuntu .
 
Thanks for your advice :)

---

### Post by plucky on 2008-07-19
> **jrev said:**
> Hi,
Where can I look for hardware compatibility in this forum ?

I have a photocopier linked to a computer with double boot ubuntu 8.04 and windows XP
This machine works fine with windows XP 
The Brother site doesn't mention Ubuntu .
 
Thanks for your advice :)

In Hardy 8.04,the Brother printer drivers are now on Synaptic.

From **System > Administration > Synaptic Package Manager** search for **Brother MFC-8460** and you will get two packages.Install both the cups-wrapper and lpr-drivers packages.

Then open the **System > Administration > Printing** GUI and "Add New Printer" and it should find and install your printer.

See this link for further information on [Brother Driver Packaging](https://wiki.ubuntu.com/BrotherDriverPackaging?highlight=(brother))


Good Luck

:)

---

### Post by jrev on 2008-07-19
Thanks for this very good answer Plucky

The printer works fine

---

### Post by jrev on 2008-07-19
I probably need another driver to operate the scanner...

When I start Xsane, I got the message :

no peripheral available 

the photocopier is well on line and ready

---

### Post by plucky on 2008-07-19
> **jrev said:**
> I probably need another driver to operate the scanner...

When I start Xsane, I got the message :

no peripheral available 

the photocopier is well on line and ready

Yes you do,you have to download the debian file from the brother website depending on 32 bit or 64 bit **brscan2** and the scan tool file.It also has the installation instructions there.

See this link [http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html)


Good Luck


p.s. Not the .rpm file

---

