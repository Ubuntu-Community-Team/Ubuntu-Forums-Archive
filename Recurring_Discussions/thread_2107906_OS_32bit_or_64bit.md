---
title: "OS 32bit or 64bit"
date: 2013-01-23
forum: Recurring Discussions
---

### Post by lelovely7315 on 2013-01-23
Hi there, I hope this is a simple question to answer. I am running Ubuntu 12.04 (LTS) 32bit. This is the OS I had downloaded before I upgraded my computer. I see that there is also a 64bit version, what is the difference between the 32bit and the 64bit versions. And my question is: should I upgrade to the 64bit? Also what advantages is there between 32bit and 64bit? So far this Ubuntu 12.04 (LTS) 32bit is working great!!!
 Thanks Larry :D

---

### Post by 3rdalbum on 2013-01-23
Certain intensive calculations such as video encoding, work somewhat faster on 64-bit. You can also natively handle 4GiB of RAM or more on 64-bit.

Of course, 64-bit operating systems only work on 64-bit CPUs. Look up your CPU on Wikipedia and it will say if it is 64-bit or not. Most in the last six years are.

You would have to reinstall Ubuntu to get 64-bit; not worth it in my opinion, just install 64-bit the next time you do a clean install of Ubuntu.

---

### Post by omeomi on 2013-01-23
> should I upgrade to the 64bit?

If you don't have 4GiB RAM or more installed there is no real need to change to 64bit.

---

### Post by ibjsb4 on 2013-01-23
I just love this question :)  32 bit is just fine ..

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=32+bit+vs+64+bit&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=32+bit+vs+64+bit&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by smitty4478 on 2013-01-23
I don't think the upgrade would be worth having to reinstall, I agree with 3rdalbum...

---

### Post by Paqman on 2013-01-23
> **omeomi said:**
> If you don't have 4GiB RAM or more installed there is no real need to change to 64bit.

This is not true. As well as being able to handle more memory, 64-bit is significantly faster at any kind of hardcore number crunching (video or audio encoding, encryption, compression, etc).

There's no reason to throttle a 64-bit chip down to 32-bit speeds.

---

### Post by oldfred on 2013-01-23
How much RAM? Most say unless you have 3GB or more the 32bit is fine.

       Ubuntu 12.10: 32-bit vs. 64-bit Linux Performance
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_3264&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_3264&num=1)
Assuming your hardware is x86_64 capable (basically any modern Intel/AMD CPU) and have at least 2GB of RAM, you really should be running the 64-bit version.
Essentially says if you can use the 64bit kernel you should.April 2011
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
Ubuntu 32-bit, 32-bit PAE, 64-bit Kernel Benchmarks Dec 2009
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)
Linus does not like PAE or 32 bit.
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/)

---

### Post by NilPointer on 2013-01-25
> **3rdalbum said:**
> You can also natively handle 4GiB of RAM or more on 64-bit.

I have 8 GiB of RAM and 32-bit PAE kernel, which handles entire RAM. PAE allows up to 64 GiBs of RAM. So, primary advantage of 64-bit OS is ability to allocate more than 2 GiB of RAM to single process. However, some software can be incompatible with 64-bit OS. And that's my primary reason to use 32-bit OS.

---

### Post by Paqman on 2013-01-25
> **NilPointer said:**
> However, some software can be incompatible with 64-bit OS.

Maybe a few years ago, but that's not a real problem any more. I've been using 64-bit exclusively for years and can't remember the last time I found a 32-bit only application. And even if I did, it can still run on 64-bit.

---

### Post by oldos2er on 2013-01-25
> **NilPointer said:**
>  some software can be incompatible with 64-bit OS.

What software?

---

### Post by oldos2er on 2013-01-25
> **omeomi said:**
> If you don't have 4GiB RAM or more installed there is no real need to change to 64bit.

Unless you want to speed up CPU-intensive tasks such as video encoding. Doing that on my 64-bit system with 2GB RAM was measurably faster (10 to 15 mins. faster) than it was on 32-bit.

---

### Post by NilPointer on 2013-01-25
> **oldos2er said:**
> What software?

Well, I had to install Ubuntu 64-bit on my laptop (because proprietary drivers were available only for 64-bit variant), and to be honest, I didn't run into serious problems so far. But when I tried to run one of my own programs, that depended on a 32-bit only library, I got error:

```
wrong elf class elfclass32
```

Eventually, I downloaded 64-bit version of same library and it worked, but I guess there may be some problems running some exotic old software, or proprietary software that doesn't come with source. For example, I wonder if ports of old games (such as Unreal Tournament/Unreal Tournament 2004) still work on 64-bit Linuxes.

---

### Post by dannyboy79 on 2013-01-25
if you have any recent CPU, within the last 5 years, and if your current install isn't highly customized, then I would definitely install the 64bit version.

---

### Post by lelovely7315 on 2013-01-26
Hi everyone, thanks to all of you for the info. I have a 64bit CPU, and 8gb of ram that can be upgraded to 16gb. This is my new system that I built 3 weeks ago. I will leave it this way for now.    Thanks Larry :D

---

### Post by BlinkinCat on 2013-01-26
> **lelovely7315 said:**
> Hi everyone, thanks to all of you for the info. I have a 64bit CPU, and 8gb of ram that can be upgraded to 16gb. This is my new system that I built 3 weeks ago. I will leave it this way for now.    Thanks Larry :D

Hi,

In my opinion 8gb of ram is ample - :)

---

### Post by dannyboy79 on 2013-01-26
> **lelovely7315 said:**
> Hi everyone, thanks to all of you for the info. I have a 64bit CPU, and 8gb of ram that can be upgraded to 16gb. This is my new system that I built 3 weeks ago. I will leave it this way for now.    Thanks Larry :D
if you aren't using the PAE kernel, you're only getting use of 3GB of RAM

---

### Post by Blackbug on 2013-01-29
Hi,

I have recently switched to corei5 from amd turion.
I am confused in choosing the ubuntu version, i386 or amd64 on new corei5 machine.
corei5 is a 64bit processor but i have read alot that i386 version should be used on intel machines.

Any specific reason why to choose i386 even when processor is 64 bit?

Thanks.

KK

---

### Post by howefield on 2013-01-29
Both versions will work on your machine perfectly well.

The naming convention is a historical thing, amd64 version is suitable for both intel and amd machines.

---

### Post by ibjsb4 on 2013-01-29
> amd64 version is suitable for both 32 and 64 bit machines.

Think you made a typo.

---

### Post by howefield on 2013-01-29
Indeed, thanks for the correction :)

---

### Post by mörgæs on 2013-01-29
Threads merged.

---

### Post by matt_symes on 2013-01-29
Hi
 
> **Paqman said:**
> Maybe a few years ago, but that's not a real problem any more. I've been using 64-bit exclusively for years and can't remember the last time I found a 32-bit only application. And even if I did, it can still run on 64-bit.
 
^^^ This.
 
Personally i would upgrade to 64 bit straight away for the reasons given in this thread, but that is just me.
 
Kind regards

---

