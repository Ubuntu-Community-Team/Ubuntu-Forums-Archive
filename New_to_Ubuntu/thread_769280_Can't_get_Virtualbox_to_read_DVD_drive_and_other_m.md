---
title: "Can't get Virtualbox to read DVD drive and other mess"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by SlappyPappy on 2008-04-26
I installed Virtualbox from Synaptic. No problem. Well there was a problem, no permissions for me to run it but I figured that out. There goes one hour of my life.

Now I'm trying to install an OS but the Virtualbox isn't reading the DVD in the drive. So I made an .iso to work around it. Still won't boot even though it is bootable.

So I tried to get the floppy boot disk to work. Even though Virtualbox sees it, for whatever reason it chokes on it and can't read it. So I make image file of it.

Now I boot up, sees image file fine, then boot up. Next problem is it can't boot with CDROM support. Pretty worthless at this point.

Totally stuck here.

BTW for whatever reason Virtualbox sees my DVD drive as /dev/fd0 which is plain wrong as that's the floppy drive. Can't find a way to change a setting so it can see my DVD drive.

So far, not a big fan of Virtualbox in Ubuntu. Also, I'm in Gutsy cause I'm a Gutsy kind of a guy.

Any help you can offer? Thanks man.  :confused:

---

### Post by SlappyPappy on 2008-04-27
Virtualbox is a brutal piece of software to deal with. There is so much FUD, disinformation and general garbage out there. Totally ridiculous.

Well after a day of battling I've got Virtualbox up and running, usb, printer, and so forth.

I'm still in Gutsy so here are a few tips that will hopefully save some people the time that I lost.

1) Get the latest version which is currently 1.5.6 of Virtualbox. Go to their website. Stay away from the current piece of junk in Synaptic.

2) Be sure to put in the Guest Additions otherwise it's pretty crippled.

3) USB can be a pain. Best info I found was this link:

[http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html](http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html)

Worked a treat and cut through all the people who are way off course on how to get it going.

4) Printers can be a pain. I found this link, so simple and my printer sprung to life immediately. All I had to really do was download a driver and follow his directions:

[http://forums.virtualbox.org/viewtopic.php?t=1465&highlight=usb+printer](http://forums.virtualbox.org/viewtopic.php?t=1465&highlight=usb+printer)

So simple, makes sense, best printer in Virtualbox I found and I looked at a lot of people who claimed they had the answer. Yeah? Well they didn't.

WRAP-UP:
That should help you get going. This literally took me a day to figure out because of all the people who were just spit-balling when they really had no clue how to get it going. Again, I hope this helps someone out there. Now I'm going to get back to my Windows 2000 install and start moving my documents over with USB and start printing.

Peas to the middle.

---

