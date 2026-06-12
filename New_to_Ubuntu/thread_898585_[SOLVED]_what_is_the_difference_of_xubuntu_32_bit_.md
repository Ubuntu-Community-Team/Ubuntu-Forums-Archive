---
title: "[SOLVED] what is the difference of xubuntu 32 bit to xubuntu 64 bit?"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by mdialogo on 2008-08-23
what is the difference of xubuntu 32 bit to xubuntu 64 bit? and how can i know if my xubuntu is 32 or 64 bit? thanks...

---

### Post by WRDN on 2008-08-23
To find whether you are using a 32bit or 64bit OS, type the following in the Terminal:

```
uname -a
```

The output may look something like this:

> Linux Desktop 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 **i686** GNU/Linux

i686 is 32bit, whilst x86-64 is 64bit.

---

### Post by Joeb454 on 2008-08-23
An easier option would be to run ```
uname -m
``` from the terminal :)

Chances are you'll be running 32 bit :)

---

### Post by SunnyRabbiera on 2008-08-23
The difference is one is made for 64bit architectures and the other is made for 32, though its possible to run a 32bit kernel in a 64bit system (but not vice versa)
Its typically better to run the 32bit version, as its easier to get media and such running in it.
The biggest issues of a 64bit kernel is flash and java, the java issue will probably be fixed by next year with any luck while flash will be fixed on the eve of doomsday (as adobe sucks)

---

### Post by menayak on 2008-08-23
hi 

i like your site
and its so good content
it good ubuntu
curt smith

  [NewHampshireDrugAddiction]("http://www.drugaddiction.net/new-hampshire")

---

### Post by SunnyRabbiera on 2008-08-23
nevermind

---

### Post by Joeb454 on 2008-08-23
> **SunnyRabbiera said:**
> nevermind

:lolflag: Oh and SunnyRabiera - I've heard rumor of some 64 bit builds of Flash 10 internally...

---

### Post by mdialogo on 2008-08-23
could you also reply to my other posts that still unanswered? they are already in the 2nd page of the forum display and wait long and keep on checking if theres a reply but no avail. can you please look for it. thanks in advance...

---

### Post by Paqman on 2008-08-23
> **SunnyRabbiera said:**
> 
The biggest issues of a 64bit kernel is flash and java, the java issue will probably be fixed by next year with any luck while flash will be fixed on the eve of doomsday (as adobe sucks)

As far as the end-user user is concerned, both are fixed already. Installing ubuntu-restricted-extras installs both of the above automatically, including any wrappers they need to work properly.

I've been using 64-bit since I switched to Linux, and it's gone from a bit of a hassle to complete par with 32-bit. There really is no reason left to not make the switch IMO.

---

### Post by Marcial Contreras on 2008-08-23
> **SunnyRabbiera said:**
> The difference is one is made for 64bit architectures and the other is made for 32, though its possible to run a 32bit kernel in a 64bit system (but not vice versa)
Its typically better to run the 32bit version, as its easier to get media and such running in it.

Do you think that if I change from 64bit ubuntu to 32 it will run faster or better? I have a HPpavilion dv5000 with a Turion64, 512 of ram and a shitty ati radeon200m.

I ask because I think my ubuntu is running slower than my sister's (and she has an even older and slower pc).

Thanks in advance.

---

### Post by WRDN on 2008-08-23
> **Marcial Contreras said:**
> Do you think that if I change from 64bit ubuntu to 32 it will run faster or better? I have a HPpavilion dv5000 with a Turion64, 512 of ram and a shitty ati radeon200m.

I ask because I think my ubuntu is running slower than my sister's (and she has an even older and slower pc).

Thanks in advance.

For the majority of mainstream applications used by users in general (such as word processor, web browser, media player etc), you won't see a noticeable speed increase for these applications. 64bit is great if you compile programs, and do lots of number crunching, as a 64bit OS can perform these tasks faster than a 32bit OS (from what I've heard).

---

### Post by Liviu-Theodor on 2008-09-02
> **Marcial Contreras said:**
> Do you think that if I change from 64bit ubuntu to 32 it will run faster or better? I have a HPpavilion dv5000 with a Turion64, 512 of ram and a shitty ati radeon200m.

I ask because I think my ubuntu is running slower than my sister's (and she has an even older and slower pc).

Thanks in advance.

If you have less than 1 GB of memory, you should stick with the 32 bit variant. And a little piece of advice: a little bit of memory works wonders, even 256 MB of RAM more than what you have will visibly increase the performance of your computer. I managed to install ubuntu (standard, not xubuntu) even on machines with 128 MB of RAM (it requires "just" 384), but works very slowly, and I have seen big differences between 512 MB and 1 GB of RAM.

---

