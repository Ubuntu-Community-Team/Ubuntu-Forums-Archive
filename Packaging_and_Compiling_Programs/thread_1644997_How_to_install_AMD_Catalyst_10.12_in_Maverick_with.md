---
title: "How to install AMD Catalyst 10.12 in Maverick with Kernel 2.6.36"
date: 2010-12-14
forum: Packaging and Compiling Programs
---

### Post by HX_unbanned on 2010-12-14
Good morning!

Is there any way to do it or I am forced to choose - 
Use better kernel ;
or
Use better video card drivers ?

I would be glad to have both for my Radeon HD 5750 VGA ... :popcorn:

Related links: [http://www.phoronix.com/forums/showthread.php?t=27750](http://www.phoronix.com/forums/showthread.php?t=27750)

---

### Post by P-Geist on 2010-12-14
I just turned my PC on for the first time and it started installing, i would personally update my drivers to the latest from the ATI site.

Contact me if you need anymore help :)

P-Geist

---

### Post by HX_unbanned on 2010-12-14
> **P-Geist said:**
> I just turned my PC on for the first time and it started installing, i would personally update my drivers to the latest from the ATI site.

Contact me if you need anymore help :)

P-Geist

Sorry, I do not get the point of your text ...

What is the meaning of "I just turned it on for the first time" ?
What is "it" in the sentence "and it started installing" ?
How do you put latest sentence "i would personally update my drivers to the latest from the ATI site" in the whole context?

P.S. There is no ATI site anymore. It is owned by AMD for some time already, my friend ... ;)

--

Again - I already use Kerrnel 2.6.36 on my Ubuntu PC. I want to install AMD Catalyst 10.12, but I cannot because of error(s). Question - Is there any way to install them though????!!!

---

### Post by rodrigosavage on 2010-12-18
Hello! what errors do you get?

I followed:
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx)

and tips on : 
[http://ubuntuforums.org/showthread.php?t=1576383&page=2](http://ubuntuforums.org/showthread.php?t=1576383&page=2)

I don't get error. but the screen loads black when i reboot :(

I am also using 2.6.36 kernel and trying to install [B]Catalyst 10.12

Thanks!
[/B]

---

### Post by rodrigosavage on 2010-12-20
Problem solve!!
well i read a lot of stuff from everywhere even update the kernel. But the key thing was that my laptop is equip with switchable graphics! and ubuntu got confused.

When i did 

```
$ lspci | grep VGA
```my system would output the information of 2 VGA controllers, Intel, and ATI I noticed that in my xorg.conf, the device driver of ATI was address to intel controller, soo I change it so it would address the ATI controller... but it didn't work.

Sooo, I restart my lap, enter the bios and disable the switchable graphics to discreet.

And it work!! now lspci outputs only the ATI card!!! :)
$ lspci | grep VGA
```

01:00.0 VGA compatible controller: ATI Technologies Inc Madison [Mobility Radeon HD 5000 Series]

```

and magically when I enter ubuntu again catalyst worked!!!

---

