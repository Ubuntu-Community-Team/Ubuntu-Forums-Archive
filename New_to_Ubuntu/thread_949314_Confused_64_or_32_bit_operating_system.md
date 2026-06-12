---
title: "Confused? 64 or 32 bit operating system"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by PhilOHara on 2008-10-16
Hi Could somebody please clarify what is the best ubuntu operating system to load on my pc as I have a AMD 64 bit 1.8 GHZ motherboard with 1 mg memory.
I would presume the 64 bit version but reading the threads people say to run the 32 bit operating system....can I run the 32 bit system on a 64 bit processor an if so what are the pros and cons? thanks for your reply Phil

---

### Post by tangibleorange on 2008-10-16
> **PhilOHara said:**
> Hi Could somebody please clarify what is the best ubuntu operating system to load on my pc as I have a AMD 64 bit 1.8 GHZ motherboard with 1 mg memory.
I would presume the 64 bit version but reading the threads people say to run the 32 bit operating system....can I run the 32 bit system on a 64 bit processor an if so what are the pros and cons? thanks for your reply Phil

there is a lot of debate about this one. personally, i think if you are a new user and you use web plugins like flash and java, you are better starting with 32-bit - it can be run on most 64-bit processors in a kind of compatibility mode. The problem with 64-bit is that web plugins can be tricky to get working, as no native 64-bit versions exist.

but others will definitely disagree with me... you sacrifice a small amount of speed for (what i believe to be) easier setup.

---

### Post by hyper_ch on 2008-10-16
flash and java are no problems on 64-bit. They work out of the box - or well, with as much/little effort as on 32bit.

---

### Post by Nepherte on 2008-10-16
Just go with 64bit. The only thing you have to remember, is to install openjdk6 and icedtea web plugin instead of the official sun java.

Installing flash is absolutely no problem. The package management system automatically takes care of this.

---

### Post by Paqman on 2008-10-16
> **tangibleorange said:**
> The problem with 64-bit is that web plugins can be tricky to get working, as no native 64-bit versions exist.


That's used to be true, but not any more. It's all done automatically these days, you won't even know it's happening.

---

### Post by isparkes on 2008-10-16
I went 64bit the other day - the only slight problem I have noticed is that Skype is a little bit more tricky to install (you have to force the installation).

The future is 64, I'd say go with it unless you're a complete 100% noob.

---

### Post by hyper_ch on 2008-10-16
didn't you use skype from the medibuntu repos?

---

### Post by LowSky on 2008-10-16
install 64bit and if you need  java and flash and mp3 support use the following command and everything will work just fine

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by hyper_ch on 2008-10-16
also add the medibuntu repos for a few other things like skype, libdvdcss2, googleearth, ...

---

### Post by Frogging101 on 2008-10-16
Use 32-bit, it is more compatible with many things, and it is simpler.

---

### Post by Keen101 on 2008-10-16
Basically at this point in time they are basically the same. why are they basically the same? Well, because most programs don't take advantage of the new resources. Things will get better in time, and 64bit will be the one you want. however, there is no problem in running 32bit, and some people do even though they have 64bit processors.

The biggest advantage i hear is that only 64bit systems can take advantage of the 4gigs of memory and higher, but i can't confirm.

---

### Post by hyper_ch on 2008-10-16
32bit (or rather 34bit) can also address more than 4gb ram - you just need to enable PAE...

But the question is, is there any reason not to use 64bit now?

---

### Post by tangibleorange on 2008-10-16
sorry its been a long time since i tried to install a 64-bit OS - i hadn't really been following its progress, but if it works now - great!

---

### Post by jerome1232 on 2008-10-16
If you do alot of any of the following the 64-bit is actually a HUGE advantage (4GB+ ram or not)

audio/video encoding, gaming, compiling, compressing, encrypting.

Anything that involves alot of numbercrunching by your cpu will go much faster if it's taking advantage of the 64-bit architecture.

---

### Post by LowSky on 2008-10-16
> **jerome1232 said:**
> If you do alot of any of the following the 64-bit is actually a HUGE advantage (4GB+ ram or not)

audio/video encoding, gaming, compiling, compressing, encrypting.
 

This is only true if the program was designed to use a processors 64bit ability, if not the difference is small.

the same can be said for multicore CPUs as many apps cannot use the mutliple cores availbile which in some cases these programs will run slower than on old but higher clock rated CPUs.

The biggest advantage of 64Bit computing is the ability to use more RAM and to process longer strings of data. But for some reason 2GB of RAM is the norm and it has been for a long time. Operating Systems like Windows Vista are pushing the use of more RAM but not enough to really warrant 64bit computing. Computers have had the abiltiy to use 64Bits for quite some time starting in 2003 with the first AMD Athlon 64. although these processors have been availible an odd occurance happened in computing, Micorsoft released Vista much later than planned, Game developemnt for PC took a hit from consol gamming and piracy, and many users baught low end machines over mid to high range because of their need for running only light use like internet and word processing.
64Bit will be popular in the comming years as Windows 7 is released and with Proccessor companes moving to phase out old chip controller to free up space for newer technology like extra cores or transport lanes.

---

### Post by hyper_ch on 2008-10-16
> **LowSky said:**
> Computers have had the abiltiy to use 64Bits for quite some time starting in 2003 with the first AMD Athlon 64.

I have to disagree:

    * 1961: IBM delivers the IBM 7030 Stretch supercomputer, which uses 64-bit data words and 32- or 64-bit instruction words.

    * 1974: Control Data Corporation launches the CDC Star-100 vector supercomputer, which uses a 64-bit word architecture (previous CDC systems were based on a 60-bit architecture).

    * 1976: Cray Research delivers the first Cray-1 supercomputer, which is based on a 64-bit word architecture and would form the basis for later Cray vector supercomputers.

    * 1983: Elxsi launches the Elxsi 6400 parallel minisupercomputer. The Elxsi architecture has 64-bit data registers but a 32-bit address space.

    * 1991: MIPS Technologies produces the first 64-bit microprocessor, the R4000, which implements the MIPS III ISA, the third revision of their MIPS architecture.[2] The CPU is used in SGI graphics workstations starting with the IRIS Crimson. However, 64-bit support for the R4000 would not be included in the IRIX operating system until IRIX 6.2, released in 1996. Kendall Square Research deliver their first KSR1 supercomputer, based on a proprietary 64-bit RISC processor architecture running OSF/1.


[http://en.wikipedia.org/wiki/64-bit](http://en.wikipedia.org/wiki/64-bit)

---

### Post by jerome1232 on 2008-10-16
> **LowSky said:**
> This is only true if the program was designed to use a processors 64bit ability, if not the difference is small.
Hence
> **jerome1232 said:**
> Anything that involves alot of numbercrunching by your cpu will go much faster if it's taking advantage of the 64-bit architecture.

Alot of programs are multi threaded, some aren't, do a little research and you can find which ones take advantage of your extra cores.

Nearlly all of the code you run on a 64bit Ubuntu installation is in fact 64-bit code, not 32-bit code. It's an advantage now, not in the future. 64-bit machines have been around for a very long time.

---

### Post by Therion on 2008-10-16
I've been using 64-bit Ubuntu since Feisty.  In my experience the whole "issue" with Java/Flash on a 64-bit distro is DEAD.  I've had exactly zero problems with getting both working flawlessly under 64bit distros.  The biggest "issue" I can think of was uninstalling Gnash player which seemed to conflict with the Adobe plugin, I think under Gutsy.  That took about, ohhhh...  Ten seconds in Synaptic to fix.

I can't verify from my own personal experience that the 64-bit versions are *perceptibly* faster but what I can tell you is that a 64-bit install runs much more smoothly.  It's a hard thing to define but once you experience it, you'll never want to go back to a 32-bit distro.  It's a just a whole different "ride" using 64-bit.

---

### Post by PhilOHara on 2008-10-18
Thank to everyone who responded I think I go with 64 bit...cheers

---

### Post by scorp123 on 2008-10-19
> **Nepherte said:**
> Just go with 64bit. The only thing you have to remember, is to install openjdk6 and icedtea web plugin instead of the official sun java. Can you post a link with instructions somewhere somehow please? I am having trouble with certain Java web apps that only seem to work with Sun's Java ... and that one only exists for 32-bit on Linux.

Right now I have to use 32-bit Linux with a PAE-enabled kernel .. but I'd clearly prefer a clean 64-bit solution if there is one?

---

### Post by hyper_ch on 2008-10-19
scorp: if you install sun java it will also install the required 32-bit (ia32) libs in order to run it. I have not yet experienced problems that way.

---

### Post by Nepherte on 2008-10-19
> **scorp123 said:**
> Can you post a link with instructions somewhere somehow please? I am having trouble with certain Java web apps that only seem to work with Sun's Java ... and that one only exists for 32-bit on Linux.

Right now I have to use 32-bit Linux with a PAE-enabled kernel .. but I'd clearly prefer a clean 64-bit solution if there is one?
If you follow these instructions, you'll have openjdk 64bit and a java 64 bit web plugin:
```
sudo apt-get install openjdk-6-jre icedtea-gcjwebplugin
```

---

### Post by Mike'sHardLinux on 2008-10-19
While, theoretically speaking, the 64-bit Ubuntu should be faster than 32-bit for many things, I haven't seen any concrete proof that it is really noticeably faster. I DO in fact do things like video and audio encoding, and it feels about the same to me. If it encodes an mp3 in 2 or 3 less seconds, I wouldn't consider that a "HUGE advantage".

I have been running 64-bit since Gutsy (been using Hardy since it was beta). I haven't been able to get certain software compiled and working in 64-bit. Maybe I am missing something? For example, Lacie Lightscribe labeler and zsNES. I am pretty sure there are a few others I couldn't get working. An yes, I know about installing 32-bit libs and forcing architecture, etc.... That doesn't always work.

---

### Post by jerome1232 on 2008-10-19
For zsnes [http://ubuntuforums.org/showthread.php?t=588744](http://ubuntuforums.org/showthread.php?t=588744)

---

### Post by scorp123 on 2008-10-19
> **hyper_ch said:**
> scorp: if you install sun java it will also install the required 32-bit (ia32) libs in order to run it. I have not yet experienced problems that way. Yes, but: the browser-plugin doesn't exist for 64-bit, only for 32-bit. And the Java stuff I have to use won't work with those alternative plugins.

Here's one of the products I am talking about and for which I apparently really really need SUN's java:

Sun Secure Global Desktop
[http://www.sun.com/software/products/sgd/index.jsp](http://www.sun.com/software/products/sgd/index.jsp)

What it does? Well ... it's both a "WebTop" and a VPN-replacement. With it you can deliver any app (Windows, Unix, Linux, Mainframe, etc.) to any Java-enabled browser. So to access e.g. my Windows 2003 or my Solaris 10 session in my office all I'd need is a web browser with the Sun Java plugin and I can get in. Fullscreen, 16-bit graphics and even with sound if I want to. And it even works across low-bandwidth connections, I just need to get into the Internet somehow. It's a really cool piece of software .... But: it's from Sun, so it uses Java. A lot. 

So, to work with this I really really need the Sun Java plugin it seems. So far I have not managed to get this thing working with any of the other plugins (e.g. openjdk6, gcj, and so on).

Anyone who's interested can take a free test-ride on SUN's server (no username or password needed, just hit the "Login" button):
[https://sgddemo.sun.com/](https://sgddemo.sun.com/)

I'd be glad if any of you 64-bit users could try that "Test Ride" link above and tell me if you ever get to the main menu? (You should get to a web page offering you various applications, e.g. "PowerPoint Viewer", and so on.). My experience so far with 64-bit Linux and the various Non-SUN plugins was that this stuff simply will not work :(

---

### Post by scorp123 on 2008-10-19
> **Nepherte said:**
> If you follow these instructions, you'll have openjdk 64bit and a java 64 bit web plugin:
```
sudo apt-get install openjdk-6-jre icedtea-gcjwebplugin
``` OK, please see my previous posting (above this one). I assume you have that combo installed? Can you then please go to this web site and try if it will open for you? 

[https://sgddemo.sun.com/](https://sgddemo.sun.com/)

---

### Post by Mike'sHardLinux on 2008-10-19
> **jerome1232 said:**
> For zsnes [http://ubuntuforums.org/showthread.php?t=588744](http://ubuntuforums.org/showthread.php?t=588744)

For the record, I've visited that thread several times since I've been using Hardy. I guess it has been a while since my last visit. Dfreer's repo was down for quite some time, and everything else I tried had failed.

This kind of supports the fact that running 64-bit anything can still be a real hassle. The people who think it's perfect are just lucky that the software they happen to use is precompiled for them already; or in some cases, compiles using the fore architecture thing. Granted, some *workarounds* have worked for me as well.

Anyway, thanks for the reminder of that thread. It'll be nice to kill some time in zsNES again! Gotta go thank Dfreer again!!

---

