---
title: "How to add paper size 8.5x13 in epson L110 in Ubuntu 12.04.1"
date: 2013-02-14
forum: New to Ubuntu
---

### Post by auxilium on 2013-02-14
Hi,

Using LibreOffice I have the option letter 8.5x11, legal 8.5x14 and long bond 8.5x13. But when I print to Epson L110, its properties don't have 8.5x13 instead it chooses 8.5x14. So does it makes the print out exceed to the margin. And print out goes ruined.

How can I add the 8.5x13 paper size to Epson L110 in Ubuntu 12.04.1 32-bit.

This is my LibreOffice version: 
Version 3.6.0.1 (Build ID: 360m1(Build:101))

This is my Epson Driver: 
Epson L110 Series - epson-inkjet-printer 1.0.0-1lsb3.2 (Seiko Epson Corporation LSB 3.2)


Thank you in advance

---

### Post by auxilium on 2013-02-15
bump..

Does any1 know or can help me point out where to get this fixed



Thank you

---

### Post by pdc on 2013-02-16
I haven't googled it to be sure .....

.....but I suggest you edit the ppd file for your printer: you have the full Epson driver installed.......well done.......

if I look at the ppd file for my MG3100 series Canon ..

.....I have copied and pasted a section below

> *PageSize Letter/Letter [8.50"x11.00" 215.9x279.4mm]: "<</CNPageSizeName(Letter)/PageSize[612 792]/ImagingBBox null>>setpagedevice"
*PageSize Letter.bl/Letter(borderless) [8.50"x11.00" 215.9x279.4mm]: "<</CNPageSizeName(Letter.bl)/PageSize[612 792]/ImagingBBox null>>setpagedevice"
*PageSize Legal/Legal [8.50"x14.00" 215.9x355.6mm]: "<</CNPageSizeName(Legal)/PageSize[612 1008]/ImagingBBox null>>setpagedevice"



...if you use the Search function and search on ppd

you should find your ppd (mine is in etc/cups/ppd/)

..I would have thought you could define a new entry...........

...and I guess call it long bond .........

.......something on the lines of

> *PageSize Letter/long bond [8.50"x13.00" 215.9x??.4mm]: "<</CNPageSizeName(Letter)/PageSize[??? ???]/ImagingBBox null>>setpagedevice"

you need to research the page size......ie is detailed for each entry

.......to edit the command  would be 

> [COLOR="Red"]gksudo gedit /etc/cups/ppd/*EpsonL110whatever*.ppd[/COLOR]

SAVE CLOSE

__________________________________________________________________________________________________________-

after posting the above; and googling around long bond, I find this bug report

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1062091](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1062091)

that suggests that editing the ppd file may not work..we can only hope it does

_____________________________________________________________________________________________________________-

could you perhaps be posting from the Philippines?

I ask because this thread

[https://issues.apache.org/ooo/show_bug.cgi?id=91260](https://issues.apache.org/ooo/show_bug.cgi?id=91260)

says that long bond is 8.5x13 in the Philippines......................whereas long bond is 8.5x14 in other places?

---

### Post by auxilium on 2013-02-17
thanks for the effort pdc!

yes im from philippines

are out of luck now?

---

### Post by pdc on 2013-02-17
> are out of luck now? 

....... you could be......but have a go at my suggestions...... :D

---

### Post by auxilium on 2013-02-17
Glad to give it a shot.

Its better than nothing, else I had to manually adjust every page I will print for Long Bond size.

I'll post back later

Thank you for helping me out, lets hope alll goes well 



Cheers,

---

### Post by auxilium on 2013-02-20
Sorry guys I was busy for some hi priorties.

I will try this some time later and I'll get back to report the result

Hopefully it will work.

Thank you for hanging on

---

### Post by auxilium on 2013-03-28
Hi

I'm back after some time of busy days. Well, so many things had happened already. I haven't done anything but I could print using the "Long Bond" option maybe all those updates solve the case.

Thanks for the support too, PDC.



Cheers

---

