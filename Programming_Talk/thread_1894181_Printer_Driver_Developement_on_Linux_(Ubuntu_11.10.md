---
title: "Printer Driver Developement on Linux (Ubuntu 11.10 )?"
date: 2011-12-12
forum: Programming Talk
---

### Post by Gurmeet Singh on 2011-12-12
Hello,
I have worked in windows environment in VC++/MFC for managing devices like (port communication, Printing on printer from application and also experience of sending data directly to printer from my application etc).** Now I want to develope a printer driver on Ubuntu 11.10 (Oneiric ocelot). I am new to linux. Please guide me how to start with?** like tutorial link, books etc and most important **which Device Driver kit will be better for developing a printer driver?**
Please help.

Thanks.

---

### Post by JDShu on 2011-12-12
Non proprietary drivers are all in the[ Linux kernel]("http://www.kernel.org/") under the GPL. Downloading it and reading the code would probably be a good way to start.

---

### Post by Gurmeet Singh on 2011-12-12
Thanks JDShu for your valuable response.
Please let me know one thing **which compiler or DDK will be better for device driver developement?**
Actually i am totally new to linux so feeling difficulty.
Post any link which will be better for beginer.
Thanks in advance.

---

### Post by JDShu on 2011-12-12
[http://lwn.net/Kernel/LDD3/](http://lwn.net/Kernel/LDD3/)

For now only gcc can compile the Linux kernel.

As far as I know, Linux developers don't use device driver kits. Use a text editor ;) There do appear to be various debuggers though. They may require knowing gdb as a prerequisite.

---

### Post by Gurmeet Singh on 2011-12-12
Thanks !!

I am using gcc and gedit for witing small code... Even I tried my hands with gdb tooo.

Now, the question arises about a particular link that I found while searching for printer driver development.

[http://www.kroah.com/log/linux/ddk.html](http://www.kroah.com/log/linux/ddk.html)

[http://www.cups.org/documentation.php/doc-other/cupsddk.html#1_1](http://www.cups.org/documentation.php/doc-other/cupsddk.html#1_1)

Hope for expert guidance soon.

---

### Post by Gurmeet Singh on 2011-12-13
> Thanks !!

I am using gcc and gedit for witing small code... Even I tried my hands with gdb tooo.

Now, the question arises about a particular link that I found while searching for printer driver development.

[http://www.kroah.com/log/linux/ddk.html](http://www.kroah.com/log/linux/ddk.html)

[http://www.cups.org/documentation.ph...psddk.html#1_1]("http://www.cups.org/documentation.php/doc-other/cupsddk.html#1_1")

Hope for expert guidance soon.

Please help me.
I am still waiting for any response from experts.
thanks.

---

### Post by Zugzwang on 2011-12-13
Gurmeet Singh, I think that you found all the information that you need by yourself. I would say that your best bet is to follow the CUPS driver development guide, as printer drivers are a bit special in Linux. As far as I know, they are seldomly in the kernel, so the "general" driver development guides for Linux might not apply. The link to the CUPS page that you found should tell you more about this.

Since you say that are new to Linux, consider also reading the CUPS wikipedia page: [http://en.wikipedia.org/wiki/CUPS](http://en.wikipedia.org/wiki/CUPS)

---

### Post by Gurmeet Singh on 2011-12-15
Thanks all for your guidenance.
I will contact with you again if needed.
Thanks:)

---

### Post by Petrolea on 2011-12-16
> **Gurmeet Singh said:**
> Thanks !!

I am using gcc and gedit for witing small code... Even I tried my hands with gdb tooo.

Now, the question arises about a particular link that I found while searching for printer driver development.

[http://www.kroah.com/log/linux/ddk.html](http://www.kroah.com/log/linux/ddk.html)

[http://www.cups.org/documentation.php/doc-other/cupsddk.html#1_1](http://www.cups.org/documentation.php/doc-other/cupsddk.html#1_1)

Hope for expert guidance soon.

I think the first link might be outdated, since that kit is for older kernel.

The second link looks good, I think it might be a good one to start with.

---

### Post by Gurmeet Singh on 2011-12-20
Thanks all,

I am able to compile and load the kernel module.
Now i want to start actual printer driver developement.
can anyone please provide me basic information to start with?

Thanks.:confused:

---

### Post by Zugzwang on 2011-12-20
> **Gurmeet Singh said:**
> can anyone please provide me basic information to start with?

So did you read [http://www.cups.org/documentation.php/doc-other/cupsddk.html#1_1?](http://www.cups.org/documentation.php/doc-other/cupsddk.html#1_1?) Any questions of problems with this documentation?

---

### Post by Gurmeet Singh on 2011-12-20
Hello Experts,

I am following the same link for developement and found many helpful clues.
I will come again for expert guide if needed.
Thanks this time:)

---

### Post by Petrolea on 2011-12-20
> **Gurmeet Singh said:**
> Hello Experts,

I am following the same link for developement and found many helpful clues.
I will come again for expert guide if needed.
Thanks this time:)

It's a good idea to follow that guide, it's well written and easy to understand.

---

