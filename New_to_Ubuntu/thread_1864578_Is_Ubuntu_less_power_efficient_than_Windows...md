---
title: "Is Ubuntu less power efficient than Windows.."
date: 2011-10-19
forum: New to Ubuntu
---

### Post by aruntu on 2011-10-19
I am advanced level user in windows and know my way around it, i recently switched to Ubuntu to become familiar with it, I heard that Ubuntu drinks more battery than Windows.. and in my experience it really is.. So all i want to know is whether there is anyway to improve the power efficiency.. Windows provides loads of power options but in Ubuntu there are very few as far as or any new user could know.. So please help me with this..

---

### Post by mcduck on 2011-10-19
This pretty much depends on your hardware, especially the graphics card and how well whatever drivers you are using for it handle power saving.

There's nothing in Linux (or Ubuntu) itself that would make it less efficient when it comes to power usage, and most people get equal, or even better, power efficiency that they do in Windows.

There *are* things you can do to improve power efficiency, but none of those make a big difference compared to the effect graphics card/driver have.

So if you are lucky, you get great power efficiency without really doing anything about it. And if you are unlucky, your battery life might truly suck compared to Windows. It all depends on the setup of the exact setup of your machine. If you want to check beforehands, you can always try to google for the computer model, or components, you are using. Otherwise you'll just have to test it yourself.

---

### Post by buzzmandt on 2011-10-19
For the most part I would answer your question as yes

---

### Post by Paqman on 2011-10-19
Check out [Jupiter]("http://www.jupiterapplet.org/"), it's a power control applet that actually re-tunes your kernel on the fly, depending on whether you're on battery or what level of performance you want.

---

### Post by kaldor on 2011-10-19
It depends heavily on your hardware setup. Intel graphics cards tend to be the most efficient for laptops and netbooks. If you use an AMD/ATI or Nvidia graphics card, you should install the proprietary drivers- they have much better results on mobile devices.

If you are using a desktop machine, then the proprietary drivers won't matter unless you have a specific need for them (HD video playback, 3d games).

I also strongly suggest the Jupiter applet.

---

### Post by gene simmons on 2011-10-19
i use jupiter on my laptop and it runs longer than windows 7 on battery,on my netbook ubuntu ran way longer on battery than windows 7.i have never heard of windows lasting longer than linux on battery,in all my experiences on all my computers linux has lasted longer

---

### Post by Mark Phelps on 2011-10-19
The critical factor is how well the OS does power-saving.  PC's that come preinstalled witn Win7, especially laptops, already have the power-saving features turned on. 

Ubuntu, when installed, does NOT automatically enable the same features.  So, if you install Ubuntu, it's likely that you'll hear the fan more, have the laptop run hotter, and see the battery run down sooner.

If you ARE able to then enable power-saving features in Ubuntu, it will generally do BETTER than Win7 as conserving power.

---

### Post by mcduck on 2011-10-19
> **Mark Phelps said:**
> The critical factor is how well the OS does power-saving.  PC's that come preinstalled witn Win7, especially laptops, already have the power-saving features turned on. 

Ubuntu, when installed, does NOT automatically enable the same features.  So, if you install Ubuntu, it's likely that you'll hear the fan more, have the laptop run hotter, and see the battery run down sooner.

If you ARE able to then enable power-saving features in Ubuntu, it will generally do BETTER than Win7 as conserving power.

This is incorrect. Ubuntu will, by default, run your processor in on-demand mode, which means the frequency will be dropped to smallest supported on low load, and switched to highest supported when there is need. This has been proven to be the most efficient way to handle CPU power saving on any modern processor on almost all common usage situations. (the voltage dropping is handled automatically by the CPU and motherboard in accordance to the frequency currently in use, so the OS doesn't need to do anything about that)

Your graphics card will also do the same, depending on card and the drivers used. Lack of support for graphics card power saving in drivers is, like I mentioned previously, the most common reason why you might get worse battery life on Linux.

...and in addition power saving features are even used for things like your hard drive, and even the sound chip if you have a model that supports such features. (luckily this seems to work without any issues now, couple of versions ago the sound chip power saving used to cause audible pops when the card was switched between powered and power-saving mode)

---

### Post by dargaud on 2011-10-19
One area where Ubuntu fails with respect to Windows is putting hard drives in sleep mode. I've tried all kind of things with hdparm, but the disk always wakes up within 10 seconds. It's a secondary, non-system disk and on Windows it would sleep all day if not in use. I gave up.

---

### Post by aruntu on 2011-10-20
Thanks guys for your response.. Installed Jupiter and will test it out...

---

### Post by thatguruguy on 2011-10-20
> **mcduck said:**
> This is incorrect. Ubuntu will, by default, run your processor in on-demand mode, which means the frequency will be dropped to smallest supported on low load, and switched to highest supported when there is need. This has been proven to be the most efficient way to handle CPU power saving on any modern processor on almost all common usage situations. (the voltage dropping is handled automatically by the CPU and motherboard in accordance to the frequency currently in use, so the OS doesn't need to do anything about that)

Your graphics card will also do the same, depending on card and the drivers used. Lack of support for graphics card power saving in drivers is, like I mentioned previously, the most common reason why you might get worse battery life on Linux.

...and in addition power saving features are even used for things like your hard drive, and even the sound chip if you have a model that supports such features. (luckily this seems to work without any issues now, couple of versions ago the sound chip power saving used to cause audible pops when the card was switched between powered and power-saving mode)

I believe he was referring to ACPI, which is turned off by default in the Linux kernel.

---

### Post by mcduck on 2011-10-20
> **thatguruguy said:**
> I believe he was referring to ACPI, which is turned off by default in the Linux kernel.

It sure isn't, unless your system has some problems with it's ACPI support.

---

