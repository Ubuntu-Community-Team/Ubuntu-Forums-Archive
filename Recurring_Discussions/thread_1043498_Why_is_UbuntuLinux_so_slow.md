---
title: "Why is Ubuntu/Linux so slow?"
date: 2009-01-18
forum: Recurring Discussions
---

### Post by memories on 2009-01-18
First, I have been using Linux exclusively for the past 6-8 years. I will probably continue to use Linux if I don't switch to OS X (has nothing to do with performance, I just like Mac). Let's please keep the *Windowz is Lame* mentality out of this.

I recently upgraded my hardware to an Intel Q6600/8 GB of RAM/EP45-DS3L/Geforce 8600 GT. 

I have been toying with OS X / Windows XP SP1 and Ubuntu Hardy on my box for the past week. I actually booted into Windows for the first time in years just to see how my hardware performs. 

Here's what I noticed. 


**GUI Response**
The desktop/GUI response on XP and Aqua (Mac) is damn fast. It's instant. Linux IMO has always been sluggish in this area, but this is probably due to Xorg/Gnome/KDE. 

There's a noticeable delay between when I press a button and a terminal window open. It's VERY quick on Linux, but it's just much quicker on Windows or OS X. 

There's an option in the Kernel to speed up desktop response time, IIRC. I'll recompile my kernel in a sec. I'm using 2.6.27-9-generic #1 SMP.


**Internet**
I have disabled IPV6 and browsing the Internet in Ubuntu is still pretty slow, relative to the other OSes. I wasn't surprised to find that OS X was super quick but I just thought it was due to Safari (recommended!). But Firefox in XP also outperforms Firefox in Ubuntu (same version, same extensions). I know FF in Linux has always been sluggish but the difference is huge!

Opening Firefox is also 10x slower in Linux IMO. All machines were tested using the same NIC/ethernet. No wireless tests were done.


**Geekbench (Higher is better)**
The results were surprising. My score in Linux and Windows is around the same, hovering near 4800 even with nothing running (services/daemons off etc). But it can break 6000 easily in OS X.. and this is OS X 10.5.2 installed on non-Apple hardware probably with some ghetto drivers. I'm not sure why, though, because Geekbench tests mainly the CPU/RAM. Anyone know? 

Only 32bit was tested. ubuntu is 64bit, osx is 32bit w/ 64bit extensions and XP is 32bit. 


Your thoughts?

---

### Post by bapoumba on 2009-01-19
> **memories said:**
>  But it can break 6000 easily in OS X.. and this is OS X 10.5.2 installed on non-Apple hardware probably with some ghetto drivers.
Please keep that off the forums, it is against [Mac OS X license]("http://www.apple.com/legal/sla/macosx.html"), thanks.
> This License allows you to install and use one copy of the Apple Software on a single Apple-labeled computer at a time.

---

### Post by HermanAB on 2009-01-19
Your problems are likely due to a lame DNS.  Check /etc/resolv.conf and test the nameservers using digg.  Then put the fastest one at the top of the list.  You could also install BIND as a caching only name server, slaved to your ISP name server.  That will make most all lookups resolve instantly.

Cheers,

Herman

---

### Post by Simian Man on 2009-01-19
I agree that a full Gnome or KDE desktop is usually slower than a fresh install of Windows.  However the Gnome or KDE desktop will be just as fast 6 months later whereas Windows tends to get slower the more you use it.

You can try disabling compiz, disabling services you don't need or using a lighter desktop environment such as Xfce (which is closer to the Windows desktop in terms of functionality and at least as quick).

---

### Post by Yashiro on 2009-01-19
> Opening Firefox is also 10x slower in Linux IMO
Not true. FF on Windows does seem faster though, yes, but it's probably attributable to the whole desktop being a bit slower.

That said you must have some issues somewhere as my now tweaked Ubuntu is blazingly fast.
Much better than my XP when under average load, anyway.

---

### Post by Gondee on 2009-01-19
I agree with you on the firefox. Linux firefox opens sluggish and just moves around sluggish. In windows it seems to be quick and instant. It looks to me that the firefox in a virtual box (windows) is faster than linux firefox. This really disapointed me when i started using linux, but now that i leave everything open most the time, its not that bad.

---

### Post by Yashiro on 2009-01-19
It's not *that* much slower. If it is, you have something up somewhere. 
On first load, possibly, but during use? No real difference.

---

### Post by DeMus on 2009-01-19
> **Gondee said:**
> I agree with you on the firefox. Linux firefox opens sluggish and just moves around sluggish. In windows it seems to be quick and instant. It looks to me that the firefox in a virtual box (windows) is faster than linux firefox. This really disapointed me when i started using linux, but now that i leave everything open most the time, its not that bad.

I really have no idea what you all are talking about. I use Hardy Heron with Firefox and it works fantastic. It's not slow, it starts normal, pages are shown in a normal way, there is absolutely nothing slow here.
Okay, I have a nice PC, but it is running 4 instances of a program which use the 4 cores of my processor 100% all the time and still I can do everything in a normal way with Firefox.

---

### Post by HermanAB on 2009-01-19
Note that if someone complains that his system is slow, then you have to accept that it really is slow - if it wasn't, why would he bother to complain about it?

So, assuming that his FF system IS slow (but everything else is normal), then the most common problem is due to a lame DNS, as I pointed out above.

Another problem may be that his system is generally slow, due to a bad task running all the time, consuming CPU time.  This can be verified using a utility like 'top'.
$ sudo top

All heavy consumers should list at the top and that will give you an idea of what is the matter.

Cheers,

Herman

---

### Post by adamlau on 2009-01-19
Ubuntu is not slow, rather it is a combination of X, your chosen DE and the lack of hardware support for the latest and the greatest. More X and the DE than anything. Multiple toolkit libraries compound the issue as well. And yes, Opera for Windows is noticeably more responsive than Opera for Linux :( . For now :) .

---

### Post by Andreas1 on 2009-01-19
just because i am curious: is the overall ubuntu performance similar to comparable distros like, say, fedora, or others with gnome?

i recently found this [guide]("http://distrowatch.com/weekly.php?issue=20081215#feature") at distrowatch, do you think this might actually yield some performance? i sometimes wonder how many resources of my poor old laptop are wasted on it being able to do things i never intended to do. i mean i don't even have a printer. or are those things irrelevant compared to what the desktop environment eats up?

---

### Post by DeMus on 2009-01-19
> **HermanAB said:**
> Note that if someone complains that his system is slow, then you have to accept that it really is slow - if it wasn't, why would he bother to complain about it?

So, assuming that his FF system IS slow (but everything else is normal), then the most common problem is due to a lame DNS, as I pointed out above.

Another problem may be that his system is generally slow, due to a bad task running all the time, consuming CPU time.  This can be verified using a utility like 'top'.
$ sudo top

All heavy consumers should list at the top and that will give you an idea of what is the matter.

Cheers,

Herman


What I was trying to say is, here Ubuntu, and also programs like Firefox, are not slow. Meaning there must be something wrong with his hardware or with the installation, because Ubuntu can be fast. It's not that I don't believe "memories" when he writes it.
Since he also writes OSx and Windows perform better on his computer it must be the installation of Ubuntu which slows him down. Agree?

Use System Monitor to find out if there is a process or program which uses a lot of the processor capacity. Click the process tab.
Before looking at the data make sure you view all processes, including the system ones.
View | All processes.
Then click on the button on top of the list which says % CPU and do it again to have the text followed by a ^. This way the processes which use most are on top of the list.
Is there something using way too much?

Click the Resources tab and see how much memory you are using and if you use your swap memory as well. This might also slow you down since a hard disk is much slower than ram memory.

Just write down the results to find out what is causing your problems.

---

### Post by txcrackers on 2009-01-19
One issue may be that of perception. "Slowness" is strictly a subjective measurement - unless you sit there with a stop-watch and repeat over and over and over until you get a statistically significant sample. (Even then, you'd have to try to take into account programs that buffer or cache information, which tends to speed them up on subsequent invocations.)

Also, many Windows-based programs *are* "faster" on Windows because a huge chunk of what those programs need to do are already loaded by the OS (compare actual **OS** memory footprints). The GUI is integral to the OS, not running on "top" of it. Windows, typically being the first installation on the hard-disk, can find programs in it's disk-space faster due to less seek-time. Hardware drivers are more highly optimised for Windows. And so on.

Once you get adjusted to the fact that Linux Is Not Windows, you stop paying attention to the subjective differences and just start using it.

---

### Post by vs8 on 2009-01-19
Hi, I own a Gateway GT5676 4gb RAM, 2 320gb Sata HDDs, AMD Phenom 9600 Quad Core, ATI Radeon HD 3200. I use Vista and Ubuntu 8.10 with kernel 2.6.27.11.

 There's not much difference in boot time. But ion overall performance Vista is more polished than Ubuntu. It's GUI is more responsive, the file manager is faster and it's a smoother experience.

 In terms of applications they open at the same speed in both and the internet feels equally fast. The problem in Ubuntu is that when you scroll up and down it gets kind of stock for a few milliseconds and even when you stop pressing the left button on your mouse firefox still scrolls when you move the mouse around. It's crazy but I think it's a FF bug anyway because Opera doesn't do that. Another thing is smooth scrolling which is not existent because when you enable it, it gets even slower and it's not smooth at all.

Flash and Java are slower than a turtle, but that's not Ubuntus fault.

Torrents work perfectly in both OSs, I use port 40072, which is uTorren't default port and it works very fast.

I noticed that Compiz makes the whole system slower. The Compiz Fusion devs should work to make it lighter with every iteration. Mac and Vista integrate desktop effects and the system still runs very fast.

Gnome is just a slowpoke. It loads slow and performs slow and it needs more polish. I know it's lighter than Windows Explorer and Vista's Aero theme but still is very slow and that is a huge problem. 

I hope that Jaunty fixes most performance problems and gives us a smoother Ubuntu experience.

---

### Post by Rainstride on 2009-01-19
im using 9.04(A3) and so far im seeing proformance gains boots seems faster, and programs seem to load faster. it should very fast once its done. so far some of my programs are working way better.

---

### Post by vs8 on 2009-01-19
Awesome! Can't wait for Jaunty!

---

### Post by dabl on 2009-01-19
Yep -- what txcrackers said.

[http://rudd-o.com/en/linux-and-free-software/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that](http://rudd-o.com/en/linux-and-free-software/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that)

:)

---

### Post by bodhi.zazen on 2009-01-19
> **HermanAB said:**
> Note that if someone complains that his system is slow, then you have to accept that it really is slow - if it wasn't, why would he bother to complain about it?

<clip>

Cheers,

Herman

I agree with what you are saying , I think it is all in the title.

"Help, my system seems slow" seems to elicit help 

But general titles such as "Why is Ubuntu/Linux so slow?" attracts trolling as it begs a comparison, as in the OP question, why is Ubuntu/Linux so slow compared to OSX and Windows.

And like all such threads, there is a single post, with a flurry of posts from the community, with no follow up from the OP.

As such this thread seems more appropriate for recurring discussions rather then the support sections 

-> Thread moved :twisted:

---

