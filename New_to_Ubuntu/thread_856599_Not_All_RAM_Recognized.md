---
title: "Not All RAM Recognized"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by woody22075 on 2008-07-11
I have Ubuntu 8.04 on an HP 6715b.  I just upgraded the RAM to 4 gigs (2x2).  When I check System Monitor, it states "Memory: 2.8 GiB"  How do I get Hardy to recognize all 4 gigs?

Thank you for any assistance.

---

### Post by [Jaguar] on 2008-07-11
I suppose you're using a 32Bits O.S.?
  For 2.8GB+ you need a 64Bits O.S.

---

### Post by dca on 2008-07-11
Are you sure, check this out:
 
[http://www.vistaclues.com/reader-question-maximum-memory-in-32-bit-windows-vista/](http://www.vistaclues.com/reader-question-maximum-memory-in-32-bit-windows-vista/)
 
I know they use Vista as a reference but it does go a little into detail about mem allocation and possible explanations...

---

### Post by WRDN on 2008-07-11
You can make the 32 bit OS recognise the full 4Gb RAM by recompiling the kernel with the relevant options enabled.
Read this [Kernel Compilation]("http://ubuntuforums.org/showthread.php?t=56835&highlight=kernel") post and [this]("http://ubuntuforums.org/showpost.php?p=5254634&postcount=7") for more information :)

---

### Post by Kevbert on 2008-07-11
Are you using Hardy 64 bit ?  The processor is a 64 bir AMD Turion which should see your memory.  There may be a setting in bios which you can select (it may be something like 'use memory hole' or something like that).  The specs suggest that it uses shared memory (UMA) so it may mean you see less than the full 4Gb as some may be used as video memory (but I may be wrong).
You can also use the following command in terminal
```
free -m
``` which will display how much memory Hardy thinks you have.
The other thing to check is that the memory is properly seated in its sockets and to perform a memtest via the grub bootmenu.  If you get any errors either the memory needs refitting or is faulty.  The difference between the POST memory test (when you turn on the laptop) and memtest is that the POST test is just a very quick test which does not check the memory completely (and its still cold) while the memtest is an extensive test which will find all errors (and the memory gets heated up).  It's possible to run Windows with memory problems and get away with them (but you may get the occasional unexplained crash).

---

### Post by [Jaguar] on 2008-07-11
> **WRDN said:**
> You can make the 32 bit OS recognise the full 4Gb RAM by recompiling the kernel with the relevant options enabled.
Read this [Kernel Compilation]("http://ubuntuforums.org/showthread.php?t=56835&highlight=kernel") post and [this]("http://ubuntuforums.org/showpost.php?p=5254634&postcount=7") for more information :)

(isnt LOT easier and better install a 64 bits O.S.?)

---

### Post by zgornel on 2008-07-11
Actually for recompiling the kernel you have to write a few commands and that's it. Furthermore, nothing in the installation will change or break.

---

### Post by neurostu on 2008-07-11
So even if you recompile the kernel you will NOT have all 4gb available to you.

The 32bit addressing in the 32bit OS has access to 4gb's of memory.  However several Megabytes of addressing are reserved for system purposes and are not available for physical memory.

Also the memory on your video card is included in the 32bits of memory addresses so every megabyte of video memory you have decreases the number of megabytes possible to have recognized in your RAM.

I have two machines both running Ubuntu32 bit with 4gb of ram installed. Both machines can only use about 3gb of that ram.  

If you want all 4gb of ram available you must install the 64bit os.  The question is... is it more important for you to have all 4gb of ram available or is it more important for things to just work? 

I know several people who claim to have had no problems with the 64bit OS.  I'm not one of them... there tend to be driver or compatability issues that can usually be overcome with a little work... if you really need all 4 gb then reinstall with 64bit... if you want the 4gb just for ego purposes, tell your friends you've got 4gigs and keep your current install.

Unless you're doing some real HEAVY DUTY computations, you'll never see the difference between 2.8gb and 4gb of ram, and even then you would probably do better to upgrade the cpu as well, but I'm talking about doing computations on LARGE amounts of data.

---

### Post by bodhi.zazen on 2008-07-11
To allow your system to use igher ammounts of RAM on a 32 bit CPU all you need is a PAE enabled kernel.

It is very easy to install or compile your own. See there links :

How - to : 
        vor : [http://ubuntuforums.org/showthread.php?t=855511](http://ubuntuforums.org/showthread.php?t=855511)
        Alternate : [http://ubuntuforums.org/showthread.php?t=853678](http://ubuntuforums.org/showthread.php?t=853678)

---

### Post by Inxsible on 2008-07-11
Its funny how many threads I have seen similar to this one, over the last few days.

Everyone is getting more memory than they need and of course the 32 bit OS (which most people use) doesn't see it all. Are we getting to a point, when 64bit will just become the standard ? ;)

---

### Post by jimmy the saint on 2008-07-11
I notice that everyone always jumps to a software solution here, but there is also the possibility of a hardware limitaition.  Some chpsets and MOBOs cannot recognize 4 gigs, even if they say they can.  The first thing I would do is get into BIOS and see if it recognizes all 4 gigs.  If it does, then it is a software issue, if it doesn't, the board itself isn't recognizing the ram, and there is likely nothing you can do that will allow the OS to bypass this.  I, for example, have a GA-945GM-S2 that is advertised for 4gigs, but does not support memory remapping, therefore it decides on its own to reallocate memory it considers to be "excess" to other tasks.  There is apparently no way around this save purchasing better hardware.

---

### Post by bodhi.zazen on 2008-07-11
> **Inxsible said:**
> Everyone is getting more memory than they need and of course the 32 bit OS (which most people use) doesn't see it all. Are we getting to a point, when 64bit will just become the standard ? ;)

Second, yes 64 bit is the way of the future. Is it here yet ? Yes and no.

If I were to buy a new computer, I would buy 64 bit, but that is not the same as saying I am willing to give up on my 32 bit box which is working just fine, thank you very much.

Why should I go buy a 64 bit box ? And if I am going to keep my 32 bit CPU, why not make full use of it ? You can get a lot of performance still out of these "obsolete" 32 bit boxes.

---

### Post by Inxsible on 2008-07-11
> **bodhi.zazen said:**
> Second, yes 64 bit is the way of the future. Is it here yet ? Yes and no.

If I were to buy a new computer, I would buy 64 bit, but that is not the same as saying I am willing to give up on my 32 bit box which is working just fine, thank you very much.

Why should I go buy a 64 bit box ? And if I am going to keep my 32 bit CPU, why not make full use of it ? You can get a lot of performance still out of these "obsolete" 32 bit boxes.
I never meant to say that we get rid of our 32 bit boxes.. I still use one made in 1998. Works great as a triple boot thats listed in my sig.

I was just mentioning that since memory has become so cheap that everyone's getting so much of it...we are probably in the "transition" phase from 32 to 64

---

### Post by bodhi.zazen on 2008-07-11
I agree, we are in transition. 64 bit multicore is "standard" (you can get a 64 bit quad core for $200 US without much effort), IMO, for new rigs, but 32 bit is not yet obsolete and the 64 bit code is not yet complete (many apps do not take full advantage of the hardware ... yet).

---

### Post by neurostu on 2008-07-11
I personally don't understand the reason for the big push to migrate to 64bit.  How many applications exist for end users that actually see a performace boost when more then 4gb of ram are present?

One thing I'd like explained is over the last 5 years computer (IMHO) haven't gotten faster they've gotten slower.  This is totally counter intuitive as CPU speeds have gone up along with RAM and HDD availability? Why is this, bad programming, other reasons?

Sure simply upgrading your system is fun and its I know some people like to brag about their system, but when do upgrades become surperflous as has hit its asymptote.

---

### Post by zgornel on 2008-07-11
The question is not why users buy copious amounts of ram at ridiculously low prices (I myself have maxed out memory in both laptops, for good reasons) but why the PAE is not enable by default in the generic kernel. And as for 64 bit, the more bit involved, the more speed obtained.

---

### Post by sdennie on 2008-07-11
[http://ubuntuforums.org/showthread.php?t=855511](http://ubuntuforums.org/showthread.php?t=855511)

Edit:
I see bodhi.zazen already posted that link.  ;)

---

### Post by markbuntu on 2008-07-11
64 bit processors have been around for ages now and they do offer a considerable advantage if you have a 64 bit OS and 64 bit apps. I have 32 bit and 64 bit Ubuntu Hardy on my machine dual booting from identical hard drives and I much prefer to use 64 bit. It is faster, it has less cpu load so my cpu runs cooler.

Over the past few months the updates, especially from Hardy Proposed have made 64 bit far more stable and useable.

All this griping about lack of apps for 64 bit strikes me as no different than all the griping about lack of support for windows apps in linux. There are plenty of high powered apps that run better on 64 bit than 32 bit.

But anyway, now that my rant is played out, I have 2GB of ram and that seems to be plenty for what I do. I had 3GB, 2 original 512MB and 2 1GB but I took out the 512MB because I was having some instability problems and I thought that they might be the cause. 

I know for a fact that in the past, mixing ram sizes was a guarantee for problems but I was assured that this was no longer the case by numerable people. Apparently they were all misinformed since I have had no problems since removing the 2 512MB ram. Not one crash, hang, or kernel panic, none, zero. On both 64 and 32 bit Hardy. I used to switch between them semi-arbitrarily when one crashed but now I have to do so intentionally to keep up with the updates.

---

### Post by jaem on 2008-09-01
I have the 6715b, and I can confirm that it works fine with 4GB/64-bit Ubuntu.  I haven't tried recompiling the kernel, but (as of now, anyways) 64-bit runs great on it, so switching to that would be my advice.

---

