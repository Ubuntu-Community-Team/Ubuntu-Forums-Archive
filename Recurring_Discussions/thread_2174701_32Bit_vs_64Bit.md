---
title: "32Bit vs 64Bit"
date: 2013-09-15
forum: Recurring Discussions
---

### Post by Chelidze on 2013-09-15
I know the easy part x64 can use more memory.

What am I interested in performance when we have the same amount of Ram "2 GB" (Just like you know what has and decided to change from x32 to x64). So if we have two same software just as good optimized on 32 and 64 bit systems, which one will run better ?? and why ?

thank you in advanced

---

### Post by oldfred on 2013-09-15
Ubuntu will finally suggest 64bit as the default with 13.10. It just about is to the point that full Ubuntu will not run on any system that is not 64bit, so there is no reason to install 32 bit on any newer computer.

 Post by VeeDub on choosing 64 bit:
[http://ubuntuforums.org/showthread.php?t=2133616&p=12594619#post12594619](http://ubuntuforums.org/showthread.php?t=2133616&p=12594619#post12594619)
[http://ubuntuforums.org/showthread.php?t=2028717](http://ubuntuforums.org/showthread.php?t=2028717)
32-bit vs. 64-bit Ubuntu 13.04 Linux Performance with only 1GB of RAM & most tests better with 64bit
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

### Post by tgalati4 on 2013-09-15
One test is worth a thousand expert opinions.

---

### Post by ibjsb4 on 2013-09-15
[a thousand expert opinions]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=64+vs+32+bit&sa=Search&cof=FORID:9") :P

---

### Post by Chelidze on 2013-09-15
> **tgalati4 said:**
> One test is worth a thousand expert opinions.

If you are suggesting running a x32 and x64 ubuntu setups easy I can do it but where can I find software that is perfectly optimized on both options 


[[COLOR=#C61919]oldfred[/COLOR]]("http://ubuntuforums.org/member.php?u=852711")[COLOR=#000000] 

[/COLOR][COLOR=#000000]Thank you for the reply

[/COLOR]Nice articles, I will elaborate on why did I posted this question, every one knows that new iphone is running x64 on 2gb ram and there is a lot of talk about it, It really got me thinking if there is a benefit of running x64 on 2gb of ram, and what better place to post a question like this.

Thanks every one for the replies you have been huge help especially [[COLOR=#C61919]oldfred[/COLOR]]("http://ubuntuforums.org/member.php?u=852711")[COLOR=#000000] [/COLOR]

---

### Post by linuxyogi on 2013-09-15
> **Chelidze said:**
> I know the easy part x64 can use more memory.

What am I interested in performance when we have the same amount of Ram "2 GB" (Just like you know what has and decided to change from x32 to x64). So if we have two same software just as good optimized on 32 and 64 bit systems, which one will run better ?? and why ?

thank you in advanced

My PC too has 2 GB of Ram. I have used both 32 & 64. Although I have never timed the performance but still I think tasks like video encoding is quite faster in 64.

---

### Post by sanderj on 2013-09-16
> **Chelidze said:**
> Nice articles, I will elaborate on why did I posted this question, every one knows that new iphone is running x64 on 2gb ram and there is a lot of talk about it, It really got me thinking if there is a benefit of running x64 on 2gb of ram, and what better place to post a question like this.


[http://www.phoronix.com/scan.php?page=article&item=ubuntu_x86_1304&num=4](http://www.phoronix.com/scan.php?page=article&item=ubuntu_x86_1304&num=4) says:


> To no surprise compared to our 32-bit vs. 64-bit benchmarking over nearly the past decade on Phoronix, the 64-bit version of Ubuntu generally delivers superior performance over 32-bit Ubuntu. This strong 64-bit performance is even when using an old Intel Core 2 Duo system with just 1GB of memory.

HTH

---

### Post by mynamesalex on 2013-09-16
Aside from increased ram availability, 64 bit processors and OS can use a 64 bit bus, processing 64 bits of information at a time instead of 32 bits.  This will increase processing speed in the iPhone OS and probably the core apps.  However, games, apps, etc. must all be updated by the developers to run in 64 bit mode.  Probably need to have separate iTunes store entries for 64 bit iPhone apps, because all the apps around should be in 32 bit mode.  If your app is in 32 bit mode it'll run in an extended 32 bit mode to support old apps --- however it will run the old 32 bit programs exactly the same as if it were a 32 bit iPhone.  

Likely, it will take a while for developers to start putting 64 bit to use.  The big problem with this though, is fragmentation.  It will force devs to either produce both 32 bit and 64 bit apps, just make a 32 bit app and ignore the 64 bit speed advantage, or only make 64 bit apps, and cut yourself off from the rest of the iOS world.

It's a bold move but has to be done.  Probably it will be just like when 64 bit was released on PC, and take years to become a standard. We'll probably see advances a lot faster than last time x64 was introduced though, since people already like it. Only time will tell.

---

### Post by Paqman on 2013-09-16
> **Chelidze said:**
> 
What am I interested in performance when we have the same amount of Ram "2 GB" (Just like you know what has and decided to change from x32 to x64). So if we have two same software just as good optimized on 32 and 64 bit systems, which one will run better ?? and why ?


A more specific way of phrasing this question might be: assuming you have a 64-bit capable processor and 2GB RAM, is there any advantage to using 32-bit?

Running 32-bit would consume very slightly less RAM, but running Ubuntu on 2GB of memory shouldn't cause you to run low on memory with most applications anyway, so that's not a big issue. There are a lot of common workloads (encryption, compression, media encoding, etc) where you will take a performance hit for opting to use 32-bit.

So you get a slight reduction in memory use that you probably will never notice, and a substantial reduction in performance for certain tasks. Personally I don't see any reason to use 32-bit software on a 64-bit chip whatever amount of RAM you have.

---

### Post by 1clue on 2013-09-16
For modern hardware, there's zero reason to use 32-bit if the system is capable of 64-bit.

Look up your motherboard.  If your motherboard is capable of 4g or more, and your board has no warnings about 64-bit, and you google that board with 64-bit and don't get a lot of complaints, AND your processor is 64-bit capable, then go with 64-bit.

Even if you only have 2g now, if your board is capable of 4g or more you're better off to use 64-bit.  You never know if you'll upgrade RAM in the future.  If you do, then a 64-bit install is going to just take advantage of it, no problem.  If your board is only capable of 4g then chances are your BIOS has some weird memory mapping because right around the time those boards were made some companies didn't really have a good way to handle it.  Lots of boards back then had a buggy BIOS, and IMO they're not all fixed.

Finally, years late IMO, Linux distros have started recommending 64-bit installs.  If you're not sure you want pure 64 then go with a multilib setup which is what Ubuntu puts in by default.

---

### Post by pqwoerituytrueiwoq on 2013-09-16
@1clue
as far as i know the 32bit libraries are not installed until you install some 32bit software like google earth or steam

---

### Post by 1clue on 2013-09-16
You may be right.  All I know is that with *buntu you don't really have to worry about it.  I use some distros that warn about installing "multilib" for those who prefer a pure 64-bit experience.  *buntu doesn't make a fuss.

---

### Post by cariboo on 2013-09-16
Moved to Recurring, there are enough links in this thread to prove it is recurring.

---

### Post by codingman on 2013-09-17
@cariboo

You probably should have just closed the thread, seeing that the OP has set it to solved as well...

---

