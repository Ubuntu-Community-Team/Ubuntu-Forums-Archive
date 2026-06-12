---
title: "Printer driver for Fuji Xerox DocuPrint 305 linux"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by appoloin on 2008-06-02
Printer driver for Fuji Xerox DocuPrint 305 linux

Please help :(
can anyone advise where i can find or alternative?

---

### Post by ardvark71 on 2008-06-02
> **appoloin said:**
> Printer driver for Fuji Xerox DocuPrint 305 linux

Please help :(
can anyone advise where i can find or alternative?

Hi...

I'm not finding anything on Google with respect to your printer. :( I imagine you've looked, too.

However, I would think The Linux Foundation would have some information and possibly drivers...

[http://www.linuxfoundation.org/en/OpenPrinting/Database/DatabaseIntro](http://www.linuxfoundation.org/en/OpenPrinting/Database/DatabaseIntro)

Their printer compatibilty page seems to be down at the moment but you can ask at their forums (one is specifically for Xerox,) or perhaps send them an e-mail.

Best Regards...

---

### Post by appoloin on 2008-06-02
Thank you

yeah been googling all day for it but no luck

---

### Post by davidsrsb on 2008-06-02
I use Fuji Xerox 4300 Apeosports and had to download the Linux driver source from the Japanese website and compile the ppd driver file set

---

### Post by x88a on 2008-06-02
u can try using the synaptic package manager

---

### Post by henri_p on 2008-09-16
David, 

Did you succeed to compile the source you downloaded??...seems I have problems doing it, missing vfork.h

---

### Post by kngharv on 2008-10-28
> **appoloin said:**
> Printer driver for Fuji Xerox DocuPrint 305 linux

Please help :(
can anyone advise where i can find or alternative?

Here is something I did.

I go to the Fuji-Xerox website, go search for the device driver.

Out of all the drivers, there is a "Adobe 

Postscript" driver in zip format.  

Download that zip file

unzip it.

in it, you will find a couple .ppd files.  There is a readme.txt file which tell you which one belongs to Docuprint 305.

I presume once you have .ppd file, you know what to do, right?


Harv

---

