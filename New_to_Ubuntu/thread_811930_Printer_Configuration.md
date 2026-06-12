---
title: "Printer Configuration?"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by spotteddog on 2008-05-29
Using Hardy with iP4500 printer. I just realized that I can't do any type of printer maintenance with Hardy, such as align print heads, clean print heads, monitor ink tank levels, etc.

How do I do these things? Do I have to log back into Windows?

Thanks

---

### Post by spiderbatdad on 2008-05-29
have you been to the cups page? There might be some patches or another driver available:

[http://localhost:631](http://localhost:631)
Note: you are logged into your print server on this page, and can make changes to cups config.

---

### Post by shifty_powers on 2008-05-29
try typing

```
http://localhost:631/
```

into a firefox tab and see what options cups gives you...

---

### Post by spotteddog on 2008-05-29
> **shifty_powers said:**
> try typing

```
http://localhost:631/
```

into a firefox tab and see what options cups gives you...
Looks like that is what I was looking for. I'll go through it all tonight. 

Thanks

---

### Post by shifty_powers on 2008-05-29
no problem gald to have helped ;)

---

### Post by spotteddog on 2008-05-30
Maybe I'm just missing the whole picture? But after going over cups material last night, I still can't find anyway to: run a print-head cleaning utility, Align print heads, Moitor ink supply.
If these options are not available through cups, how does everyone do these things?
Thanks

---

### Post by philinux on 2008-05-30
I use mtink which is in synaptic.

em tee ink gedit

---

### Post by spotteddog on 2008-05-30
> **philinux said:**
> I use mtink which is in synaptic.

em tee ink gedit
I'll look there tonight. Thanks for the quick response!

---

### Post by spotteddog on 2008-05-30
> **philinux said:**
> I use mtink which is in synaptic.

em tee ink gedit
This is exactly what I am looking for. But it will not work with my (Canon) printer. 

Thanks anyway

---

### Post by silvanus2005 on 2008-05-31
You can`t print, or are you interested in performing those maintainance things?

---

### Post by ramjet_1953 on 2008-05-31
You could always download the demo version of TurboPrint and see if it does what you want. The 2.0Beta Version looks nice.

With the demo version, anything above 300dpi prints a watermark on each page.
The full version costs 29.95 Euros, unfortunately.

[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

Regards,
Roger :o

---

### Post by cariboo on 2008-05-31
Canon doesn't seem to want to bother with supporting linux. I've got a Canon scanner:( and there is absolutely nothing forthcoming from Canon in the way of drivers for the darn thing.

There are no maintenance functions for your Canon printer in cups or anywhere else for all that matters. You will have to do it in Windows.

Next time you buy a printer go with either HP or Epson as the are well supported in cups.

Jim

---

### Post by philinux on 2008-05-31
> **spotteddog said:**
> This is exactly what I am looking for. But it will not work with my (Canon) printer. 

Thanks anyway

It does need the launcher modifying to include gksudo I think.

You could try and install your canon printer software with Wine.

---

### Post by spotteddog on 2008-05-31
Thanks for all the suggestions. I appreciate it.

I ended up buy new peripherals for Vista, because my old ones lost some functions with the Vista upgrade. 
It looks like if I want to stick with Ubuntu, I'll have to buy all new peripherals again. 

Thanks anyway.

---

