---
title: "OKI Printer driver"
date: 2006-10-10
forum: Programming Talk
---

### Post by vulpeso on 2006-10-10
My kingdom for a driver for my printer. It's odd that Linux printer drivers are so HP centric. There seems to be one for every HP printer on the planet. I have an OKI 3200n. There seems to be no Linux driver for it. I am so frustrated with porting my print jobs to my legacy winblows box that I am ready to learn how to write Linux printer drivers and write one for my OKI. Can anyone point me to resources for how to write printer drivers for Linux? (I am running Ubuntu Daper Drake.)

--PF

---

### Post by cronholio on 2006-10-11
You will find this helpful: [http://lwn.net/Kernel/LDD3/](http://lwn.net/Kernel/LDD3/)

Btw, I doubt that OKI would disclose their protocol to you, it might be best to buy a new printer.

---

### Post by vulpeso on 2006-10-11
Thanks, for your reply. I did at least write OKI to ask if they are considering providing Linux drivers. I quoted *Linux Device Drivers*, saying, "Hardware vendors, by making a Linux driver available for their products, can add the large and growing Linux user base to their potential markets". Maybe if enough of us bug the hardware vendors for drivers, they'll take it to heart.

---

### Post by vulpeso on 2006-10-12
FYI, here is a copy of my inquiry to OKI and their lame response.

Thank you for your inquiry.


Your problem in that particular program may have to do with the fact that this is a GDI or "Host-Based" printer.  There may be some limitations in very old programs or programs that do not follow Windows standards completely.  Unfortunately, there are no alternative drivers or emulations available for these products. There are no plans to do so. You would need an higher end model like the C6100n or higher which is an PCL and PS printer. I am sorry for any inconvenience.



If we can do anything else for you in the future, please don't hesitate to ask!
Also, you may be interested to know that Oki Data has now launched my.okidata.com, which allows you to access Personalized Solutions information for all your Oki Data Products.

Your Personal Solutions Specialist

 ===================== Original Message ===================

Dear OKI,

I have a 3200n that I would love to be able to print to from my Linux system. Has OKI considered writing Linux drivers? Hardware vendors, by making a Linux driver available for their products, can add the large and growing Linux user base to their potential markets.

Thanks,

---

### Post by cronholio on 2006-10-12
> programs that do not follow Windows standards

Wtf??? Did they read your email at all? :-?

---

### Post by vulpeso on 2006-10-12
Sounds to me like they just want to sell me a C6100n. F#$*ing capitalists.:mad:

---

