---
title: "can 64 bit support??"
date: 2014-02-18
forum: New to Ubuntu
---

### Post by Hasan55 on 2014-02-18
hey helpful guys plz advice me...............

my pc configaration is .......... MOTHER BOARD GIGABYTE G41M-COMBO
                                  RAM 3 GB
                                  PROCESSORE : INTEL DUAL CORE
                                  GRAPHIC CARD : (NO EXTRANAL GRAPHIC) BUT MOTHER BOARD 
                                  CONSISTING TOTAL GRAPHIC 1326 MB 

my question is ...........can my pc configuration support 64 bit operation system??????????
i always use 32 bit operating system so i want 64 bit .
is there any benefit to swich off 32 bit to 64 bit ,plz tell your anwser in detail. thanks

---

### Post by Bucky Ball on 2014-02-18
A dual-core is 64bit. A 64bit operating system can take full advantage of the hardware, CPU and RAM. There is no problem with still being able to use any 32bit applications you might want to use that do not have 64bit versions (and if there was an issue it would be an oddity) on a 64 bit system.

---

### Post by open2reason on 2014-02-18
Hassan55,
One of the Gigerbyte G41M Combo specification pages offers both 32 & 64 bit driver downloads which to me suggests that 64bit operation is possible [http://www.gigabyte.com/products/product-page.aspx?pid=3505&dl=1#dl](http://www.gigabyte.com/products/product-page.aspx?pid=3505&dl=1#dl) . 
Is it possible for you to download a live Ubuntu image 64bit [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) and see if it runs on your machine?
Be sure to make backups of data you value prior to running the live CD.

---

### Post by Bucky Ball on 2014-02-18
> **open2reason said:**
> Hassan55,
One of the Gigerbyte G41M Combo specification pages offers both 32 & 64 bit driver downloads which to me suggests that 64bit operation is possible [http://www.gigabyte.com/products/product-page.aspx?pid=3505&dl=1#dl](http://www.gigabyte.com/products/product-page.aspx?pid=3505&dl=1#dl) . 
Is it possible for you to download a live Ubuntu image 64bit [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) and see if it runs on your machine?
Be sure to make backups of data you value prior to running the live CD.

Huh??? It's a dual-core processor. It's 64bit. No point in going much further ... :-k

@OP: Post the output of

```
lspci
```

That will tell you about the CPU along with all the other hardware ...

---

### Post by oldfred on 2014-02-18
I have only slightly different Gigabyte EP43 which also is a socket 775 system. I have a Intel(R) Core(TM)2 CPU 6600 chip from 2006, original motherboard was replaced with the EP43 in 2009 and about then I converted from 32bit to 64bit.

You have to do a new clean install. There is no upgrade. Best to export list of installed applications, backup all of /home and if you manually edited any files in /etc or elsewhere in system like cron tasks or grub back those up also.

---

### Post by 3rdalbum on 2014-02-18
> **Bucky Ball said:**
> Huh??? It's a dual-core processor. It's 64bit. No point in going much further ... :-k

@OP: Post the output of

```
lspci
```

That will tell you about the CPU along with all the other hardware ...

All the dual-core CPUs that fit into that motherboard are 64-bit.

As for the benefits, you get a small boost in speed for everyday tasks and a decent speed boost for intensive tasks (such as video encoding). There are also a handful of behind-the-scenes security features in 64-bit that couldn't be implemented in 32-bit. If you already have 32-bit Ubuntu installed, don't bother reinstalling just to get 64-bit. But if you haven't installed Ubuntu yet, you can definitely choose the 64-bit edition.

---

