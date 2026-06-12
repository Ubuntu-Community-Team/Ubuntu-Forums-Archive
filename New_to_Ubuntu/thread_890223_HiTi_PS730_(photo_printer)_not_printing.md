---
title: "HiTi PS730 (photo printer) not printing"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by linkmaster03 on 2008-08-14
I installed my HiTi PS730 photo printer through the GNOME CUPS printer setup. I downloaded the drivers from [here]("http://www.opendrivers.com/driver/220834/hi-ti-photo-printer-driver-v1.00-linux-free-download.html"). Jobs are sent just fine without error, but the printer physically doesn't even make a sound. I'd be very grateful if someone helped me get this working.

The CUPS web interface shows the following information about the installation:

[img]http://img297.imageshack.us/img297/9458/14augthu2116ma8.png[/img]

Some USB info from /dev:

```
brad@debian-seed:~$ ls /dev | grep lp
lp0
brad@debian-seed:~$ ls /dev | grep usb
usbdev1.1_ep00
usbdev1.1_ep81
usbdev2.1_ep00
usbdev2.1_ep81
usbdev3.1_ep00
usbdev3.1_ep81
usbdev4.1_ep00
usbdev4.1_ep81
usbdev4.2_ep00
usbdev4.2_ep81
usbdev4.2_ep82
usbdev5.1_ep00
usbdev5.1_ep81
usbdev5.5_ep00
usbdev5.5_ep01
usbdev5.5_ep81
```

---

### Post by nicedude on 2008-08-15
Well I looked into your problem for you and was extremly pleased to see that HiTi provides a Linux based driver for your printer. So I would recomend you use it and not CUPS as even though CUPS are cool people for giving linux support where there is none I would recommend using the factory stuff when it is available. Here is a link to HiTi's download center, select linux as the os and then your model # and download the driver.

[http://www.hitouchimaging.com/](http://www.hitouchimaging.com/)

If you cannot compile the driver yourself ask here and I will try to help you but it isn't that hard ( you unzip it -> put the unzipped directory somewhere like home folder -> enter that directory at a command line -> then you will either have to type "./configure" or "make" & then "make install" depending on how they do their setup. If you cant figure it out ( read the readme & install text files in the download ) then ask and I will download the drivers and figure it out for you, but I am sure the real drivers will do a better job for you :-)

hope this helps

---

### Post by linkmaster03 on 2008-08-15
I've tried that, but actually it's the same driver. I just tried it again and no luck. :(

---

### Post by nicedude on 2008-08-15
Have you tried Emailing HiTi support? They most certainly have more experience with this than anyone else. I am sorry not to be more help but without the equipment in front of me and having no experience with anything of that brand I kinda am at a loss. If the manufacturer or anyone else for that matter give you any advice on what to do and you can't figure out how to do it, then that I could help with.

---

### Post by linkmaster03 on 2008-08-16
I'll see what I get back.

---

### Post by linkmaster03 on 2008-08-18
They aren't responding. I made a post on their forums and to their support email. :mad:

---

### Post by nicedude on 2008-08-18
I am pretty much in uncharted water here as I don't have any experience with the company in questions printers. I hate to ask this ( first time I have actually ) but do you know if this printer works in Windows right now? I only ask to rule out any physical problems with the device.

---

### Post by linkmaster03 on 2008-08-18
Yes it works in Windows, and it works if I print directly from an SD or CF card.

---

### Post by linkmaster03 on 2008-08-21
Anyone? :(

---

### Post by ljerabek on 2009-06-23
I have this exact issue with a HiTi 641PS. I contacted HiTi they told me the can't provide the code or further support for Linux. It's kind of unfair when you think they claim to support the Linux community but then fall far short of providing a working driver. From what I could tell is the driver is expecting an older version of Linux. These HiTi printers rock but lack of Linux support is a killer.

---

