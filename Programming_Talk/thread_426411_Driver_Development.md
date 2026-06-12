---
title: "Driver Development?"
date: 2007-04-28
forum: Programming Talk
---

### Post by JediSpam on 2007-04-28
I am currently a Computer Engineer major and i'm wondering if Driver Development is what I should focus on. I'm interested in drivers and how they work and make hardware efficient. What languages should I focus on? I just finished Computer Science 3 in college and i'm pretty good at c++/java

---

### Post by moma on 2007-04-28
Linux device drivers and modules (as the kernel itself) are written in C language.

Important documents:

Howto do kernel development. Converting to a kernel monkey.
[http://lwn.net/Articles/160191/](http://lwn.net/Articles/160191/)
+
[http://www.kroah.com/log/linux/howto.html](http://www.kroah.com/log/linux/howto.html)

Online book: Linux Device Drivers
[http://www.xml.com/ldd/chapter/book/index.html](http://www.xml.com/ldd/chapter/book/index.html) but the [3.ed]("http://amazon.com/s/ref=nb_ss_gw/103-9189315-6600663?url=search-alias%3Daps&field-keywords=linux+kernel+&Go.x=0&Go.y=0&Go=Go") is more up to date. ( EDIT: [online PDF edition...]("http://lwn.net/Kernel/LDD3/"))

Device Driver Kit  (Download this KIT before you start :-)   Open the .iso file in your file browser. Surprise, it also contains the 3.edition of ldd.
[http://kerneltrap.org/node/6638](http://kerneltrap.org/node/6638)

Coding in and for the kernel, coding style 
[http://kerneltrap.org/files/Jeremy/CodingStyle.txt](http://kerneltrap.org/files/Jeremy/CodingStyle.txt)

A tiny driver sample
[http://www.linuxdevices.com/articles/AT3711365653.html](http://www.linuxdevices.com/articles/AT3711365653.html)

There have been some tests on using C++ in the kernel, but honestly, it doesn't fit in.
[http://netlab.ru.is/exception/LinuxCXX.shtml](http://netlab.ru.is/exception/LinuxCXX.shtml)

Linux kernel factory (the hot core revealed )
[http://lug.oregonstate.edu/projects/kernelmap/map.php](http://lug.oregonstate.edu/projects/kernelmap/map.php)

I collected these links from my [super chaotic kernel page...]("http://www.futuredesktop.org/gen_index.html#kernel")  BE WARNED !!

Other importante programming [resources....]("http://home.online.no/%7Eosmoma/opportunities.html")

---

### Post by samjh on 2007-04-28
> **JediSpam said:**
> I am currently a Computer Engineer major and i'm wondering if Driver Development is what I should focus on. I'm interested in drivers and how they work and make hardware efficient. What languages should I focus on? I just finished Computer Science 3 in college and i'm pretty good at c++/java

Study C and C++.

If you're interested in portable devices, like mobile phones, PDAs, etc., Java is an excellent choice.  But learn C first.

---

### Post by rickardg on 2007-04-29
> **moma said:**
> Linux device drivers and modules (as the kernel itself) are written in C language.


Online book: Linux Device Drivers
[http://www.xml.com/ldd/chapter/book/index.html](http://www.xml.com/ldd/chapter/book/index.html) but the [3.ed]("http://amazon.com/s/ref=nb_ss_gw/103-9189315-6600663?url=search-alias%3Daps&field-keywords=linux+kernel+&Go.x=0&Go.y=0&Go=Go") is more up to date.



Do you mean [this edition of Linux Device Drivers]("http://lwn.net/Kernel/LDD3/")?
;-)

Oh, and my guess is that C and a smattering of assembler would be perfect for kernel hacking  (not that I've tried it myself but I'm sure I'll be flamed if I'm wrong...)

---

### Post by moma on 2007-04-29
> **rickardg said:**
> Do you mean [this edition of Linux Device Drivers]("http://lwn.net/Kernel/LDD3/")?

Yes I do.
Great link :-) 
The Device Driver Kit has propably the same version (in its /ldd folder)

---

### Post by JediSpam on 2007-04-30
alright cool. everyone has told me to learn C and i'm going to focus on it

---

### Post by Caly08 on 2008-09-23
hello,

I'm a Kenyan and have recently witched from XP to Ubuntu.  I'm unable to connect to the internet using my GSM modem.  My machine does not recognize the device.  The device is supplied with window XP drivers only.

Where can I get drivers and software to drive it or who can develop drivers for it?

Yours Caly08.
[IMG]file:///media/PAUL/Image003.jpg[/IMG]
[IMG]file:///media/PAUL/Image004.jpg[/IMG]
attached above is pictures of the device it is supplied by Safaricom Kenya Ltd.

---

### Post by newbuntuxx on 2008-09-23
> **Caly08 said:**
> hello,

I'm a Kenyan and have recently witched from XP to Ubuntu.  I'm unable to connect to the internet using my GSM modem.  My machine does not recognize the device.  The device is supplied with window XP drivers only.

Where can I get drivers and software to drive it or who can develop drivers for it?

Yours Caly08.
[IMG]file:///media/PAUL/Image003.jpg[/IMG]
[IMG]file:///media/PAUL/Image004.jpg[/IMG]
attached above is pictures of the device it is supplied by Safaricom Kenya Ltd.

You need to post this in the absolute beginners forum to get an answer:

[http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326)

---

### Post by Gurmeet Singh on 2011-12-09
Hello,
I have worked in windows environment in VC++/MFC for managing devices like (port communication, Printing on printer from application and also experience of sending data directly to printer from my application etc). Now I want to develope a printer driver on Ubuntu 11.10 (Oneiric ocelot). I am new to linux. Please guide me **how to start with?** like tutorial link, books etc and most important **which Device Driver kit will be better for developing a printer driver?**

Thanks.

---

### Post by gnometorule on 2011-12-09
@moma: I am just beginning to read LDD (3rd edition). As it's based on the 2.6.10 kernel, do you happen to know of a page keeping track of necessary changes? (I'll work on 2.6.31 with it) I realize their O'Reilly page has a kernel change log (maintained by Colbert) until sometime in 2009, but I don't think it's translated into code changes of the book.

---

### Post by nothingspecial on 2011-12-09
Rather than bumping a thread that is almost 5 years old, please start a new one.

Closed.

---

