---
title: "Confused about 64bit vs. 32bit"
date: 2011-11-24
forum: New to Ubuntu
---

### Post by DaimyoKirby on 2011-11-24
Hi there.
I've recently just looked into 32bit vs. 64bit, for whatever reason that I can't remember, but I'm a little bit confused.

I was trying to find out what bit-type my computer is, and commands like *uname -m* and *uname -a* returned:
```

alden@XubuntuZombie:~$ uname -m
i686
alden@XubuntuZombie:~$ uname -a
Linux XubuntuZombie 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:25:36 UTC 2011 i686 athlon i386 GNU/Linux

```
which people say indicate that my system is 32bit.

But when I run *grep --color=always -iw lm /proc/cpuinfo*, it returned:
```
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp [COLOR="Red"]lm[/COLOR] 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp [COLOR="red"]lm[/COLOR] 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv

```
which the ubuntu documentation about [32bit and 64bit]("https://help.ubuntu.com/community/32bit_and_64bit") said indicates that my computer is capable of 64bit.

If this is true, should I start running 64bit?
And if so, how would I go about accomplishing that?

(P.S. Don't assume that, because I'm using commands in the terminal, I'm terminal savvy. I'm not; far from it.)

---

### Post by San_SS! on 2011-11-24
There 2 things are different: you have a computer capable of running 64bit software, thus a 64 bit OS. But you have installed a 32bit OS. 

Whether you should start using a 64bit OS and software... In my personal experience with Ubuntu, I choose to use 64bit editions. In order to do that, you should download the 64bit version of ubuntu and reinstall.

---

### Post by oldos2er on 2011-11-24
**uname** shows info about the kernel you're running, not your hardware. If you want to install 64-bit Ubuntu, you will need to do a full install, since there's no way to upgrade to 64-bit.

---

### Post by DaimyoKirby on 2011-11-24
Oh, ok.
I don't want to go through all the hassle of reinstalling *everything* again unnecessarily, so I'll ask you two.
What makes 64bit different/better/worse than 32bit?
Would you recommend switching to 64bit?

---

### Post by oldfred on 2011-11-24
Do you have 20GB that you can allocate to another install. Then you could install the 64bit side by side and see if you notice any difference. Note that most of this is older as the issue has mostly been put to bed.

[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
Ubuntu 32-bit, 32-bit PAE, 64-bit Kernel Benchmarks Dec 2009
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)
Essentially says if you can use the 64bit kernel you should.
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)
Advantages and Disadvantages of 64bit. (Plus install Guides) from 2008
[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)
Benchmarks Performance on 9.04
[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

My backup plan is to have what I need to do a new clean install if I have a major crash. These are most of the backups you would need to upgrade with a clean install to the 64bit version. But you should be backing up anyway.
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

### Post by anton_melnikov on 2011-11-24
There are some pros and cons: you will have slightly better performance, mostly noticeable on CPU-hungry tasks, like archiving and multimedia encoding. But those "extra bits" are not free: the memory usage will be about 30% higher. Also you *may* have problems with Wine and proprietary software that was installed not from repos.

So, if you have more than 2 Gb of RAM and are not concerned about Wine and stuff, you can give it a try :) You will have to do a clean install though.

---

### Post by oldos2er on 2011-11-24
> **DaimyoKirby said:**
> 
What makes 64bit different/better/worse than 32bit?
Would you recommend switching to 64bit?

Some of this info is dated, but generally it still applies: [http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428) and [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
There are also umpteen threads in Recurring Discussions regarding 64-bit.

My opinion is if you have 64-bit capable hardware, run 64-bit software to take full advantage of it.

---

### Post by T.exe on 2011-11-24
As the number of bits (32-bits to 64bits) increases there are two important benefits.
 
[LIST]
[*] 		More bits means that data can be processed in larger chunks which also means more accurately.
[*] 		More bits means our system can point to or address a larger number of locations in physical memory.
[/LIST]
 32-bit systems were once desired because they could address (point  to) 4 Gigabytes (GB) of memory in one go. Some modern applications  require more than 4 GB of memory to complete their tasks so 64-bit  systems are now becoming more attractive because they can potentially  address up to 4 billion times that many locations.


The general rule is that 32-bit will run on on a lower level 64-bit  component but 64-bit does not run on a lower level 32-bit component:
 
[LIST]
[*] 		A 32-bit OS will run on a 32-bit or 64-bit processor without any problem.
[*] 		A 32-bit application will run on any combination of OS and processor
[*] 		But 64-bit application will only run on a 64-bit OS and a 64-bit OS will only run on a 64-bit processor.
[/LIST]

---

### Post by DaimyoKirby on 2011-11-24
Thanks so much to everyone!
I started reading some of the material posted by you all, and I'll continue to do so in the next couple of weeks.
I probably won't switch to 64bit just yet, since I don't have a good way or place to back up my files yet, but I'll switch eventually. Probably by January at the latest.
Thanks all!

---

### Post by ptrakk on 2011-11-24
i686 = 32 bits
your os is 32 bits running on a 64 bit compaatible pc. the only difference between the two is 64 bits allows you to run more than 3.5 GB of ram. that's all except for the hastles of finding drivers for older stuff.

---

### Post by DaimyoKirby on 2011-11-28
Thanks everyone for the advice and help!
I decided to just back up my important files, and reinstall, and I did; now I'm back up and running, but I don't notice any noticeable changes, except that Minecraft was running great; I'm sure things are running better, though.:)
Thanks again!

---

