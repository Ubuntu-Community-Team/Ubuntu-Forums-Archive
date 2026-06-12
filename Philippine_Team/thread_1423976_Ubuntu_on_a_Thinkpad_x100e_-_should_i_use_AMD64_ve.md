---
title: "Ubuntu on a Thinkpad x100e - should i use AMD64 version?"
date: 2010-03-07
forum: Philippine Team
---

### Post by businessgeeks on 2010-03-07
I just bought a THinkpad x100e. and im trying to research on how to best install ubuntu on it. I've been reading that I should use the AMD64 version. Im just not entirely sure about it. can anyone help me out?

---

### Post by sikander3786 on 2010-03-07
> **businessgeeks said:**
> I just bought a THinkpad x100e. and im trying to research on how to best install ubuntu on it. I've been reading that I should use the AMD64 version. Im just not entirely sure about it. can anyone help me out?

As the Lenovo Website states it has Windows 7 64-Bit installed by default.
So you should be able to run 64-bit Ubuntu. You might be interested in Ubuntu Netbook Remix. [http://www.ubuntu.com/GetUbuntu/download-netbook](http://www.ubuntu.com/GetUbuntu/download-netbook)

Regards.

Sikander.

---

### Post by jepong on 2010-03-08
is there a 64-bit UNR?

---

### Post by sikander3786 on 2010-03-08
> **jepong said:**
> is there a 64-bit UNR?

I don't think so. I couldn't find it on the Ubuntu Website. I think you should go with the normal UNR Edition.

---

### Post by businessgeeks on 2010-03-09
what are the advantages of using the 64bit version?

---

### Post by loell on 2010-03-09
I'ts an age old question on why 64 is better than 32, [http://en.wikipedia.org/wiki/64-bit]("http://en.wikipedia.org/wiki/64-bit")

bottom line, faster.

---

### Post by businessgeeks on 2010-03-10
I've been hearing about some software not having 64bit versions. Will i be causing problems with my laptop in the long run if i choose to use 32bit version of Ubuntu?

---

### Post by Ravskie on 2010-03-10
> **businessgeeks said:**
> I've been hearing about some software not having 64bit versions. Will i be causing problems with my laptop in the long run if i choose to use 32bit version of Ubuntu?


You will have no problem as long as you use the right version...... !

---

### Post by zintinio on 2010-03-20
I have used the amd64 version as well as the i386, and so far the amd64 version has not only proven to be more of a hassle to use. Many programs don't have 64-bit equivalents and there aren't many benefits to using the 64-bit version, unless you have >4gb RAM. Stick with x86

---

### Post by juliobahar on 2011-06-30
I have a Lenovo Thinkpad X100e as well. I was happy with ubuntu 10.10 64-bit, although the performance was not as sleek as it should have been. Since I upgraded to Ubuntu 11.04 64-bit, I'm suffering of terrible slow stuttering performance.

I really don't know whether it is the graphics card or the whole system's fault. I'm still on the case trying to figure out how to tackle the issue.

---

### Post by tech-hero on 2011-06-30
Stick 32-bit if you want stability. Based on the specs i've seen for your unit, it's less likely to have more than 4GB of memory. You won't be able to utilize the full capacity of your device with that.

---

### Post by juliobahar on 2011-07-01
> **tech-hero said:**
> Stick 32-bit if you want stability. Based on the specs i've seen for your unit, it's less likely to have more than 4GB of memory. You won't be able to utilize the full capacity of your device with that.

Well my system is quite stable, alright!!! with either versions of ubuntu. The only issue is the SLOWNESS, boy, I would sometime want to slam the lappy against the wall. it wasn't like this before, btw.

---

### Post by Guitar John on 2011-07-01
I have the x100e with the [NV-40]("http://www.thinkwiki.org/wiki/AMD_Athlon_Neo") processor.  The only problems that I had with the 64 bit version was tearing on some web pages with flash content.  Not an issue with the 32 bit version.

FWIW, I had a lot of problems with Ubuntu 11.04 crashing on start-up unless I booted to Gnome Classic No Effects.  I finally switched to Kubuntu 11.04 and things are working well.

Enjoy the new ThinkPad.  I like mine now that things are sorted out.

---

### Post by juliobahar on 2011-07-01
> **Guitar John said:**
> I have the x100e with the [NV-40]("http://www.thinkwiki.org/wiki/AMD_Athlon_Neo") processor.  The only problems that I had with the 64 bit version was tearing on some web pages with flash content.  Not an issue with the 32 bit version.

FWIW, I had a lot of problems with Ubuntu 11.04 crashing on start-up unless I booted to Gnome Classic No Effects.  I finally switched to Kubuntu 11.04 and things are working well.

Enjoy the new ThinkPad.  I like mine now that things are sorted out.

Nice to see you here as well, John. So can you confirm that 11.04 Kubuntu 32-bit is better for your thinkpad x100e MV-40. Coz if it is I will immediately switch to it.

---

### Post by tech-hero on 2011-07-03
yeah. slowness would be the issue. 64-bit architecture tend to consume more memory than 32-bit. so if you don't have at least 4GB Ram, it would be an issue.

---

### Post by juliobahar on 2011-07-04
> **tech-hero said:**
> yeah. slowness would be the issue. 64-bit architecture tend to consume more memory than 32-bit. so if you don't have at least 4GB Ram, it would be an issue.

Well, how can you explain it that 64-bit ubuntu 10.10 was much faster than 64-bit ubuntu 11.04. And I do have 4GB RAM.

I think I got something here. It seems that gnome/unity is the issue with our Thinkpad X100e. I may confirm that is it related to unity regardless whether with compiz or not (i.e. not a graphic's issue)- The whole OS is hogging on the CPU threads

I've tried the following and they are much faster than unity:

1- Kubuntu 11.04 64-bit
2- Ubuntu 10.10 64-bit
3- openSUSE with gnome3 (?32bit)
4- Fedora 15 64-bit

Oh boy, was a busy week for me. I hope our problem is solved in the next release of ubuntu with the fully fledged gnome3.

---

### Post by tech-hero on 2011-07-04
> **juliobahar said:**
> Well, how can you explain it that 64-bit ubuntu 10.10 was much faster than 64-bit ubuntu 11.04. And I do have 4GB RAM.

I think I got something here. It seems that gnome/unity is the issue with our Thinkpad X100e. I may confirm that is it related to unity regardless whether with compiz or not (i.e. not a graphic's issue)- The whole OS is hogging on the CPU threads

I've tried the following and they are much faster than unity:

1- Kubuntu 11.04 64-bit
2- Ubuntu 10.10 64-bit
3- openSUSE with gnome3 (?32bit)
4- Fedora 15 64-bit

Oh boy, was a busy week for me. I hope our problem is solved in the next release of ubuntu with the fully fledged gnome3.
Well, in case of 64-bit vs. 64-bit, it might be the software that's running that makes the other OS slower. Basically, from what i have observed in Ubuntu 11.04, it provides more eye candies, therefore expect it to consume more resources. You may be right. It may be about unity.

---

### Post by jvgeli on 2011-07-06
Had the same issue in lag with Natty. Apparently Unity has some issues with ATI Graphic cards. I am assuming you have an ATI GPU since it is AMD but please let me know if I am wrong. With that, and Natty is simply too boring for me, I switced back to Maverick. ATI graphics now work well. Also, if you insist on using Natty you might want to use the open drivers rather than fglrx that ubuntu wants you to use. Just a thought. Good luck!

---

### Post by juliobahar on 2011-07-08
> **jvgeli said:**
> Had the same issue in lag with Natty. Apparently Unity has some issues with ATI Graphic cards. I am assuming you have an ATI GPU since it is AMD but please let me know if I am wrong. With that, and Natty is simply too boring for me, I switced back to Maverick. ATI graphics now work well. Also, if you insist on using Natty you might want to use the open drivers rather than fglrx that ubuntu wants you to use. Just a thought. Good luck!

You are absolutely right. The whole fault was that of unity's inconsistency with the proprietary ATI driver.

Honestly I did think of reverting back to ubuntu 10.10, but I decided to move on and try other distros. And I was successful with Fedora 15 (gnome shell) and openSuSE 11.4 (gnome 2.6) both 64-bit.

Thank you for your considerate reply.

---

