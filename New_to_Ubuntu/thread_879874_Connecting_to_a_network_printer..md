---
title: "Connecting to a network printer."
date: 2008-08-04
forum: New to Ubuntu
---

### Post by Suilenroc on 2008-08-04
So I've been having trouble connecting to my network printer on my Ubuntu computer. The printer is connected to the network via an ethernet cable straight to the router, and has the local IP address of 192.168.1.100. I can connect to the printer's status page by going to that address in a browser, but I just don't know how to connect to it to print with in ubuntu. The model is an HP OfficeJet 7590. 

Also, when I'm connected, will I  be able to scan documents into ubuntu? Thanks!

---

### Post by KillerSponge on 2008-08-04
In System->Administration->Printing you can add printers manually. I'm not really sure (my printer is connected via a Windows pc), but I think you should be able to connect to the device by entering it's URI in the "Other" section when adding a new printer.

---

### Post by gjoellee on 2008-08-04
check this out: [http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)

---

### Post by Suilenroc on 2008-08-04
How would I go about finding the URI for my printer? It's not 192.168.1.100, that's not being accepted by the dialogue.

---

### Post by AdamWood on 2008-08-04
You could try ipp://192.168.1.100

If you're connecting to the status page at that address it should be there.

---

### Post by Suilenroc on 2008-08-04
> **gjoellee said:**
> check this out: [http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)

That was, quite possibly, the most convenient little program that I've ever seen. That installed it right away, no hassle at all. Thanks so much for that!

(Ahah, I realized that I almost said +rep. I'm too used to Overclock.net...)

---

