---
title: "LibreOffice Greying out as Ubuntu used one core 100% and the other 7 remain idle"
date: 2016-02-09
forum: New to Ubuntu
---

### Post by dunbrokin on 2016-02-09
I am not sure if this is hardware or Ubuntu problem or LibreOffice problem.

There are 8 cores in my machine. I am on Ubuntu 15.10 and LibreOffice 5.0.2.2. LO frequently greys out on me and when I check the system monitor, I find that one of the cores is 100% occupied and the rest are practically idle. When I look under processes, LO can be using 400+ Mib...which should not be a problem as I have 2.5G of memory. Nonetheless, LO stays frozen in grey for ages. I am on the default memory allocation as given by LO in Tools/Options/Memory and changing that allocation seems to make little difference as far as I can see.....though I have not tried on Ubuntu 15.10...as it made little difference on previous Ubuntus. I have tried overclocking but that does not help either.

Any suggestions would be greatly appreciated.

---

### Post by leunam12 on 2016-02-09
Have you tried another office suite?

---

### Post by dunbrokin on 2016-02-09
No, I have not.

---

### Post by QIII on 2016-02-09
Trying another office suite does not solve the issue with LibreOffice.  That's avoidance, not a solution.  Let's help the OP with LibreOffice, not go on a tangent.

Thanks.

---

### Post by dunbrokin on 2016-02-09
Go raibh maith agat!

---

### Post by QIII on 2016-02-09
Tá fáilte romhat!

But this is an English-speaking forum.  Besides, most of the Irish I know is not fit for polite company.

---

### Post by grahammechanical on 2016-02-09
It is a peculiarity of Libreoffice 5. I am getting it on xenial xerus (16.04 development branch) on a machine with a 2 core CPU, 1GB RAM and an Nvidia GT220 with 1GB video memory. It is far away from being a high spec machine. But I never saw this effect with Liberoffice 4.

I have system load indicator installed and I can see in the app indicator what is happening to my system resources and this happens with very little CPU activity or disk activity and with only 500MB or there abouts of RAM being used. It happens with large documents of about 100 pages or more.

The Find function is a lot slower than it was with Libreoffice 4.

Regards.

---

### Post by leunam12 on 2016-02-10
> **dunbrokin said:**
> No, I have not.Then, go ahead and try another one. There are several too choose from.

---

### Post by kurt18947 on 2016-02-10
> **grahammechanical said:**
> It is a peculiarity of Libreoffice 5. I am getting it on xenial xerus (16.04 development branch) on a machine with a 2 core CPU, 1GB RAM and an Nvidia GT220 with 1GB video memory. It is far away from being a high spec machine. But I never saw this effect with Liberoffice 4.

I have system load indicator installed and I can see in the app indicator what is happening to my system resources and this happens with very little CPU activity or disk activity and with only 500MB or there abouts of RAM being used. It happens with large documents of about 100 pages or more.

The Find function is a lot slower than it was with Libreoffice 4.

Regards.

I've been running L.O. 5 since it was released on several installs, installed via PPA and part of 16.04. I've not seen that behavior, I wonder what triggers it.

---

### Post by vasa1 on 2016-02-10
> **dunbrokin said:**
> I am not sure if this is hardware or Ubuntu problem or LibreOffice problem.

There are 8 cores in my machine. I am on Ubuntu 15.10 and LibreOffice 5.0.2.2. LO frequently greys out on me and when I check the system monitor, I find that one of the cores is 100% occupied and the rest are practically idle. When I look under processes, LO can be using 400+ Mib...which should not be a problem as I have 2.5G of memory. Nonetheless, LO stays frozen in grey for ages. I am on the default memory allocation as given by LO in Tools/Options/Memory and changing that allocation seems to make little difference as far as I can see.....though I have not tried on Ubuntu 15.10...as it made little difference on previous Ubuntus. I have tried overclocking but that does not help either.

Any suggestions would be greatly appreciated.

Can you correlate the greying out with anything? Size of file? Calc, Writer, Impress, etc? Whether it's reproducible by a particular action?

I don't know what "overclocking" does, but doesn't that set your experience apart from the "average" user?

****************

@kurt18947,

Whats's the oldest hardware you feel that can run LO5 decently?

---

### Post by kurt18947 on 2016-02-11
> @kurt18947,

Whats's the oldest hardware you feel that can run LO5 decently?                                                                                              [INDENT]                                      Last edited by vasa1; 10 Hours Ago at 09:53 PM.                                               

[/INDENT]

I don't really know. I did an Ebay 'hardware refresh' recently hoping to have 'conventional BIOS' machines for a few years 'til UEFI becomes more familiar/stable. The oldest machine I use regularly is a Thinkpad X61 core2 duo w/ 4 GB. RAM. It runs L.O. 5 fine.

---

### Post by vasa1 on 2016-02-11
> **kurt18947 said:**
> [/INDENT]

I don't really know. I did an Ebay 'hardware refresh' recently hoping to have 'conventional BIOS' machines for a few years 'til UEFI becomes more familiar/stable. The oldest machine I use regularly is a Thinkpad X61 core2 duo w/ 4 GB. RAM. It runs L.O. 5 fine.
Thanks for that! I've just installed Version: 5.0.4.2 and it's working fine on my Dell 1545 Core2 Duo as well.

I always turn off anti-aliasing, BTW. I sort of remember it being to blame for high CPU usage.

Oh, and because I don't have a GPU, I also turn off hardware acceleration.

---

### Post by maglin2 on 2016-02-12
I've never seen this behaviour either. On my 2.2GHz dual core machine running 15.10 and LO5 both cores seem to load evenly.


I recall reading that having the 'Use a Java runtime environment' box in LO Tools-Options-Advanced ticked (with Java installed) can affect LO performance.

---

### Post by vasa1 on 2016-02-12
> **maglin2 said:**
> ...
I recall reading that having the 'Use a Java runtime environment' box in LO Tools-Options-Advanced ticked (with Java installed) can affect LO performance.
I think keeping JRE ticked is necessary for people who use macros or LibreOffice Base. The rest of us can keep it unchecked.

---

### Post by maglin2 on 2016-02-12
> **vasa1 said:**
> I think keeping JRE ticked is necessary for people who use macros or LibreOffice Base. The rest of us can keep it unchecked.

A bit off topic, but I found I needed LO Base to get Mailmerge to work. I've never been keen on having a JRE installed, so I installed base with no-install-recommends and got Base working to support Mailmerge without java. I gather that LO have been progressively decoupling it from Java where possible.

---

### Post by vasa1 on 2016-02-12
> **maglin2 said:**
> ... I gather that LO have been progressively decoupling it from Java where possible.That was their stated objective according to this oldish answer: [https://ask.libreoffice.org/en/question/18322/is-there-any-plan-to-ditch-java-in-the-future-and-use-only-cc-code/?answer=18368#post-id-18368](https://ask.libreoffice.org/en/question/18322/is-there-any-plan-to-ditch-java-in-the-future-and-use-only-cc-code/?answer=18368#post-id-18368)

---

