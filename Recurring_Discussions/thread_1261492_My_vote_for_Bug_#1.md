---
title: "My vote for Bug #1"
date: 2009-09-08
forum: Recurring Discussions
---

### Post by MountainX on 2009-09-08
I don't dispute that "Microsoft has a majority market share" is bug #1 in the long term, but I think the biggest and most important bug in Ubuntu that needs attention right now is the fact that all the popular web browsers run slower under Linux than they do under Windows.

For example, see [http://service.futuremark.com/peacekeeper/browserStatistics.action](http://service.futuremark.com/peacekeeper/browserStatistics.action)

I'm running Swiftweasel and Chromium under 64bit Jaunty and I have tried the relevant suggestions at this thread:
[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

It is really unsatisfactory that I have to suffer a serious performance penalty for running Ubuntu.

---

### Post by HappyFeet on 2009-09-08
Firefox and opera are fast for me. No problems here. Next!

---

### Post by MountainX on 2009-09-08
> **HappyFeet said:**
> Firefox and opera are fast for me. No problems here. Next!

I'm sorry, but you are just not informed. That's like saying a Pentium-2 is fast. 

If you are running Linux your browsers are slower than they would be on your same computer running Windows (even Vista). I'm not planning to switch back to Windows, but I would like to see this "bug" addressed so I don't have to envy my buddies who run Windows.

---

### Post by Viva on 2009-09-08
> **HappyFeet said:**
> Firefox and opera are fast for me. No problems here. Next!

I can confirm this too. The startup time in firefox is slightly higher compared to windows, but I find the general browsing faster and the browser itself faster and more stable compared to windows.

---

### Post by amauk on 2009-09-08
In the past, I've had problems with the ~/.mozilla config directory filling up with cruft, and bogging FF down

It's only happened twice, but worth looking into

I've kept the same home folder for many years, and the .mozilla directory has been through all versions from 1.5 to 3.5

I've never managed to track down exactly what the problem was, but FF **really** slowed down.

Try backing up your bookmarks (and extensions)
close FF
then remove the .mozilla directory
then restart FF, see if it performs better

---

### Post by Tamlynmac on 2009-09-08
> Viva
I can confirm this too. The startup time in firefox is slightly higher compared to windows, but I find the general browsing faster and the browser itself faster and more stable compared to windows.

Another conformation.

Firefox on my P4 runs faster than my neighbors Intel Dual-Core 2.66 with XP, both using the same identical cable modem and company.  We've gone to the exact same site and timed both machines. >90% of the time my system loads the site 2 to 5% faster. When downloading a file, my system completes a web file download in about 2% faster (on average via FF. We confirmed that both FF installs have the pipeline settings, (about:config), etc.

I've read some of the bug reports that identify the difference in speed between FF in Windows & Linux, but have not experienced the problem. A number of friends have used my cable modem to download data to their (Windows) laptops via FF and their browsing speeds are almost identical to mine. Have yet to experience slower FF speeds on any of our home systems when comparing. Of course these are simple comparrisons and not to be mistaken for actual benchmarks.

The only difference I've witnessed is when using flash. I have noticed that flash videos seem to load slightly quicker in Windows. But it was not more than a couple of seconds. To be honest, this means little to me as I don't spend much time watching web videos. However, if that were a priority a couple of seconds wouldn't have an effect on us and I don't see it as the #1 bug.

---

### Post by MountainX on 2009-09-08
It's one thing to speak about a subjective feeling, but quite another to verify the speed with benchmarks.

Try something like this:
[http://service.futuremark.com/peacekeeper/browserStatistics.action](http://service.futuremark.com/peacekeeper/browserStatistics.action)

You'll see that FF is slower under Linux. And not just a little slower - a lot!

---

### Post by cariboo on 2009-09-08
I just ran the same test as the op did, Firefox 3.5 comes in 3rd behind two browsers that don't even run on a Linux variant. I'm running Karmic Kola on a 3 year old AMDX2 3800+ w/3 Gb ram and a Nvidia 8400GS video card. See screenshot.

If you look, they got the top result with a quad core Intel cpu w/6Gb ram and a GT250 with 1Gb ram

---

### Post by MountainX on 2009-09-09
> **cariboo907 said:**
> I just ran the same test as the op did, Firefox 3.5 comes in 3rd behind two browsers that don't even run on a Linux variant. I'm running Karmic Kola on a 3 year old AMDX2 3800+ w/3 Gb ram and a Nvidia 8400GS video card. See screenshot.

If you look, they got the top result with a quad core Intel cpu w/6Gb ram and a GT250 with 1Gb ram

You sure you're reading that right?

It looks like ***your*** overall score for Firefox 3.5 a **1029**. That's what it looks like from your screen shot. Look at the top. (BTW, click "Details" and you can see more info and also copy/paste the text.) 

A score of 1029 totally sucks. I guarantee your hardware can achieve browser speeds at least twice that fast! Notice that the average Firefox 3.5 speeds are around 2200 to 2500 (on Windows).

Notice that your score of 1029 is as bad as IE8 on Windows.

And that's my whole point. When we choose to run Ubuntu, we should not be sentenced to slow browsers.

---

### Post by running_rabbit07 on 2009-09-09
Is there a bench mark comparing the speed of FF3.5 on Ubuntu 9.10 and Windows 7?

I have W7 installed but I didn't give it permission to connect yet in my Virtual Box until I get Karmic 64 bit installed permanently.

> **MountainX said:**
> And that's my whole point. When we choose to run Ubuntu, we should not be sentenced to slow browsers.

My FF isn't running slow.

---

### Post by Tamlynmac on 2009-09-09
> MountainX
It's one thing to speak about a subjective feeling, but quite another to verify the speed with benchmarks.

**As I indicated in my response**, the comparisons we made were simple and should not be considered benchmarks. I can only address my own systems and those that have used my cable to make the comparison.

The comparisons indicated, the speed of FF on my Ubuntu/Linux systems was comparable to those of others who have used my cable to access the web and had FF installed with Windows.

I cannot, nor would not speak for others. But after investing time in the Help Sections of this Forum, (IMHO) the issues/bugs related to Video and Audio are substantially more important than the potential FF issue.

---

### Post by jolx on 2009-09-09
my virtualised windows 7 perfomed worse than my virtualised arch, even though arch had less resources. Windows 7 had 896 MB memory and 128 MB graphics memory, arch had 512 and 64.

and on my arch host the test scored 1497

---

### Post by Marflus on 2009-09-09
> **MountainX said:**
> It's one thing to speak about a subjective feeling, but quite another to verify the speed with benchmarks.


Quite correct, it is. 

But, who cares about the what score their browser achieves on a benchmark, really? You've seen the vast majority of people on this thread thought Firefox was easily fast enough before they bothered going to check a benchmark.

Suppose you've just come over from Windows. You see that the browser is Firefox, something you know well and enjoyed using whilst running Windows. Now at this point, you run it. Should you feel it's really slow, then sure, you're not going to be happy, and perhaps you might run a benchmark. As it is, though, peoples "subjective feelings" tend to be good, and they don't really care about running a benchmark since they're entirely happy with the speed of the browser.

Ok, so even if Firefox does run a bit slower than Windows on everyone's machine (which according to the stories seems debatable in many cases), why does that matter? I don't care if Firefox takes 0.001 of a second more to load a page, since to me the speed seems absolutely fine.

---

### Post by adrianx on 2009-09-09
I'm just wondering, how reliable are these "futuremark" people's benchmarks, anyway? They look pretty and everything.... :D

---

### Post by fela on 2009-09-09
This bug is FUD, at least it's not reproduceable, or Ubuntu is causing it.

I ran firefox 3 on DamnSmallLinux on a pentium II 266MHz computer that's now broken (BIOS corrupted, mobo fried, about a decade old I think).

It ran faster for general web browsing than firefox 3 runs on windows on my current computer which is in my signature. Also on my current computer I run konqueror normally (that's what I'm on now) - which is WAY faster than any browser (even chrome) that I use on vista when I (rarely) boot into it. Current distro is Debian Squeeze btw with KDE4.2.

---

### Post by Arup on 2009-09-09
I have totally opposite experience with all the PCs I have installed Ubuntu in, even my friends have the same experience as I have, they are all ex Windows users or still dual boot. FF is usable in Ubuntu unlike in Win and latest Opera 10.10 beta just blazes, in case of Opera it matches the speed I get in my Windows installation.

---

### Post by armandh on 2009-09-09
but they do seem to be working hard on that bug
[http://arstechnica.com/microsoft/news/2009/09/microsoft-teaches-best-buy-employees-how-to-troll-linux-users.ars](http://arstechnica.com/microsoft/news/2009/09/microsoft-teaches-best-buy-employees-how-to-troll-linux-users.ars)

---

### Post by mdsmedia on 2009-09-09
> **Marflus said:**
> Quite correct, it is. 

But, who cares about the what score their browser achieves on a benchmark, really? You've seen the vast majority of people on this thread thought Firefox was easily fast enough before they bothered going to check a benchmark.

Suppose you've just come over from Windows. You see that the browser is Firefox, something you know well and enjoyed using whilst running Windows. Now at this point, you run it. Should you feel it's really slow, then sure, you're not going to be happy, and perhaps you might run a benchmark. As it is, though, peoples "subjective feelings" tend to be good, and they don't really care about running a benchmark since they're entirely happy with the speed of the browser.

Ok, so even if Firefox does run a bit slower than Windows on everyone's machine (which according to the stories seems debatable in many cases), why does that matter? I don't care if Firefox takes 0.001 of a second more to load a page, since to me the speed seems absolutely fine.
Agreed. I find Firefox occasionally annoying in both Windows and Linux, but I find that other browser in that other OS exceedingly annoying.

I like Opera, but it crashed on me at a critical moment, and I mean just decided to disappear when I ran it as an alternative to Firefox, which appeared to be running slowly for me at the time.

"Sentenced to running a slow browser" is rather a strong indictment when you consider what we're "sentenced" to put up with in the other OS as a matter of course.

Having a "slower" browser can hardly be considered "bug #1" when most serious problems involve hardware compatibility, which directly stems from bug #1.

---

### Post by scottuss on 2009-09-09
I'd say that the **_ possibly slightly_** slower browser start-up time is well worth the additional benefits of running your browser on Linux.

Malware, anyone?

---

### Post by howefield on 2009-09-09
> **MountainX said:**
> You'll see that FF is slower under Linux. And not just a little slower - a lot!

You'll need to help me out here, where in the link that you posted does it give information about a browsers speed in relation to the platform it is running on ?

---

### Post by thiebaude on 2009-09-09
Opera 10.10 is fast, just as fast on XP, when i had XP on this computer, i don't no more.FF is alot slower at booting up in Ubuntu than XP for me.FF in Ubuntu about 10 secs to get to my home page, where as in Opera on Ubuntu I'am on my home page in 3 secs.

---

### Post by GodLikeCreature on 2009-09-09
I honestly didn´t know about this as a fact, but I admit I had the feeling that Firefox was a bit slower under my linux PCs.  The thing that is confusing is that browsing experiences are not limited to the browser performance, but to many other elements as well.  I think Ubuntu´s overall better performance can make up a bit of the gap, so the user´s perception is that Firefox (for example) is as fast or faster under Ubuntu, when it isn´t.

Having said so, while I agree that browsing top speed is desirable, I very much disagree it would be the number 1 bug or priority.  I think Ubuntu should try to close the gap in other fronts first.

---

### Post by MountainX on 2009-09-09
> **howefield said:**
> You'll need to help me out here, where in the link that you posted does it give information about a browsers speed in relation to the platform it is running on ?

You have to do the tests. I'm sure you'll see that most browsers are at least twice as slow under Linux on equivalent hardware.

With so many vital services offered through the browser now, this issue is not just one of many "bugs" to consider. It is important. And I can't think of any other area where Windows kicks Linux's butt like this. That's why I think it is such an important thing to resolve.

[I][SIZE="1"]"Never argue with an idiot, 
they drag you down to their level
and beat you with experience."[/SIZE][/I]

---

### Post by sublimespot on 2009-09-09
Here is a video I made of my slow issue with Firefox on Ubuntu

[http://www.youtube.com/watch?v=bLZJcqxC0HA]("http://www.youtube.com/watch?v=bLZJcqxC0HA")

---

### Post by howefield on 2009-09-09
> **MountainX said:**
> You have to do the tests.

I guess that is what I'm struggling with, I do that how, exactly ?

As far as I can see, the only platform this test is designed to evaluate on is Windows.

---

### Post by fela on 2009-09-09
It's less than a second to open my browser (konqueror) on Linux, and that's when it's freshly booted up. It's so fast as it's preloaded into memory automatically.

On windows vista fresh bootup, firefox takes an age (about 10 seconds) to start up (on linux iceweasel is about the same), and Chrome takes about 2 seconds.

This means that the browser with the fastest startup time that I've found, runs on Linux and not windows.

Next bug #1 contestant please.

---

### Post by adrianx on 2009-09-09
> **sublimespot said:**
> Here is a video I made of my slow issue with Firefox on Ubuntu

[http://www.youtube.com/watch?v=bLZJcqxC0HA](http://www.youtube.com/watch?v=bLZJcqxC0HA)
That looks more like your video driver. Get another card... (or OS) :D. That's not Firefox's fault. I don't have that problem at all.

---

### Post by MountainX on 2009-09-09
> **howefield said:**
> I guess that is what I'm struggling with, I do that how, exactly ?

As far as I can see, the only platform this test is designed to evaluate on is Windows.

Sorry, I didn't understand you previously.

The [PeaceKeeper]("http://service.futuremark.com/peacekeeper/index.action") test does show your results for Linux (see the top section of the report). It just doesn't scan Linux systems. What I did was boot up Windows (not in a VM) and run the tests, then boot up the same system with Ubuntu and run the tests again. I also compared my results with a bunch of friends with various systems.

Here is a really good article about a guy doing several benchmarks: [http://allredb.wordpress.com/2009/05/07/speed-up-flash-and-firefox-in-ubuntu-jaunty-904/](http://allredb.wordpress.com/2009/05/07/speed-up-flash-and-firefox-in-ubuntu-jaunty-904/)

Here's a good thread on our own Ubuntu forum:
[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

And this might interest you:
[http://www.reddit.com/r/linux/comments/9hl7j/care_to_share_your_browsers_benchmarks_click_on/](http://www.reddit.com/r/linux/comments/9hl7j/care_to_share_your_browsers_benchmarks_click_on/)

---

### Post by lancest on 2009-09-09
Firefox starts very quickly on Jaunty 64 for me. In the past I have noticed much faster download speeds using Linux than on Windows XP. (Linux has a more aggressive TCP/IP scheme than XP). I won't be able to talk about Vista or 7 since THANKFULLY I never had to use them.

---

### Post by MountainX on 2009-09-10
Seriously, you guys (as a group of Linux users) are smarter than this!?

Browser performance is not the same as download speed or even necessarily application startup time.

It seems like there is a lot of misunderstanding or denial in this thread. Get with the program guys. I'm sure you can understand the benchmarking. Linux should not suffer from slow browser speeds (and denial only makes the issue persist).

I'm with you - I want to be 100% rid of Microsoft. I also want Ubuntu to perform up to its potential, especially with the application that is typically used more than any other -- the browser.

---

### Post by HappyFeet on 2009-09-10
> **MountainX said:**
> 
It seems like there is a lot of misunderstanding or denial in this thread. Get with the program guys.

So I should agree with you just because *your* browser may be a bit slower? Don't you have anything more important to worry about? Threads like this are getting real old, real quick. If you don't like something, help make it better. Btw, this is not the proper place to report things. Threads like this only cause more problems than solve them. 

If I started a thread about everything I did not like in this world, I would be on the computer 24/7. Crying about something in this forum will not change anything, no matter how good your intentions are.

Btw, my firefox runs very quickly. Even if it was *slower* (according to benchmarks), it would not concern me, as there is nothing I will do about it, and have more pressing concerns in my life. You are nitpicking and need to get over it. Perhaps the windows world is where you belong.

---

### Post by fela on 2009-09-10
> **HappyFeet said:**
> So I should agree with you just because *your* browser may be a bit slower? Don't you have anything more important to worry about? Threads like this are getting real old, real quick. If you don't like something, help make it better. Btw, this is not the proper place to report things. Threads like this only cause more problems than solve them. 

If I started a thread about everything I did not like in this world, I would be on the computer 24/7. Crying about something in this forum will not change anything, no matter how good your intentions are.

Btw, my firefox runs very quickly. Even if it was *slower* (according to benchmarks), it would not concern me, as there is nothing I will do about it, and have more pressing concerns in my life. You are nitpicking and need to get over it. Perhaps the windows world is where you belong.

Plus One

---

### Post by lancest on 2009-09-10
Browser rendering is so critical? I think not.

Especially when on average, a PC connected to the Internet is attacked every 12-15 mintues!

In my view it's far more important to focus on which browser (and OS) can offer better protection. Boring yes I know...

Theres no way I'm ever using Windows just because a browser running on it might be a hair faster. Is it more secure? 

Point is moot, improvements in Linux browsers at Google and Mozilla are ongoing.

---

### Post by Tamlynmac on 2009-09-10
> HappyFeet

If I started a thread about everything I did not like in this world, I would be on the computer 24/7. Crying about something in this forum will not change anything, no matter how good your intentions are.

+2
The truth... :lolflag:

---

### Post by adrianx on 2009-09-11
For me, Firefox is much faster in Linux than in Windows (I have only tested it in XP, though). In XP, IE7 outperforms Firefox (believe it or not), but in Linux, Firefox is much faster than IE7. Maybe it is a hardware thing - I don't know. 

Another thing that I don't understand is the performance of Opera 10 on my pc. In Fedora, Mint, Jaunty and Windows, Firefox is faster! According to everything I've read, that should not be the case, but still, that is how it is for me.

---

### Post by Grenage on 2009-09-11
> It's less than a second to open my browser (konqueror) on Linux, and that's when it's freshly booted up. It's so fast as it's preloaded into memory automatically.

On windows vista fresh bootup, firefox takes an age (about 10 seconds) to start up (on linux iceweasel is about the same), and Chrome takes about 2 seconds.

This means that the browser with the fastest startup time that I've found, runs on Linux and not windows.

Next bug #1 contestant please.

How is a browser pre-loaded into memory vs disk access a fair comparison?  Let's next test an Ubuntu install on a single SATA drive against a Windows RAID5, plan!

My XP and Vista installs both boot faster than Ubuntu, the browsers also load a _lot_ faster.  Once running, they perform fine.

---

### Post by Marflus on 2009-09-11
> **MountainX said:**
> And I can't think of any other area where Windows kicks Linux's butt like this. That's why I think it is such an important thing to resolve.

Tried running Crysis on Ubuntu recently? I get a fairly significant slowdown, to the extent that it hasn't done anything yet, and I double clicked setup.exe last month...*

A slowdown in a browser that the majority seem to not be experiencing is absolutely nothing compared to all the hardware issues many users get, and also as I just pointed out, windows applications that are necessary to many people's work, or indeed entertainment, do not run on linux.

Take that into context. You work in some office somewhere, using say, AutoCAD to produce some designs for some company. You like the look of ubuntu, but AutoCAD is 100% necessary for your work, and you've also heard that web browsing might slow down a bit if you switch OS.

Suppose then you hear web browsing is no longer a problem. Do you then switch? No.

Suppose the above has not happened, and web browsing is still a bit slower. You hear that AutoCAD runs on linux now. Do you then switch? Not such a forgone conclusion anymore.

*Ok, so I didn't actually do this. Crysis would struggle to run on my computer even if I *did* have Windows installed. You take the point, though ;)

---

### Post by SeePU on 2009-09-11
> **MountainX said:**
> Sorry, I didn't understand you previously.

The [PeaceKeeper]("http://service.futuremark.com/peacekeeper/index.action") test does show your results for Linux (see the top section of the report). 
WHERE?   I don't see it.

The FAQ of PeaceKeeper even reports that their scans don't support Linux.  It also doesn't mention Linux again as far as I can tell.  

So, how do you run the tests in Linux?  Use WINE or something?  If so, of course, it's very possible it will be slower (when browser scanning).

---

### Post by adrianx on 2009-09-11
> **SeePU said:**
> WHERE?   I don't see it.

The FAQ of PeaceKeeper even reports that their scans don't support Linux.  It also doesn't mention Linux again as far as I can tell.  

So, how do you run the tests in Linux?  Use WINE or something?  If so, of course, it's very possible it will be slower (when browser scanning).
Yes, I can confirm this - from their FAQ:
> [SIZE=2]**Why are there no Linux/Mac/Other lists of the top scores?**[/SIZE]

Currently, our system scan technology only works on Windows PCs. Without knowing the hardware details of a system, the performance score alone is not enough to create a list of top scores.
... and the rest of the benchmark test is probably not all that reliable.

---

### Post by Sef on 2009-09-11
This is a recurring discussion; hence, the move.

---

### Post by juancarlospaco on 2009-09-11
**Is not True, Adobe Flash is Slow, not Browsers.**
*Dont install the Adobe thing and see the diference...*

---

### Post by doorknob60 on 2009-09-11
I **know** FF is **a lot** faster for me in Arch than in Windows 7. In WIndows 7, it will randomnly freeze up for a few seconds every 30 seconds or so, and overall it's very sluggish. See my sig for specs, it's a good system. I tried FF safe mode too, same thing. Opera and Chrome work fine and fast on Windows, but they don't feel any different than in Linux. I've never had issues with browser speed in Linux, even with craploads of extensions installed. Also maybe it's Flash, that tends to slow things down sometimes :)

---

### Post by purgatori on 2009-09-11
So pages render slightly slower in Ubuntu than they do in Windows? Don't say it's true!! Lower resource usage means a lot more to me I'm afraid.

---

### Post by Tamlynmac on 2009-09-11
> Sef
This is a recurring discussion; hence, the move. 	

Thank You.

---

