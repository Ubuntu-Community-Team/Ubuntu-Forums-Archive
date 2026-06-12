---
title: "Duplex printing, brother 2070n"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by japhyr on 2008-09-02
Hi everyone,

I have a brother 2070n laser printer, and I've been using the hl1250 driver listed on the OpenPrinting database ([http://www.openprinting.org/show_printer.cgi?recnum=Brother-HL-2070N]("http://www.openprinting.org/show_printer.cgi?recnum=Brother-HL-2070N")).  I am starting another semester of grad school, and gaining the ability to use duplex printing would save a lot of trees.

Should I try the manufacturer driver listed on the above page?  Duplex printing would be nice, but the last thing I need is to muck up my whole printing setup entirely.  Any advice?

---

### Post by plucky on 2008-09-02
FYI :If you are running Hardy Heron (8.04.1) the Brother Printer drivers are now packaged in Synaptic.

See the [Brother Driver Packaging page](https://wiki.ubuntu.com/BrotherDriverPackaging?highlight=(brother))

If you use synaptic drivers,then the drivers will be updated when you upgrade.
You have to install both the CUPS wrapper and LPR driver,just search for brother 2070n.

> Duplex printing would be nice, but the last thing I need is to muck up my whole printing setup entirely. Any advice? 

Sorry don't have a Laser printer,but my Brother inkjet was very easy using the packages in Synaptic and the Printer setup GUI.

Also printer setup using the CUPS web interface is very straight forward.From your web browser input in the address bar ```
localhost:631/admin
```


Enjoy :)

---

