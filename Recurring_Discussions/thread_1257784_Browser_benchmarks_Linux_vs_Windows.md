---
title: "Browser benchmarks: Linux vs Windows"
date: 2009-09-04
forum: Recurring Discussions
---

### Post by unimatrix on 2009-09-04
I have found this excellent browser benchmarking tool called [Peacekeeper]("http://service.futuremark.com/peacekeeper") and have decided to compare the results in Windows and Linux using the same browsers, on the same computer.
So let's go right down to it...

_Computer specs:_
CPU: AMD 64 X2 Dual Core 4600+
MEM: 2.0 GB
GPU: nVidia GeForce 7900 GS (driver 180.44)

**Windows XP SP3 (32-bit)**:
[LIST]
[*]Firefox 3.5.2:	**1738**
[*]Opera 10:		**1439**
[*]Google Chrome 2.0: 	**1930**
[*]Google Chrome 4.0:	**2636**
[/LIST]

**Ubuntu 9.04 (64-bit)**:
[LIST]
[*]Firefox 3.5.2:	**772**
[*]Opera 10 (QT3):	**782**
[*]Opera 10 (QT4):	**879**
[*]Google Chrome 4.0:	**2080**
[/LIST]

_Conclusion:_
From the results we can clearly see that *Windows greatly outperforms Linux* when it comes to browser performance. The reason for this is probably the X windowing system, which is known to be very unresponsive and bad at rendering in general. In my opinion, this is one of the biggest issues with Linux. It is not directly noticeable, but greatly damages the overall desktop experience. The fastest / most optimized browser on Linux seems to be Google's Chromium, but even it is much slower on Linux.

Now I'm sure some people will refuse to believe these results. If you disagree, please do your own comparison and you will get similar results.

---

### Post by TheShader on 2009-09-04
Hmm I see. But what can we do? There is no other alternative than X windowing system, isn't it?

---

### Post by filip007 on 2009-09-04
Yes the speed is lower but it not effects anything maybe some heavy forms computing other stuff is just fine.

---

### Post by TheShader on 2009-09-04
By the way I tested my Chromium also. I'm on a Acer 2920Z. 2GB of ram, Intel Pentium Dual-Core 1.73Ghz, and Intel graphics(GM 965). I just tested Chromium 4.0.207.0, the result is 2216. Not that bad, isn't it?

---

### Post by GoldenSun on 2009-09-04
I just got a 1524 on a amd 4850e oc'd to 3ghz, 4 gb ram, hd3300 igp.
on firefox 3.5.2 on ubuntu 9.04 64.  Maybe your system isn't performing properly?

---

### Post by unimatrix on 2009-09-04
GoldenSun and TheShader: if you can, repeat the test on Windows using the same browsers. I assure you, you will get higher results.

GoldenSun: My system is performing properly. I have also done these tests on two other machines and got similar results. It would be quite a coincidence if all three were not performing properly.

TheShader: What can we do about it? Well I don't know, but a good start would be discussing the problem. That is my initiative by posting this here.
Also, there is an alternative to X. It's called Wayland, but I think it only works with Intel GPUs for now.

---

### Post by Tom Mann on 2009-09-04
Are you using the free driver or the nvidia one? if the nvidia one, default nvidia, envy or downloaded from nvidia's site?

I ask this as there has been known problems with nvidia drivers in X for a while...

---

### Post by unimatrix on 2009-09-04
> **Tom Mann said:**
> Are you using the free driver or the nvidia one? if the nvidia one, default nvidia, envy or downloaded from nvidia's site?

I ask this as there has been known problems with nvidia drivers in X for a while...

nvidia-glx-new from the repository

---

### Post by GoldenSun on 2009-09-04
I can't do it on windows, as I don't have it installed.  I could do it in a virtual box, but that would be a massive handicap on windows.  

Also, I don't think this matters too much in the os performance.  A good example here would be why does ubuntu get better results when using super pi on the same computer?  

Ubuntu can't be the best at everything.

---

### Post by unimatrix on 2009-09-04
> **GoldenSun said:**
> I can't do it on windows, as I don't have it installed.  I could do it in a virtual box, but that would be a massive handicap on windows.  

Also, I don't think this matters too much in the os performance.  A good example here would be why does ubuntu get better results when using super pi on the same computer?  

Ubuntu can't be the best at everything.

The reason why Ubuntu gets better results when using Super PI is because the Linux kernel kicks *** compared to Windows.
The problem is that graphics on Linux (particularly the X server) suck.

---

### Post by philinux on 2009-09-04
Using Karmic.

FF 3.5.2 = 1232
Chromium 4 = 2740

Yet FF displays sky news website renders than chromium.

---

### Post by unimatrix on 2009-09-04
Also, Ubuntu (and Linux) CAN and SHOULD be best at everything :)

---

### Post by Nepherte on 2009-09-04
I'm not denying any result, but ultimately benchmarks remain benchmarks. The only real performance measure is actual daily usage execution time and I don't experience that one os is faster than the other when we're talking about internet browsing.

In general, benchmarks can give very biased results. As soon as a program knows how to exploit a certain piece of benchmarking code so it can optimize these particular lines of code, the benchmark has become worthless.

---

### Post by GoldenSun on 2009-09-04
It's also hard to make an unbiased benchmark that is cross platform when they don't even use the same graphics drivers.  
dx10>opengl because that benchmark was optimized for windows machines.  
 They should make a linux only benchmark and compare other linux machines against one another.  Only then would it be fair.

---

### Post by unimatrix on 2009-09-04
> **Nepherte said:**
> In general, benchmarks can give very biased results. As soon as a program knows how to exploit a certain piece of benchmarking code so it can optimize these particular lines of code, the benchmark has become worthless.

Except this cannot be the case here, because we're using the same software. Unless you're saying all of them intentionally made those particular benchmarks score higher only on Windows. I find that unlikely.

---

### Post by unimatrix on 2009-09-04
> **GoldenSun said:**
> It's also hard to make an unbiased benchmark that is cross platform when they don't even use the same graphics drivers.  
dx10>opengl because that benchmark was optimized for windows machines.  
 They should make a linux only benchmark and compare other linux machines against one another.  Only then would it be fair.

The point is, everything (but especially browsing) feels much more responsive in Windows. For example closing a tab. It closes immediately on Windows, but on Ubuntu/Linux it feels like it's delayed for a very short moment before it actually disappears. Now I know it's not a big deal, but users who are used to immediate system responses will find this annoying.

---

### Post by philinux on 2009-09-04
I've never experienced an immediate system response from Windows except when it was first installed. Except vista which was slow from the beginning.

---

### Post by unimatrix on 2009-09-04
> **philinux said:**
> I've never experienced an immediate system response from Windows except when it was first installed. Except vista which was slow from the beginning.

I'm not talking about how fast software loads. That's already better on Linux. I'm talking about responsiveness in regards to the visual things like scrolling, opening/closing tabs etc.

---

### Post by GoldenSun on 2009-09-04
I have instant response when I press "ctrl + t" on ff 3.5.2 in ubuntu.  My windows machine on xp seems slower to me.  I also have a ramdisk for firefox in ubuntu, so that may help out a lot.

---

### Post by gordintoronto on 2009-09-04
> **unimatrix said:**
> _Computer specs:_
CPU: AMD 64 X2 Dual Core 4600+
MEM: 2.0 GB
GPU: nVidia GeForce 7900 GS (driver 180.44)

**Windows XP SP3 (32-bit)**:
[LIST]
[*]Firefox 3.5.2:	**1738**
[*]Opera 10:		**1439**
[*]Google Chrome 2.0: 	**1930**
[*]Google Chrome 4.0:	**2636**
[/LIST]

**Ubuntu 9.04 (64-bit)**:
[LIST]
[*]Firefox 3.5.2:	**772**
[*]Opera 10 (QT3):	**782**
[*]Opera 10 (QT4):	**879**
[*]Google Chrome 4.0:	**2080**
[/LIST]


My computer has an AMD Phenom II X2 550 processor and nVidia 9400 GT video card.  Here are my scores on Peacekeeper:
Ubuntu/Firefox 3.5: 1782
Windows 7/Firefox 3.5: 2495
Windows 7/Explorer 8: 1089.

Given that most Windows users will be using Explorer, my browsing is much faster.  There's also less percentage difference than you observed, between the same browser in the different environments.  The difference is that my computer has more CPU and less video power than yours.

All the best,
Gord

---

### Post by Tom Mann on 2009-09-04
> **unimatrix said:**
> nvidia-glx-new from the repository

This will be why - nvidia have been working to fix their drivers after a regression that hit 2d performance in KDE, maybe we're missing something on the render speed of Gnome too? Phoronix is our friend here.

Also, could you repeat the test with the latest alpha? We should look forward as well as back...

---

### Post by zenkaon on 2009-09-04
I agree strongly that something needs to be about X.org, it is far too slow.

At work I hook up my laptop to an external monitor, keyboard and mouse and then click a little button I have which runs
```

xrandr --auto

```
The performance of my laptop slows significantly when hooked up to the monitor, especially firefox.

I have a Dell Latitude D420 (2x1.2GHz 1GB RAM) Using repository intel drivers. Firefox 3.5.2. Debian Lenny (I know this is an ubuntu formum.....but ubuntu is tweaked Debain) X.org version 1.4.2

My Benchmarks for peacekeeper are:
Stand alone laptop = 562
Docked laptop = 246

OK so my performance isn't great anyway, but I am taking a 44% hit in performance by changing my 12" laptop screen to a 19" monitor.

---

### Post by zenkaon on 2009-09-04
Wow,

based on these peacekeeper benchmarks I suck google chrome on my laptop. I've only tested while docked so far, I'm sufficiently impressed and unless I see any hickups I've changed browser.

Firefox 3.5.2 just laptop = 562
Firefox 3.5.2 Docked to 19" = 246
Chrome 4.0.203.2 Docked to 19" = 1443

Goodbye firefox

---

### Post by SunnyRabbiera on 2009-09-04
Benchmarks should not be counted on as it really depends on your hardware.

---

### Post by Nepherte on 2009-09-04
> **unimatrix said:**
> Except this cannot be the case here, because we're using the same software. Unless you're saying all of them intentionally made those particular benchmarks score higher only on Windows. I find that unlikely.
You're forgetting the fact that browsers rely on remote procedures as well, inherent to the operating system. It is practically impossible to test the performance of the single application. Not to mention that the execution time can be separated in user time + system time.

You're also underestimating the value of scoring high in performance benchmarks. Companies would do everything to score high and hence get better sales. So yeah, a lot of companies intentionally forge better scores.

---

### Post by chriskin on 2009-09-04
sorry to say what is supposed to be said here
but using the sunspider ([http://www2.webkit.org/perf/sunspider-0.9/sunspider.html](http://www2.webkit.org/perf/sunspider-0.9/sunspider.html)) benchmark i found out that the same browsers are slower on my brother's Too-new-to-be-true ultra powerful desktop pc (wired connection)that runs on vista than my not-so-new laptop (wireless) that runs on ubuntu

so i just can't accept that chromium is faster over there than here :)

---

### Post by unimatrix on 2009-09-04
> **Tom Mann said:**
> This will be why - nvidia have been working to fix their drivers after a regression that hit 2d performance in KDE, maybe we're missing something on the render speed of Gnome too? Phoronix is our friend here.

Also, could you repeat the test with the latest alpha? We should look forward as well as back...

I suspected something like this, yes.
I shall repeat the test tomorrow with the latest drivers.

---

### Post by coldReactive on 2009-09-18
I just got 1683 in Peacekeeper on 3.5.3 Firefox myself. Then again, I have a 3.0 GHz Duo Core and 6 GB of RAM and a GTS 250 Graphics card with 1 GB Video RAM.

---

### Post by rookcifer on 2009-09-18
A lot of it has to do with how the browser was compiled.  Obviously, Windows and Linux use different compilers with different settings, etc.

I have seen benchmarks (on Phornoix I think) where it was shown that running Firefox in WINE was **faster** than running native Linux Firefox.  This shows there is some difference in how the code is compiled.

---

### Post by unimatrix on 2009-09-19
> **rookcifer said:**
> A lot of it has to do with how the browser was compiled.  Obviously, Windows and Linux use different compilers with different settings, etc.

I have seen benchmarks (on Phornoix I think) where it was shown that running Firefox in WINE was **faster** than running native Linux Firefox.  This shows there is some difference in how the code is compiled.

I've also benchmarked Firefox native and Firefox via Wine get about the same results. The one on Wine is slightly lower. Don't really care what Phoronix says, the fact remains that Firefox on Linux is still very unresponsive and much slower.

---

### Post by geoken on 2009-09-19
> **coldReactive said:**
> I just got 1683 in Peacekeeper on 3.5.3 Firefox myself. Then again, I have a 3.0 GHz Duo Core and 6 GB of RAM and a GTS 250 Graphics card with 1 GB Video RAM.

I have similar specs as you (C2D E8400 [3.0 ghz], 6 gb of ram, Nvidia 8800GTS 320.

With Firefox 3.5.3 on Win 7 rc x64 I got 2081 points. I'm not sure if it matters but I have a ton of extensions and had a FireFTP in another tab and a Firebug session in yet another tab (about 7 tabs were running at the time of the test).

With Chrome 3.0.195.21 I got 4101.

---

### Post by ChrT on 2009-09-19
I don't have a windows machine to compare, so I just ran the benchmark on firefox, then on uzbl.

Intel C2D E6700 (2.67GHz), Geforce 8800GTS 512, 2GB ram

Note how uzbl runs faster on a C2D than firefox runs on an i7.

This is the last straw, I'm ditching firefox here and now.

[[IMG]http://img182.imageshack.us/img182/7066/browserbenchmark.th.png[/IMG]]("http://img182.imageshack.us/i/browserbenchmark.png/")

---

### Post by mohtasham1983 on 2010-06-13
I know I am late a bit, but just wanted to say that Windows graphic environment is part of windows Kernel, while it is not the same with Linux. By having the graphical interface integrated into the kernel, you gain a lot of speed, but you will lose stability. That is unlike in Linux, when a windows app crashes, it may affect other open apps as well.

---

### Post by Diluted on 2010-06-13
> **mohtasham1983 said:**
> I know I am late a bit, but just wanted to say that Windows graphic environment is part of windows Kernel, while it is not the same with Linux. By having the graphical interface integrated into the kernel, you gain a lot of speed, but you will lose stability. That is unlike in Linux, when a windows app crashes, it may affect other open apps as well.
[WDDM](http://msdn.microsoft.com/en-us/library/aa480220.aspx) seems to disagree with you.

> At a technical level, WDDM display drivers have two components, a kernel mode driver (KMD) that is very streamlined, and a user-mode driver that does most of the intense computations. **With this model, most of the code is moved out of kernel mode.**
>  This greatly reduces the chance of a fatal blue screen and most graphics driver-related problems result in **at worst one application being affected.**

---

### Post by World Unknown on 2010-06-13
[IMG]http://pici.se/pictures/oquTGEvCq.png[/IMG]

7339
Chrome 5.0
Snow Leopard
3ghz
2gb ram
Dual core

---

### Post by Shining Arcanine on 2010-06-13
> **unimatrix said:**
> I have found this excellent browser benchmarking tool called [Peacekeeper]("http://service.futuremark.com/peacekeeper") and have decided to compare the results in Windows and Linux using the same browsers, on the same computer.
So let's go right down to it...

_Computer specs:_
CPU: AMD 64 X2 Dual Core 4600+
MEM: 2.0 GB
GPU: nVidia GeForce 7900 GS (driver 180.44)

**Windows XP SP3 (32-bit)**:
[LIST]
[*]Firefox 3.5.2:	**1738**
[*]Opera 10:		**1439**
[*]Google Chrome 2.0: 	**1930**
[*]Google Chrome 4.0:	**2636**
[/LIST]

**Ubuntu 9.04 (64-bit)**:
[LIST]
[*]Firefox 3.5.2:	**772**
[*]Opera 10 (QT3):	**782**
[*]Opera 10 (QT4):	**879**
[*]Google Chrome 4.0:	**2080**
[/LIST]

_Conclusion:_
From the results we can clearly see that *Windows greatly outperforms Linux* when it comes to browser performance. The reason for this is probably the X windowing system, which is known to be very unresponsive and bad at rendering in general. In my opinion, this is one of the biggest issues with Linux. It is not directly noticeable, but greatly damages the overall desktop experience. The fastest / most optimized browser on Linux seems to be Google's Chromium, but even it is much slower on Linux.

Now I'm sure some people will refuse to believe these results. If you disagree, please do your own comparison and you will get similar results.

The discrepancies here are not because of the X Windowing System. It is well known that Firefox is slower on Linux than it is on Windows:

[http://www.tuxradar.com/content/benchmarked-firefox-javascript-linux-and-windows-and-its-not-pretty](http://www.tuxradar.com/content/benchmarked-firefox-javascript-linux-and-windows-and-its-not-pretty)

This is due to compiler optimizations, in particular, Profile Guided Optimization; there is a bug report on this at Mozilla:

[https://bugzilla.mozilla.org/show_bug.cgi?id=418866](https://bugzilla.mozilla.org/show_bug.cgi?id=418866)

You can install the Windows version of Mozilla Firefox in WINE and run benchmarks to verify this. You will see that it runs faster in WINE on Linux than it runs natively on Linux. That alone destroys your argument that the X Window System is at fault because combination of poor native compiler optimizations and fact that the only way to avoid that is by using an emulation layer serves as a confouding variable in any argument that the X Window System is at fault. You would need to demonstrate that a native version of the application with proper compiler optimizations is in fact slower than the same application on Windows before the X Window System can be considered a suspect.

Also, to make matters worse, TraceMonkey support is not enabled in Firefox on 64-bit Linux. It is actually present in the source code, but it is not officially supported by upstream, so no Linux distribution's package maintainers enable it as far as I know, with perhaps the exception of Arch Linux. There is a bug report about this in Gentoo Linux's bug tracker, but the Mozilla maintainer for Gentoo Linux has no interest in pushing the envelope so to speak, so Gentoo Linux likely will not have this feature until it is officially supported by upstream:

[http://bugs.gentoo.org/show_bug.cgi?id=315997](http://bugs.gentoo.org/show_bug.cgi?id=315997)

If you were running 32-bit Ubuntu, you would have TraceMonkey enabled by default. I would say that 64-bit Windows suffers from the same problem, but there is no official 64-bit build of Firefox on 64-bit Windows, so it is difficult to say that Mozilla is favoring Windows in this respect, although the lack of official 64-bit support is likely because of Windows, as the majority of systems that run Firefox are 32-bit Windows, so 32-bit support is what receives the most attention from upstream.

On the other hand, Google Chrome/Chromium has many different versions that are all called 4.0. Just to name a few:

[LIST]
[*]4.0.249.43
[*]4.0.266.0
[*]4.0.295.0
[*]4.0.302.2
[/LIST]

Differences in the actual version of Chromium will likely affect the benchmarks. The discrepancy in your scores could be caused by running an older version of Chromium on your Ubuntu Linux system. I know this because I have a Windows 7 Professional 64-bit system with a 64-bit Gentoo Linux virtual machine running on top of it and I have run benchmarks on Chrome/Chromium 6.0.427.0 and the two of them perform at about parity with one another. While I am hesitant to say it, because of statistical margins of error, it appears almost as if Google Chromium inside the Gentoo Linux virtual machine runs faster than Google Chrome on Windows 7 Professional.

Another possibility is that Ubuntu's Google Chromium package maintainer does not compile Google Chromium with the correct compiler optimizations. That would be a Ubuntu-specific issue, which does not affect Linux in general. I use Gentoo Linux and made sure that my make.conf CFLAGS are optimal for my computer, so I do not have to worry about Google Chromium being compiled incorrectly. There was a slight issue with how it was being compiled on Gentoo Linux a few weeks ago, but I filed a bug report about it and the maintainer fixed it.

As for Opera, I am not sure why you are seeing a discrepancy. I really do not use Opera very much, so I never bothered to pay much attention to its performance. Perhaps you should ask Opera's developers why you are seeing a discrepancy.

Lastly, your perception that the X Window System is "very unresponsive and bad at rendering in general" is probably more because you run Ubuntu Linux than anything else, because having a responsive desktop environment requires a kernel with the following features:

[LIST]
[*]1000Hz clock with Dynamic Ticks
[*]Kernel Pre-emption
[*]RCU Pre-emption
[/LIST]

Ubuntu Linux as far as I know by default has a 250Hz clock with Dynamic Ticks and all forms of Pre-emption disabled. You can verify that kernel pre-emption is disabled by running [COLOR="Green"]uname -v[/COLOR] in a terminal. Here is what I get when I run [COLOR="Green"]uname -v[/COLOR] on my Gentoo Linux system:

> $ uname -v
#2 SMP PREEMPT Thu Jun 3 02:22:12 EDT 2010

The PREEMPT keyword indicates that Kernel Preemption is enabled. I think Canonical recently made a preemption enabled kernel available in its repositories. You might want to get that, although I do not know what it does in the other areas I mentioned. If it does not do things properly in the other areas, you could:
[LIST]
[*]Compile your [own kernel]("https://help.ubuntu.com/community/Kernel/Compile") and be ostracized by the Ubuntu support community for using it.
[*]Switch to a distribution that either supports user kernel compilation or requires it, such as [Gentoo Linux]("http://www.gentoo.org/").
[*]Switch to another distribution that has a properly compiled kernel by default. I think OpenSUSE is one of them.
[/LIST]

---

### Post by NightwishFan on 2010-06-13
Ubuntu Generic uses a 100hz clock with dynamic ticks and voluntary preemption on 64-bit and 250hz on 32-bit. It also has a preempt kernel which has 1000hz and more preemption, and finally realtime kernel (though it is 2.6.31 on lucid and not 2.6.32).

You can check the configuration in /boot. You can also use diff to see the differences between versions, or a gui such as [meld]("apt://meld")

---

### Post by Shining Arcanine on 2010-06-13
> **NightwishFan said:**
> Ubuntu Generic uses a 100hz clock with dynamic ticks and voluntary preemption on 64-bit and 250hz on 32-bit. It also has a preempt kernel which has 1000hz and more preemption, and finally realtime kernel (though it is 2.6.31 on lucid and not 2.6.32).

You can check the configuration in /boot

I did not know that dynamic ticks were enabled in Ubuntu kernels. I learned something new today.

From what I know, Ubuntu has traditionally only had its server (100Hz) and desktop (250Hz) kernels. Its preemption and realtime kernels are recent things, with the preemption kernel being the most recent addition. It did not exist until a few months ago.

By the way, do you know if RCU Preemption is enabled in the Ubuntu Preemption Kernel as well? If it has RCU Preemption is enabled too, then it should be perfect for the original poster. I have no idea what Canonical's developers were thinking when they decided to use a 250Hz Voluntary Pre-emption kernel for desktops, but whatever it was, it was a bad decision.

---

### Post by NightwishFan on 2010-06-13
It excels in both throughput and latency for me. I will make sure about the dynticks and rcu though. One moment.

---

### Post by NightwishFan on 2010-06-13
Lucid Generic Kernel:
```
CONFIG_TREE_RCU=y
# CONFIG_TREE_PREEMPT_RCU is not set
# CONFIG_RCU_TRACE is not set
CONFIG_RCU_FANOUT=64
# CONFIG_RCU_FANOUT_EXACT is not set
# CONFIG_TREE_RCU_TRACE is not set
```

I cant remember how to tell if dynticks is enabled, but I am pretty sure it is.

---

### Post by Shining Arcanine on 2010-06-13
I just realized that Dynamic Ticks has no effect on performance on Linux. What it does affect is power consumption. I enable Dynamic Ticks alongside a 1000Hz clock so often that I tend to forget that detail.

With that said, you can run [color=Green]zcat /proc/config.gz | grep CONFIG_NO_HZ[/color] to check the status of Dynamic Ticks on a kernel compiled with CONFIG_IKCONFIG, which if CONFIG_IKCONFIG=m like it is on my system, might require that you run [color=Green]modprobe configs[/color] first.

Anyway, while I enable RCU Preemption whenever I compile a kernel for a system running X because according to theory, it should have a positive effect on latencies like the kernel preemption, now that I think about it, I am not sure whether or not the time that the kernel spends in RCU-sections makes it an important enough feature that the lack of it is an issue because while RCU Preemption should lower latencies when the kernel is executing Read-Copy-Write sections of code, I have not seen benchmarks that quantify the extent to which that effect is important.  At the same time, considering how long it took for Canonical to even make a Preemption Capable kernel available from its repositories, it might not be a good to assume "Canonical does best" in this matter.

Anyway, the original poster will probably be much happier if he installed the PREEMPT kernel from Canonical's official repositories.

---

### Post by NightwishFan on 2010-06-14
I would think they wouldn't notice much (I never do) but I agree it would not hurt. The only thing I personally noticed the preempt helps with is audio on wine on some games.

---

### Post by Shining Arcanine on 2010-06-14
From what I have read on these forums, I suspect that preemption support would also help increase minimum frame rates in games, because before the preemption kernel existed, someone in another thread reported that using the realtime kernel improved minimum frame rates in his games.

---

### Post by NightwishFan on 2010-06-14
It may, but I have no conclusive evidence of this so I could not tell you.

---

