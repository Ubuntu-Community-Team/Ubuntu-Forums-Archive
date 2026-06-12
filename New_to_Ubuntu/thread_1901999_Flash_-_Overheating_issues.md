---
title: "Flash - Overheating issues"
date: 2011-12-29
forum: New to Ubuntu
---

### Post by Krabby.Linux on 2011-12-29
I have some Heat Problems with my Dell Notebook.

Everythin seems to be fine until I start watching videos i.e. on youtube. Watching these videos for some minutes will increase the temperature of my notebook. Its actually very hot, i cant even touch the bottom of my notebook for a few seconds because its to hot. Probably ~60°C or 110°C+ on the graphics card chip.

I think it is the graphics card in combination with flash. What can i do to avoid this problem?

---

### Post by zielstep on 2011-12-29
There are several quick ways to improve the laptop cooling.  


[LIST=1]
[*]Buy a laptop cooler that will work for your computer.  Some have fans designed to cool the laptop, others simply elevate the laptop so that the internal fans can suck in air to cool the inside of the system.  It depends on your computer on which route you will go.  There are also varying degrees of coolers that you can buy, from the most basic ones that allow the laptop to cool itself easier, to the most expensive ones that are meant to cool gaming systems (usually 3 high speed fans at a minimum).
[*]Make sure the fan in your computer is clean of dirt and dust.  This will require you to open the laptop, find the fan, and use a can of air to clean out the dirt, etc, that may be there.  You may also need to use some Q-tips to clean dirt.  This makes a BIG difference in your overall temperature.  You can go to YouTube and find video's of computer repair men taking air hoses to the inside of computers that automatically turn themselves off due to the heat.  After the cleaning, they work again.
[*]You may want to replace the heat sink compound on the processor while you are in there, especially if it has been a while ("a while" is relative, but if you use your laptop often, I would say a year is "a while").
[/LIST]
If you find a lot of dirt or dust inside the system, replace old heat sink compound, and buy a decent laptop cooler - then you can reliably decrease the temperature of the system by 10 degrees C at a minimum.  When I did items 1 & 2 on my desktop, my temperature decreased by 6 degrees C, and I didn't even have a lot of dust.

---

### Post by Krabby.Linux on 2011-12-29
This does not help at all.

It has nothing to do with dirt if the graphics card goes up to 110°C or even a lot more within a few minutes.

The problem does NOT occur while using windows. ONLY on Ubuntu!

While using Windows my notebook stays cold or does only get a little bit warm.

---

### Post by zielstep on 2011-12-29
You did not specify that the problem is specific to an operating system.

Which version of Windows are you running?

Which version of Ubuntu are you running?

If the problem occurs in Ubuntu, but not Windows, then you are correct to assume that it is not a physical problem (I.E. dirt, etc), but rather an issue with Ubuntu.  

I'll try to do some digging around (I have a few minutes to spare) but hopefully someone more experienced may drop by to help out.

Regards,

zielstep

---

### Post by Krabby.Linux on 2011-12-29
Thanks!


I am using

Windows 7
Ubuntu 11.10 32Bit

---

### Post by chipbuster on 2011-12-30
Are you using flash or one of the open-source variants of it? My first Ubuntu install came with some open-source junk on Mozilla that repeatedly glitched and crashed, so if you're using that, I wouldn't be surprised if that were the issue.

Right click on a Youtube video or other flash app. Does it show an Adobe Flash name at the bottom of the menu or a different plugin?

---

### Post by mcduck on 2011-12-30
> **Krabby.Linux said:**
> This does not help at all.

It has nothing to do with dirt if the graphics card goes up to 110°C or even a lot more within a few minutes.

The problem does NOT occur while using windows. ONLY on Ubuntu!

While using Windows my notebook stays cold or does only get a little bit warm.

Overheating is _always_ a hardware-related problem. No matter what drivers you use, what programs you run, even if the load on hardware is higher on Linux the fact that the laptop's cooler isn't able to keep the temperature on acceptable levels is definitely a hardware issue.

All computer hardware should be capable of running at full load for long periods of time. If they fail to do so, or get problems like overheating, it most certainly is a hardware problem.

You may be able to fix the overheating with software, but you are still left with a system that's not capable of cooling itself properly. I would definitely recommend checking that all fans are working properly and are free of dust, even if you manage to solve the problem of Flash videos causing high load. (Actually I would most likely return a computer that isn't able to run under high load without problems back to the shop as defunct or flawed product... :D)

---

### Post by chipbuster on 2011-12-30
> **mcduck said:**
> Overheating is _always_ a hardware-related problem. No matter what drivers you use, what programs you run, even if the load on hardware is higher on Linux the fact that the laptop's cooler isn't able to keep the temperature on acceptable levels is definitely a hardware issue.

All computer hardware should be capable of running at full load for long periods of time. If they fail to do so, or get problems like overheating, it most certainly is a hardware problem.

You may be able to fix the overheating with software, but you are still left with a system that's not capable of cooling itself properly. I would definitely recommend checking that all fans are working properly and are free of dust, even if you manage to solve the problem of Flash videos causing high load. (Actually I would most likely return a computer that isn't able to run under high load without problems back to the shop as defunct or flawed product... :D)

Definitely check all that, but it isn't quite true that all overheating is software-based. I had a friend who could almost max out Crysis, but he still regularly overheated his computer while playing Borderlands, a much less graphics intensive game. The difference was that Borderlands had no FPS cap. As a result, his system was rendering almost 400 FPS and cooking itself. Really badly written programs can demand more from the hardware, and as a result cause excess heat generation.

---

### Post by Paqman on 2011-12-30
You might want to try Youtube in their [HTML5 beta]("http://www.youtube.com/html5") to see if the problem is Flash-related.

---

### Post by mcduck on 2011-12-30
> **chipbuster said:**
> Definitely check all that, but it isn't quite true that all overheating is software-based. I had a friend who could almost max out Crysis, but he still regularly overheated his computer while playing Borderlands, a much less graphics intensive game. The difference was that Borderlands had no FPS cap. As a result, his system was rendering almost 400 FPS and cooking itself. Really badly written programs can demand more from the hardware, and as a result cause excess heat generation.

Even with the excessive load, any properly designed and functioning computer should be be able to cool itself properly.

So one might have a software problem that causes high load. But if that high load results in overheating, that's a hardware problem.

(so it would actually be two problems instead of one. A software problem that causes high load, and a hardware problem that makes your system unable to handle that high load)

Edit: actually there really isn't such thing as "excessive load" on computers, like I said all the hardware, even cheapest consumer-grade stuff, should be able to handle sustained full load without any problems.

---

### Post by QIII on 2011-12-30
Calling LovingLinux...

Hardware/Software problem aside (and, by golly, load or not your hardware should be able to keep itself either cool or in check), I might suggest (if you are using FireFox) that you look for an Add-On called Flash Aid.  It might help you figure out if your Flash is really to blame.

---

### Post by Krabby.Linux on 2011-12-30
If you say this Problem is Hardware related. WHY does my System stay cool while using Windows under full load. And WHY does Linux cause my notebook to get so hot that i cant even touch my notebook while watching Flash videos.

I don`t see any Hardware related problems here. Ubuntu shows that the Fan runs at 100% Speed.

@Paqman, Watching HTML5 Videos keep my Notebook cool.

It is DEFINITELY Flash!

I use the Adobe Flash Player Plugin 11 which has a lot of positive reviews from people who are using Ubuntu 11.10.

Youtube Problem solved, thanks to Paqman. But what do I do while watching Flash Content on other sites ?

---

### Post by Paqman on 2011-12-30
> **Krabby.Linux said:**
> 
@Paqman, Watching HTML5 Videos keep my Notebook cool.

It is DEFINITELY Flash!


It often is. Another fine product from Adobe. Unfortunately the HTML5 beta on Youtube keeps opting you out, so you need to keep going back to that page and opting in.

As was suggested above, open up Firefox and install the plugin called Flash Aid. This will upgrade you to a newer version of Flash than you have in the repos and hopefully it will perform better.

---

### Post by vasa1 on 2011-12-30
This is what I have:
```
    File: libflashplayer.so
    Version: 
    Shockwave Flash 11.1 r102
```

No heating problems.

---

### Post by Krabby.Linux on 2011-12-30
> **Paqman said:**
> It often is. Another fine product from Adobe. Unfortunately the HTML5 beta on Youtube keeps opting you out, so you need to keep going back to that page and opting in.

As was suggested above, open up Firefox and install the plugin called Flash Aid. This will upgrade you to a newer version of Flash than you have in the repos and hopefully it will perform better.

I am using Google Chrome and Flash aid is not available for Chrome :-(.

---

### Post by Derek Karpinski on 2011-12-30
Do you have Firefox installed?
 
If you do, install flash-aid, and run it. Then you never have to open FF again.
 
Chrome will use the flash installed by flash-aid.
 
Or, you can manually put the flash .so file in the folder manually.
 
And I agree that if your computer cannot function at 100% load, and stay cool enough to not melt down......that's a hardware issue, no matter how badly the linux implementation of flash is, the hardware MUST keep you're system from melting down.
 
You CAN enable hardware acceleration for flash, but I think you need to have an nVidia gpu, and you need to install a package. HW acceleration helped bring down the load on the CPU for me.
 
Please give your pc specs including graphics card.

---

### Post by Krabby.Linux on 2011-12-30
My System:

Ubuntu 11.10
Kernel 3.0.0-14-generic-pae
GNOME 3.2.1

Processor Intel Core 2 Duo T8300 @2.4Ghz
6GB RAM

Graphics Card: Geforce 8400M GS

I dont see an option where I can use hardware acceleration for Flash.

Thanks :-)

---

### Post by Derek Karpinski on 2011-12-30
First, did you have FF installed?  Did you find the 'flash-aid' extension for FF?  Did you run it?

---

### Post by Derek Karpinski on 2011-12-30
To enable HW acceleration, install 'libvdpau'.  After you've installed that, run flash-aid, and make sure to check the box for HW acceleration.
 
I'd use the beta version of flash from 'flash-aid'.

---

### Post by Paqman on 2011-12-31
> **Krabby.Linux said:**
> I am using Google Chrome and Flash aid is not available for Chrome :-(.

It doesn't matter, Flash Aid will sort out Flash for all browsers. Go ahead and install it into Firefox, then run it.

---

### Post by S2UIRR3L on 2011-12-31
Krabby - Just taking a shot in the dark here...

Could it be that your version of Ubuntu isn't compatible with your hardware yet? As in, maybe there's a bug that hasn't been reported yet and you may not be the only one experiencing this over heating issue?

I have a similar system in regards to the processor, RAM, etc... But mine is a Gateway desktop with a Fujitsu hard drive (the original 1-TB didn't want to work anymore). I am running 64-bit Lucid and it's just great.

I skipped installing 7 on my new Fujitsu hard drive (I don't use Windows anymore) and just installed Lucid only. My computer fans never even think of speeding up while watching a you tube vid... even in full screen.

I'm taking a wild guess here in thinking that there's a bug or something that hasn't been resolved with your hard ware just yet. I'm just a little curious here (had this problem with an older computer, but not this one)...

Watching you tube videos:
Does your laptop's fan(s) speed up to cool your system while in Windows?
Does your laptop's fan(s) speed up to cool your system while in Ubuntu?
Have you checked your BIOS to see if there's any limit on your cpu/fans?

-Squirrel

---

### Post by lovinglinux on 2011-12-31
> **QIII said:**
> Calling LovingLinux...


I guess I am late :-)

First of all, although dirt might contribute a lot to the overheating problem and that it could also be affected by hardware issue, the most likely reason  here is because flash sucks and uses too much CPU cycles. You need to make sure Flash is using hardware acceleration to reduce CPU usage. Flash-Aid can help you with that, even if you use other browsers. Flash-Aid is just an script generator, that detects your system settings and flash plugins, remove all plugins to avoid conflicts, install the best version according to your system architecture and apply some optimizations. Once you execute Flash-Aid, you can close Firefox and open other browsers. However, if you are using Chrome 32bit, you might need to disable the plugin that is bundled with Chrome. You can do that by typing *[noparse]about:plugins[/noparse]* in the address bar, the clicking "Details", then disabling the one that is located under **/opt/google/chrome/libgcflashplayer.so**.

If you are using a vdpau capable nvidia card, you can install *libvdpau* package, as already suggested, before running Flash-Aid, so the extension will detect it and will offer to apply HWVideo Decode tweak. However, if you are on a 64bit system, HWVideo Decode can cause crashes with the latest flash version, so I have disabled it by default in the latest Flash-Aid version. You need to test on your system.

If were a Firefox user, I would recommend [FlashVideoReplacer](https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/), which is another extension I develop. It replaces the flash video player with the original mp4/flv video, so you can play it with a different plugin, like totem or gecko-mediaplayer. This reduces CPU usage a LOT. The extension also allows to open the videos with external video players without downloading first. FVR also has an option to use WebM HTML5 video when available on YouTube. You don't need to subscribe to the HTML5 beta program. All you need is to enable this option in the preferences and the extension redirects to the HTML5 video when available.

Unfortunately, FVR is not available for Chrome. You could try a script for Greasemonkey. See [http://userscripts.org/scripts/show/50771](http://userscripts.org/scripts/show/50771)

---

### Post by sabinedoll on 2012-01-01
Hi, I just went through the same problems, computer heating up and crashing while playing flash-movies, EVEN with ice-packs on the computer and everything clean!

I did the following: after installing newest Firefox (version 9), I found Flash-aid (an add-on), which allowed me to test three available flash-players, the newest from Adobe, the one from the repositories, and Google's version. I am sticking with **Google's version of the flash-player**(works in all browsers), as it **runs considerably cooler, at least on my computer.**

(In addition, there may be other software causing heat-problems, the linux-kernel may be one of them. This is a known problem that was announced to be fixed in kernel 3.3.)

---

### Post by S2UIRR3L on 2012-01-01
Can I suggest something crazy... Download, burn and run a puppy disc. Let it install everything you need to watch a video on YouTube and see if your computer overheats with Puppy.

Heck... Try a few different distros and see if they make any difference. If I'm not mistaken, you're on a beta version of Ubuntu and I'm assuming beta versions are all about running into problems and fixing them.

Like I said above... The odds are not great, but there are indeed odds that say your computer may not yet be supported with this distro. And what does it cost to try a live disc... a few hours and 12-cents for the CR-R? You might even like "it" better than Ubuntu :)

-Leo

---

### Post by corrytonapple on 2012-01-01
IDK if this is answered or not, didn't read past page one.
It could be that Windows controls the fan better than Ubuntu does.

---

