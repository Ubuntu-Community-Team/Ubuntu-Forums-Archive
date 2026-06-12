---
title: "USB ADSL modems..no conection"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by Ducatiboy Stu on 2008-06-27
Just realised that USB modems dont work, at least not on the live CD of Ubuntu & Xubuntu....

My lappy has a LAN port ( which runs Hardy rather well) so I have been blissfully unaware of this problem until I used the Live CD's on my home PC...which does not have a LAN card...

The Modem is a Siemens Speed stream 4200...

Does anyone know how to get it to work without installing a LAN card...??

---

### Post by mjwhitfield on 2008-06-27
This any help?

[http://www.linuxquestions.org/questions/debian-26/network-connection-540398/](http://www.linuxquestions.org/questions/debian-26/network-connection-540398/)

---

### Post by Ducatiboy Stu on 2008-06-27
Unfortunatly my problem is that it is a USB connection to the modem ( which also has an ethernet port)..

I know the modem works, because I plug my lappy into the LAN port ( with  hardy) and can surf at at the same time as my PC using XP with the USB port..

It is more of a USB driver issue....

---

### Post by sharks on 2008-06-27
u can try sudo pppoeconf

---

### Post by manishtech on 2008-06-27
I also face the same problem with modem at my home,wheras the modem provided by Airtel at my college works fine out of box.
It all depends whether the driver is available or not.

I believe USB is not fit for internet. Why do we need USB when we are happy with ethernet?

Look here what Ubuntu help has to say about it
[https://help.ubuntu.com/community/UsbAdslModem](https://help.ubuntu.com/community/UsbAdslModem)
It says USB: **Unsuitable for Broadband** ](*,)

---

### Post by sharks on 2008-06-27
i also have internet thru USB and i m happy with that.

---

### Post by manishtech on 2008-06-27
> **sharks said:**
> i also have internet thru USB and i m happy with that.
I also have internet through USB at my college and am also *happy* with that.

We are happy only when it works, I was damn frustrated when it didnt work at home. After searching the CD for drivers,I found one only for RHEL. After trying hard to compile it, had to leave it in dismay. Finally I figured out the reason. It was for 2.4 kernel.

---

### Post by Ducatiboy Stu on 2008-06-27
I do tend to think that it should work..


It is getting it to work....afterall it is a USB device...and I have had no issues with installing other USB devices...including an RS232/usb comm port adapter that works very well...:)

---

### Post by Tomatz on 2008-06-27
You should be able to install it (the modem drivers) with ndiswrapper if you have the modem driver disc.

If you do post back :)

---

### Post by manishtech on 2008-06-27
> **Ducatiboy Stu said:**
> I do tend to think that it should work..


It is getting it to work....afterall it is a USB device...and I have had no issues with installing other USB devices...including an RS232/usb comm port adapter that works very well...:)
I am also the believe or "It should work"

Only two things dont work on my ubuntu, wi-fi and USB modem connection at my home... rest all work flawlessly out of box without a sinlge tweak

---

### Post by manishtech on 2008-06-27
> **Tomatz said:**
> You should be able to install it (the modem drivers) with ndiswrapper if you have the modem driver disc.

If you do post back :)
He He!!!
Even the windows driver is crappy at my college and USB works like charm.
At home windows driver is a bit better and it doesnt work in Ubuntu.

I may ask my bro at home to try and tell provided he understands ndsiwrapper and driver stuffs. Maybe I have to write a good manual for it :)

---

### Post by Canis familiaris on 2008-06-27
> **Ducatiboy Stu said:**
> Just realised that USB modems dont work, at least not on the live CD of Ubuntu & Xubuntu....

My lappy has a LAN port ( which runs Hardy rather well) so I have been blissfully unaware of this problem until I used the Live CD's on my home PC...which does not have a LAN card...

The Modem is a Siemens Speed stream 4200...

Does anyone know how to get it to work without installing a LAN card...??

No Offense mate. But buy a LAN card. It is very cheap and worth the investment even if you get the modem working with USB in Linux.

---

### Post by Canis familiaris on 2008-06-27
> **Ducatiboy Stu said:**
> I do tend to think that it should work..


It is getting it to work....afterall it is a USB device...and I have had no issues with installing other USB devices...including an RS232/usb comm port adapter that works very well...:)

I have to tell you: 

USB != Ethernet

Your router is not recognised when you plug in via router it can only communicate with your PC and hence you can use it.
However thorugh USB it has to be recognised and have drivers for it for effective communication b/w Router and PC.
So if it works with ethernet, it has no indication that it will work with USB.

---

### Post by manishtech on 2008-06-27
> **Anurag_panda said:**
> I have to tell you: 

USB != Ethernet

Your router is not recognised when you plug in via router it can only communicate with your PC and hence you can use it.
However thorugh USB it has to be recognised and have drivers for it for effective communication b/w Router and PC.
So if it works with ethernet, it has no indication that it will work with USB.
Surely agree with Anurag!

Why reinvent the wheel when we are very happy with Ethernet and esp when the new technology proving more of a headache than a solution?

---

### Post by Ducatiboy Stu on 2008-06-27
I do agree that I should just get a LAN card, but for the time being I am stuck with USB, plus I would then neet a small switch/hub as the modem only has 1 eth port..

Looks like a long search for a driver...if any...

---

### Post by manishtech on 2008-06-28
> **Ducatiboy Stu said:**
> I do agree that I should just get a LAN card, but for the time being I am stuck with USB, plus I would then neet a small switch/hub as the modem only has 1 eth port..

Looks like a long search for a driver...if any...
That driver would have to be provided by the router's company itself. Or wait for sometime and hope a generic driver which works on more wider range of USB modems.

---

