---
title: "32-bit versus 64-bit"
date: 2008-10-16
forum: Recurring Discussions
---

### Post by WaeV on 2008-10-16
I have used 64-bit AMD processors since 2004 and have toyed around with a few 64-bit systems, but the vastly superior support for 32-bit has kept me away from 64-bit in recent years.  What are the advantages of a 64-bit system versus a 32-bit OS on a 64-bit chip?

---

### Post by KiwiNZ on 2008-10-16
To be honest ,right now , not a lot . That may well change in time . But many in the Industry believe that 64bit will not reach prime time

---

### Post by era86 on 2008-10-16
Well, I believe you are able to use alot more RAM :)  I know for development, this might come in handy.

---

### Post by hyper_ch on 2008-10-16
question is: what are the disadvantages for using 64bit on linux comapred to 32bit?

---

### Post by Perfect Storm on 2008-10-16
> **hyper_ch said:**
> question is: what are the disadvantages for using 64bit on linux comapred to 32bit?

None, well there's java in browser but there's a workaround (which can be found on our 64-bit forum). But I have heard that when sun Java 1.7 comes out it will be 64-bit compatible.

---

### Post by natehall on 2008-10-16
I have a Dell 1420N Inspiron that I bought preinstalled with Ubuntu last year. Turns out it was with the 32 bit version even though it has a 64 bit processor.  I did a fresh install with 64 bit 8.10 and most of the stuff worked fine but the Wireless didn't.  I like to do stuff with Gimp and the 64 bit version ran at warp speed compared with the 32 bit version. 

Kept trying to get the wireless to work only to find out you have to use the Ndiswrapper. I went back to the 32 bit version. I figure a native 64 bit driver for the wireless will happen one of these days and I'll go back to 64 bit when that happens as part of my six month fresh install cycle.

---

### Post by hyper_ch on 2008-10-16
Ibex uses newer kernels and I think has also a lot more wifi drivers in there. You might want to download the 64bit Ibex Beta and see if your wifi runs :)

---

### Post by CJ56 on 2008-10-16
Running Hardy 8.04.1 I've just moved over from 32-bit to 64-bit and so far I'm very pleased. 

I've got a wired connection, so wifi isn't an issue. I grabbed all the restricted extras plus Medibuntu lidvdcss & W32 codecs and followed the instructions on the x86 64-bit users page to get Flash and Java. Graphics were from the automated restricted drivers tool, for a GeForce 7300GT

So far, everything works! And the basic selection of apps + VLC all worked straight off without any tweaking

And, better yet, it runs just a little bit faster in all applications. Web pages on FF3 load quicker, which surprised me. I don't do any really big-ticket stuff like video editing, but even at my modest level, I really appreciate the extra snap & slickness.

I'm slightly holding my breath to see what breaks first, but at the moment it's definitely been worth the change... :)

---

### Post by hyper_ch on 2008-10-16
try to convert a dvd-->avi... you'll notice a lot of speed improvement there ;)

---

### Post by beniwtv on 2008-10-16
Well, using 64 bit since hardy (both on my home cinema, servers and my laptop) and I'm very happy.

I have yet to come across anything that won't work with 64 bit but does with 32 bits. I think 64 bit support in Linux is very mature at this stage.

(And yes, I use Wine, Flash, Java, Video (codecs), dev environments, 32 bit software, many different tools, etc...)

Cheers,

---

### Post by Perfect Storm on 2008-10-16
> **natehall said:**
>   I like to do stuff with Gimp and the 64 bit version ran at warp speed compared with the 32 bit version. 


I noctied that too. It's damn fast now, also when doing heavy editing with big pictures you can see the diffrences.
(and Gimp 2.6 is absolutly awesome/brilliant).

---

### Post by jespdj on 2008-10-16
> **WaeV said:**
> ... but the vastly superior support for 32-bit has kept me away from 64-bit in recent years.  What are the advantages of a 64-bit system versus a 32-bit OS on a 64-bit chip?
"Vastly superior support"? Are you talking about Windows or about Linux here? The 32/64-bit issue is completely different on Linux than it is on Windows, precisely because Windows is not an open source operating system.

On Windows, you are totally dependent on the companies who sell you applications and drivers. Since 99% of the people run 32-bit Windows, those companies don't bother with making 64-bit software.

On an open source system like Linux, it's totally different. Since the source code for all software is available, it's easy to compile it for 64-bit. Note that in the Ubuntu repositories, practically everything that's available for the 32-bit version is also available for the 64-bit version.

The only two 32-bit programs that I'm running on my 64-bit Ubuntu system are two proprietary programs: Adobe Flash ans Skype. And installing those on a 64-bit system is just as easy as on a 32-bit system.

In the Linux world, it is certainly not true that there is "vastly superior support for 32-bit".

---

### Post by _sAm_ on 2008-10-16
If you ask me it sounds like pain to install 32bits flash in 64bits: [http://ubuntuforums.org/showthread.php?t=948729](http://ubuntuforums.org/showthread.php?t=948729) 

Then we have Java and skype. And if you want to use other proprietary programs, Like Bibble labs and others, you will only get 32bits versions. 

If you install the Ubuntu server kernel you can use more then 3.4gig with ram. I have read some test of 32 vs 64 bits Linux and the different is very small. So all in all, I don't see the big point with 64bits.

---

### Post by Paqman on 2008-10-16
> **jespdj said:**
> 
In the Linux world, it is certainly not true that there is "vastly superior support for 32-bit".

Completely agree. As i've said many times on this forum: the user experience for 64-bit Ubuntu is identical to 32-bit. You just get a nice little speed boost in some tasks.

Why throttle a 64-bit chip down?

---

### Post by jespdj on 2008-10-16
> **_sAm_ said:**
> If you ask me it sounds like pain to install 32bits flash in 64bits: [http://ubuntuforums.org/showthread.php?t=948729](http://ubuntuforums.org/showthread.php?t=948729)
Are your running a 64-bit system yourself? Have you tried installing Flash on a 64-bit system? Or are you running a 32-bit system and are you just repeating what others say?

Since Ubuntu 7.10 installing Flash on a 64-bit system is exactly the same as on a 32-bit system:
```
sudo apt-get install flashplugin-nonfree
```
On 64-bit, this with automatically install nspluginwrapper, which is an adapter to make 32-bit Flash work on 64-bit Firefox.

---

### Post by _sAm_ on 2008-10-16
> **jespdj said:**
> Are your running a 64-bit system yourself? Have you tried installing Flash on a 64-bit system? Or are you running a 32-bit system and are you just repeating what others say?

Since Ubuntu 7.10 installing Flash on a 64-bit system is exactly the same as on a 32-bit system:
```
sudo apt-get install flashplugin-nonfree
```
On 64-bit, this with automatically install nspluginwrapper, which is an adapter to make 32-bit Flash work on 64-bit Firefox.
Neither, I am providing a link where you can read how 64bits users are struggling to install the latest release of Adobe flash(10) witch is not in the repos. The same software that is one-click install on 32 bits.

---

### Post by hyper_ch on 2008-10-16
installing software outside the repos is not recommended for anyone with little knowledge on linux. So that comparison has no meaning ;)

---

### Post by _sAm_ on 2008-10-16
> **hyper_ch said:**
> installing software outside the repos is not recommended for anyone with little knowledge on linux. So that comparison has no meaning ;)

Tell him that when he is sitting on Ubuntu Ibex 64 bits and Flash 11 comes out witch he really want. Or if he wants to try out Bibble Labs etc. 

I believe I answered his question, and that he is able to judge for himself what is relevant for him.

---

### Post by jespdj on 2008-10-16
> **_sAm_ said:**
> Neither, I am providing a link where you can read how 64bits users are struggling to install the latest release of Adobe flash(10) witch is not in the repos. The same software that is one-click install on 32 bits.
Someone [made a script](http://ubuntuforums.org/showpost.php?p=5974204&postcount=30) to install it on 64-bit. I just installed it, it was 30 seconds work.

I'm sure it's going to be in the repos soon.

---

### Post by Paqman on 2008-10-16
> **_sAm_ said:**
> Tell him that when he is sitting on Ubuntu Ibex 64 bits and Flash 11 comes out witch he really want.

That would only be a problem if it wasn't going to be in the repos. If you can't wait for it to be packaged properly, then you're just creating hassle for yourself. The problem you're citing is not 64-bit, but impatience.

---

### Post by JohnFH on 2008-10-16
I have 64bit Hardy running on AMD64.  The only problem I have is that Python-psyco isn't available on 64bit.  :(

---

### Post by jespdj on 2008-10-16
Also note that 32-bit packages can be installed on a 64-bit system with "dpkg -i --force-architecture". You'll have to make sure that you have the necessary 32-bit libraries installed, and there's [getlibs](http://ubuntuforums.org/showthread.php?t=474790) to make this easy.

> **JohnFH said:**
> I have 64bit Hardy running on AMD64.  The only problem I have is that Python-psyco isn't available on 64bit.  :(
It's [open source](http://psyco.sourceforge.net/), right? You could try compiling it yourself on your 64-bit system. (Strange that there's only a 32-bit version of this in the Ubuntu repos; you could file a bug report on Launchpad to ask for a 64-bit version in the repos).

---

### Post by qazwsx on 2008-10-16
> **_sAm_ said:**
>  Ibex 64 bits and Flash 11 comes out witch he really want

I think Flash 11 is going to be 64bit (+32bit). I am not 100% sure.
 At least that blog has stated that it is under development... or possibly just a prank 
[http://blogs.adobe.com/penguin.swf/](http://blogs.adobe.com/penguin.swf/)

---

### Post by JohnFH on 2008-10-16
Of course!  I'll have a go at compiling it myself - thanks.

---

### Post by Joeb454 on 2008-10-16
> **KiwiNZ said:**
> To be honest ,right now , not a lot . That may well change in time . But many in the Industry believe that 64bit will not reach prime time

I'm waiting for 128 or 256 bit processors ;)

---

### Post by Perfect Storm on 2008-10-16
> **Joeb454 said:**
> I'm waiting for 128 or 256 bit processors ;)

[img]http://www.imageviper.com/displayimage/128836/0/Joeb.gif[/img]

---

### Post by hyper_ch on 2008-10-16
and you'll fill the 256bit processor full with ram and then you wget the whole internet into ram?

---

### Post by Joeb454 on 2008-10-16
> **Artificial Intelligence said:**
> [img]http://www.imageviper.com/displayimage/128836/0/Joeb.gif[/img]

Yes?

> **hyper_ch said:**
> and you'll fill the 256bit processor full with ram and then you wget the whole internet into ram?

That's the plan. I'll have superfast interwebz then :)

---

### Post by Canis familiaris on 2008-10-16
> **Joeb454 said:**
> I'm waiting for 128 or 256 bit processors ;)

I am waiting for 1 Gigabit processor. :P

---

### Post by Therion on 2008-10-16
I've bounced back and forth between 32bit and 64bit Ubuntu distros since Feisty and my experience is once you've done 64bit you'll never look back.  There were some initial hitches with Gutsy 64bit and the nVidia binary driver, but that was an easy fix.  Other than that I've had zero issues with running a 64bit distro.  And that includes Flash, Java etc.  ZERO problems.  Period.  

I won't say running 64bit is faster, but it is, for lack of a better word, a "smoother" overall computing experience.  I can't quite define that, but once you experience it you'll know what I mean.  Now if 64bit simply doesn't work for you for whatever reason then yeah, fall back on 32bit and get on with life.  But if your processor supports 64bit computing and the distro itself, generally speaking, runs well on your system, why WOULDN'T you want to use a 64bit distro?

---

### Post by ratmandall on 2008-10-16
> **KiwiNZ said:**
> To be honest ,right now , not a lot . That may well change in time . But many in the Industry believe that 64bit will not reach prime time
*OffTopic
Congrats on your 26,000 post

---

### Post by CrazyArcher on 2008-10-17
Not that many apps really make the full use of 64 bits, and in that sense the situation is similar to having 2/4 cores - not that many programs multithread efficiently. However, I believe that the situation will improve over time. After all, the transition from 16 bits to 32 didn't happen overnight either.

---

### Post by Ioky on 2008-10-19
64bit seem great, exspecially with Linux, I will switch to 64bit once Java, and Flash are already. you know, you just need those stuff on ago around the web --.--! how sad. but anyway. is time to movie forward.

---

### Post by Ioky on 2008-10-19
> **anurag_panda said:**
> i am waiting for 1 gigabit processor. :p

+10

---

### Post by BabboMatteo on 2008-11-26
Well,

thank you all in making my choiche more easier, I installed II 64bit two days ago, but the lack of support for Java and Flash makes me a bit perplexed...

roll back to 32bit :D

---

### Post by bruce89 on 2008-11-26
> **BabboMatteo said:**
> thank you all in making my choiche more easier, I installed II 64bit two days ago, but the lack of support for Java and Flash makes me a bit perplexed...


That is not the case anymore. OpenJDK is ported to more (all) architectures, and non-free flash is now available on x86_64.

> **CrazyArcher said:**
> Not that many apps really make the full use of 64 bits, and in that sense the situation is similar to having 2/4 cores - not that many programs multithread efficiently. However, I believe that the situation will improve over time. After all, the transition from 16 bits to 32 didn't happen overnight either.

Quite a few programs use [FONT="Monospace"]double[/FONT]s, which are 64 bits long. 64 bit CPUs can deal with them in one cycle instead of two. Also, programs compiled for 64 bit CPUs have certain things (SSE, MMX etc.) enabled always.

---

### Post by new2ubuntu on 2009-12-27
I installed Mint 8 64-bit last week and flash and java came and worked great. Most things worked... however I did run into a few programs that did not have a 64 bit version and there is no way to run some 32 bit programs in 64 bit system because library conflicts. In Windows 64 bit, it just puts a program like that in a 32 bit space ... I wish linux had something like that... since it doesn't... I went back to 32 bit.

---

### Post by Keyper7 on 2009-12-27
oMG tEH zOMbIES!!!1!!!1!!

---

### Post by Exodist on 2009-12-29
> **new2ubuntu said:**
> I installed Mint 8 64-bit last week and flash and java came and worked great. Most things worked... however I did run into a few programs that did not have a 64 bit version and there is no way to run some 32 bit programs in 64 bit system because library conflicts. In Windows 64 bit, it just puts a program like that in a 32 bit space ... I wish linux had something like that... since it doesn't... I went back to 32 bit.
Most new linux systems do. They include both 32bit and 64bit library files. SuSE was the first to start doing this about 5 years ago. ;-)

---

### Post by jmat on 2009-12-29
Hey Everyone,

Question: Can anyone explain, in user-friendly layman's language, what the difference is between the 32 and 64 Bit versions of Ubuntu 9.10?  A friend told me that he thought the 64 bit technology runs faster--does this sound correct?  Also, if I've installed the 32 bit version on a computer that can handle 64 Bit, am I going to miss anything by not having the optimum technology?  

I know, I'm asking a lot of questions :) but one more: Is there a terminal command one can use to determine if the machine is 32 or 64 Bit compatible? 

Happy Holidays and a Prosperous New Year!

Joe

---

### Post by 3rdalbum on 2009-12-29
1. 64-bit can address more RAM. 32-bit is limited to 4 GiB of total address space, so 64-bit is useful if you have more RAM than that. Certain calculations run faster on 64-bit machines because you're working with more precise numbers.

That's the main difference.

2. You won't know what you're missing if you install 32-bit onto a 64-bit-capable computer. There's not really much of a difference for everyday work, but you might as well use 64-bit if your machine can handle it.

3. I'm not sure how to determine if the CPU itself is 64-bit capable. I'd just look up your processor model (you can find it out through System Monitor) on Wikipedia and see if there's any mention of 64-bit support!

---

### Post by drs305 on 2009-12-29
Here are a couple of ways of seeing 64-bit/32-bit:

If you get colored "lm" from the following command, it's 64-bit:
```

grep --color=always ' lm ' /proc/cpuinfo

```

or:
```

file `which bash`

```

or:
System, Administration, System Monitor: System tab.

---

### Post by philinux on 2009-12-29
> **jmat said:**
> Hey Everyone,

Question: Can anyone explain, in user-friendly layman's language, what the difference is between the 32 and 64 Bit versions of Ubuntu 9.10?  A friend told me that he thought the 64 bit technology runs faster--does this sound correct?  Also, if I've installed the 32 bit version on a computer that can handle 64 Bit, am I going to miss anything by not having the optimum technology?  

I know, I'm asking a lot of questions :) but one more: Is there a terminal command one can use to determine if the machine is 32 or 64 Bit compatible? 

Happy Holidays and a Prosperous New Year!

Joe

This comes up a lot.

[http://www.google.co.uk/search?q=ubuntu+forums+32+64+bit&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.co.uk/search?q=ubuntu+forums+32+64+bit&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

---

### Post by 3rdalbum on 2009-12-29
> **drs305 said:**
> Here are a couple of ways of seeing 64-bit/32-bit:

If you get colored "lm" from the following command, it's 64-bit:
```

grep --color=always ' lm ' /proc/cpuinfo

```

or:
```

file `which bash`

```

or:
System, Administration, System Monitor: System tab.

file `which bash` shows you if you are running 64-bit Linux. If your computer is 64-bit but your OS is 32-bit, it will say "32-bit".

Also there's nothing in System Monitor about whether your CPU is 64-bit?

---

### Post by mörgæs on 2009-12-29
> **philinux said:**
> This comes up a lot.

[http://www.google.co.uk/search?q=ubuntu+forums+32+64+bit&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.co.uk/search?q=ubuntu+forums+32+64+bit&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

A little off topic: 

Googling with ```
32 64 bit site:http://ubuntuforums.org
``` in the search field gives a more precise search.

---

### Post by drs305 on 2009-12-29
> **3rdalbum said:**
> Also there's nothing in System Monitor about whether your CPU is 64-bit?

Mine shows that I am using an AMD 64 processor.

I also didn't mention the "uname -m" command, but that always seems to degenerate into the definition of "machine"...  ;-)

---

### Post by Joeb454 on 2009-12-29
Moved to Recurring Discussions.

Personally, I don't think there's currently much difference in running the 64 bit versions compared to the 32 bit...so I run 64 bit :)

---

### Post by Pasdar on 2009-12-29
I installed 64bit kubuntu since 2-3 weeks ago and I think the performance is boosted. its snappier...

---

### Post by MooPi on 2009-12-29
Hard to say if performance has changed significantly since the change to 64bit. The reason is I was using older kernel and Crunchbang 32bit versus Minimal Ubuntu 64bit, which is using a more recent kernel. It seems to be snappier but it could just be the improved kernel. I don't find using Linux harder under 64bit.

---

### Post by cariboo on 2009-12-29
When I click on the System tab in System Monitor I get what type of cpu I'm running. See screenshot.

---

### Post by mmix on 2009-12-29
multiply

[http://gmplib.org/gmpbench.html](http://gmplib.org/gmpbench.html)

---

### Post by HappyFeet on 2009-12-29
> **Pasdar said:**
> I installed 64bit kubuntu since 2-3 weeks ago and I think the performance is boosted. its snappier...

I agree. To me also, it feels faster. Plus, I do a lot of VM stuff, and the 6GB of RAM I have get put to good use.

---

### Post by crimesaucer on 2009-12-30
I think this Phoronix article is worth a look: [http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)

They take the same Lenovo ThinkPad T61 notebook running an Intel Core 2 Duo T9300 processor, 4GB of system memory, a 100GB Hitachi HTS7220 SATA HDD, and a NVIDIA Quadro NVS 140M and benchmark it using 3 different installs of Ubuntu 9.10:

1.) 32-bit Ubuntu 9.10 that's only using 3GB RAM
2.) 32-bit PAE Ubuntu 9.10 using all 4GB of RAM
3.) 64-bit Ubuntu 9.10 that also uses all 4GB of RAM.


64-bit was much faster in every test.

---

### Post by crimesaucer on 2009-12-30
> **Keyper7 said:**
> oMG tEH zOMbIES!!!1!!!1!!

I don't know why I feel compelled to post these benchmarks in a zombie thread from 2008, but have a look at these results from Phoronix: [http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)

They take the same Lenovo ThinkPad T61 notebook running an Intel Core 2 Duo T9300 processor, 4GB of system memory, a 100GB Hitachi HTS7220 SATA HDD, and a NVIDIA Quadro NVS 140M and benchmark it using 3 different installs of Ubuntu 9.10:

1.) 32-bit Ubuntu 9.10 that's only using 3GB RAM
2.) 32-bit PAE Ubuntu 9.10 using all 4GB of RAM
3.) 64-bit Ubuntu 9.10 that also uses all 4GB of RAM.


64-bit was much faster in every test.

---

