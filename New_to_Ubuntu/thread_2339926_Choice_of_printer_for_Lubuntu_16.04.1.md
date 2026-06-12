---
title: "Choice of printer for Lubuntu 16.04.1"
date: 2016-10-14
forum: New to Ubuntu
---

### Post by nginmu on 2016-10-14
Epson XP-235
Epson XP-432
Epson XP-4520
Canon Pixma MG-2950
HP DJ3630

These are all all-in-one printer/scanners for sale currently at my local Tesco in the UK.

Does anyone know, are any of them good for trouble-free full featured operation (including wireless connection) under Lubuntu 16.04.1?

I see that the Epsons do have some manufacturer driver support for linux, but notes abound regarding the fact that many will only use the generic driver and wireless is sometimes unusable etc.

I'm trying to purchase an all-in-one printer/scanner that installs and works flawlessly with Lubuntu from the start.. rather than just buy any old unit and then spend weeks trying to make it do something it doesn't want to.

Thanks for any help.

---

### Post by mörgæs on 2016-10-14
First of all I think you should ask Tesco about that. It's not a given fact that they are able to answer but at least they should know that consumers have an interest in the topic.

---

### Post by nginmu on 2016-10-14
Yeah, I did ask but I was met with a blank stare and the question "what's linux?" - pretty much as I expected. They only know what's written on the outside of the box.

---

### Post by nginmu on 2016-10-14
Alternatively, if anyone can recommend a decent scanner / printer known to work flawlessly with Lubuntu that's easily available in the UK, let me know.. probably willing to spend up to £100 tops. Usage will be light business front-end stuff, scanning & printing invoices etc - no need for extremely high quality photo printing, or particularly high speed / volume operation. Just a good basic occasional machine.

---

### Post by mörgæs on 2016-10-14
Normally I recommend [https://www.thinkpenguin.com/catalog/printer-all-one-gnulinux](https://www.thinkpenguin.com/catalog/printer-all-one-gnulinux) but I don't know if they send their orders overseas and what the transport will cost.

---

### Post by ajgreeny on 2016-10-14
The HP you mention is fully supported, as are most HP printers, but I do not know about the other makes.
See [http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_3630_series.html](http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_3630_series.html)

You will need hplip version 3.15.6 or newer so the version in 16.04 should be fine.
The **hplip-gui** package is worth installing as well as it gives you a great configuration application for printer maintenance and control.

---

### Post by monkeybrain20122 on 2016-10-14
I have picked up two used  printer/scanners all in one for free. Both work. The Epson M415 works out of the box, the Cannon Pixma works after installing driver from [https://launchpad.net/~inameiname/+archive/ubuntu/stable/+packages](https://launchpad.net/~inameiname/+archive/ubuntu/stable/+packages) There are a list of cannon printer drivers (the cnijfilter packages, click View Package details to see which printer is supported)

---

### Post by nginmu on 2016-10-14
Thanks!

HP DJ3630 - that looks like a direct hit for a full featured Ubuntu driver? should Lubuntu should be able to use it okay? And it does say the networking is supported, but do you think that means wireless as well as ethernet? [http://store.hp.com/UKStore/Merch/Product.aspx?id=K4T99B&opt=BEV&sel=PRN](http://store.hp.com/UKStore/Merch/Product.aspx?id=K4T99B&opt=BEV&sel=PRN)

Canon Pixma MG-2950 - can't specifically see that exact one listed in the cnijfilter packages, but that's a really helpful resource, big thanks for that one

Epson XP-235, XP-432, XP-4520 - Good to hear the Epson M415 works out of the box, that's encouraging, will keep on googling those if no joy with others

---

### Post by ajgreeny on 2016-10-14
Whether or not the HP works on wifi is more down to the printer hardware than Ubuntu or the drivers, I suspect; HP say it is a wifi printer so I think it should work fine.

Give it a static local IP using the reservation system in your router for ease of setup.

I use an HP Photosmart 6520 over wifi for both printing and scanning without any difficulties at all, and I imagine you will find the same with that printer if it has wifi capability.

---

### Post by nginmu on 2016-10-14
Dammit, they sold the last one.

I bought this instead: 
Hp Envy 4520
[http://store.hp.com/UKStore/Merch/product.aspx?sel=PRN&id=J6U70B&opt=ABU](http://store.hp.com/UKStore/Merch/product.aspx?sel=PRN&id=J6U70B&opt=ABU)

Hoping it's supported, being HP.. but extracted a promise they'll take it back if not. Fingers crossed.

[edit] 
[http://hplipopensource.com/hplip-web/models/other/envy_4520_series.html](http://hplipopensource.com/hplip-web/models/other/envy_4520_series.html)
looking good so far. confident enough to open the box!

Thanks for the excellent help everyone.

---

