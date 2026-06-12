---
title: "32bit vs 64bit"
date: 2013-10-21
forum: Recurring Discussions
---

### Post by mcsheffrey on 2013-10-21
A few questions here, 
1. Are there any advantages to moving to 64bit ubuntu, and are there any prerequisetes.
2. Can u upgrade to 64bit without re-installing.

---

### Post by broadcast23 on 2013-10-21
How much RAM do you have?  You need a 64bit capable processor, and it is better for more than 4GB of ram since 32bit can't see it.  Also if your upgrading from 32bit to 64bit you will need to reinstall since the code is different for 64bit.

---

### Post by vasa1 on 2013-10-21
[http://ubuntuforums.org/showthread.php?t=2089495](http://ubuntuforums.org/showthread.php?t=2089495)
[http://ubuntuforums.org/showthread.php?t=2077173](http://ubuntuforums.org/showthread.php?t=2077173)
[http://ubuntuforums.org/showthread.php?t=1992810](http://ubuntuforums.org/showthread.php?t=1992810)
[http://ubuntuforums.org/showthread.php?t=2174701&p=12789977#post12789977](http://ubuntuforums.org/showthread.php?t=2174701&p=12789977#post12789977)

---

### Post by mcsheffrey on 2013-10-21
Well I do have a 64bit capable processor, and 4Gig of memory, don't like the idea of having to re-install, but what are the advantages of moving to 64bit. Anyone aware of what I could possibly loose by upgrading to 64 bit.  Tks Roy

---

### Post by terminator14 on 2013-10-21
> **mcsheffrey said:**
> Well I do have a 64bit capable processor, and 4Gig of memory, don't like the idea of having to re-install, but what are the advantages of moving to 64bit. Anyone aware of what I could possibly loose by upgrading to 64 bit.  Tks Roy

As far as I know, there are no advantages to staying with 32 bit. The only thing 32 bit is good for is running on super old computers that don't have a 64 bit CPU.
I probably wouldn't reinstall my entire system just to switch to 64 bit, but the next major upgrade you do in Ubuntu version (13.04 to 13.10 or w/e), go with 64 bit. I doubt you will find any disadvantages.

---

### Post by jimmy-frydkaer on 2013-10-22
It isn't entirely true that a 32 bit system cannot "see" more than 4 gig of memory. All you need to do for your Ubuntu system, as for any Linux system, to "see" more than 4 gig is to use a Linux PAE-kernel. PAE, or Physical Address Extension, which takes care of the otherwise limited address range.

If you have 4 GB of memory or more it **can **be an advantage for you to upgrade to a 64 bit system. For that you'll need a fresh, or clean install.
Many people believe that going from 32 bit to 64 bit will double the speed on the system. It don't. You'll only see an increase in speed at 15 - 25% no more than that.
64 bit is the future but as far as applications are concerned we aren't quite there yet. The biggest gain in performance you'll experience is if you have a multi-core CPU and you have been running a 32 bit Windows (don't you just love Microsoft for making 32 bit Windows computers on a 64 bit capable sys?) and the biggest increase you'll see is in media conversion where all your CPU kernels works at 100%. Better still if your CPU supports Hyper Threading too.

---

### Post by monkeybrain20122 on 2013-10-22
> **jimmy-frydkaer said:**
> 

64 bit is the future but as far as applications are concerned we aren't quite there yet. .

Huh?? Nowadays you can't even buy a 32 bit laptop. What applications are you talking about?

---

### Post by CaptainMark on 2013-10-22
A 64 bit system will actually use more ram than an identical 32 bit equivalent, so if your running on a netbook or seriously aging machine stick to 32, for anything else there's no downside not to go for 64 bit but you will have to re-install.
A bit of advice for the future though: run an internet search before posting straight here, this question has been asked and answered hundreds of times on this very forum alone and repetitive questions are known to be closed by the admins

---

### Post by FGQhxGt on 2013-10-22
> **jimmy-frydkaer said:**
> 64 bit is the future but as far as applications are concerned we aren't quite there yet.As far as applications are concerned, I never had any problem running a 64-bit Linux OS. Every application I need is there and behaves well (of course mileage may vary from case to case).

Then, I agree if you say that many applications (especially on Windows) are still 32-bit ones but also in that case many applications already made the jump: Office is available in 64-bit, Photoshop is available in 64-bit, WinRAR is available in 64-bit and so is Java for example, and so on.

So, in my opinion there's no downside in switching to a 64-bit OS (apart from having to re-install), even because many applications' newest versions (such as VMWare player) are no longer supported on 32-bit systems. :D

---

### Post by oldfred on 2013-10-22
Moved to recurring discussions.
 
This poor old horse has been beat to death so many times. See also Vasa's post #3 above.

 Post by VeeDub on choosing 64 bit:
[http://ubuntuforums.org/showthread.php?t=2133616&p=12594619#post12594619](http://ubuntuforums.org/showthread.php?t=2133616&p=12594619#post12594619)
[http://ubuntuforums.org/showthread.php?t=2028717](http://ubuntuforums.org/showthread.php?t=2028717)
32-bit vs. 64-bit Ubuntu 13.04 Linux Performance with only 1GB of RAM & most tests better with 64bit Mac Mini
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_x86_1304&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_x86_1304&num=1)
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

### Post by help_me2 on 2013-10-22
> **jimmy-frydkaer said:**
> 
64 bit is the future but as far as applications are concerned we aren't quite there yet.
Such as? I've been using 64bit for 3 years and never had a problem with *anything*. 64bit is now the standard btw. All computers sold are now 64bit, and run 64bit OS's, except for maybe some netbooks. And please, don't name some obscure apps that 99.9% of the population would never use. Besides, even **if** you could find an app that isn't available in 64, you can always run 32bit apps in 64bit. :P No real reason to *not* use 64.

---

