---
title: "Please stop the CRASHING!!!"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by leo123 on 2008-08-21
So many great things have been said about Ubuntu so I decided to try it. Not long after installing Hardy, the crashes started. After 3 months of constant crashes and no solutions found on the forums, I downgraded to Gusty, which had worked for the most part flawlessly.

That too started crashing, so Hardy was reinstalled again, a couple of months ago.  This constant crashing is driving me crazy.  Both Kubuntu and Ubuntu crash while looking at e-mail in Thunderbird or browsing in Firefox 3.

After the crash, the log-in screen appears. This is very frustrating and more and more I am booting up a Windows laptop, that before all of the crashes, I barely touched.

Ubuntu/Kubuntu is new to me and the default install is basically, what I've gone with.

Can someone please assist me in getting to the root of these crashes?

---

### Post by Mhurst1 on 2008-08-21
I jave yet to have a crash. What are you doing in FF when it crashed?

---

### Post by leo123 on 2008-08-21
I just clicked on the "New Reply" button and it crashed.

---

### Post by rdpsycho on 2008-08-21
i had the same problems with firefox(im using ubuntu 8.04 & ultimate edition 1.8 ) , clicking on stuff/links at totally random times would close out firefox, althought my computer did not actually log it self off it was very frustrating and for some reason is hasnt done it for a really long time now though(fingers crossed). also i could not get the crashes to repeat themselves when going back and trying the previous action that crashed it, meaning it would always happen at a different time/link.

p.s. when i say crash i mean the program would instantly close the moment i clicked a link, no lag/freeze whatsoever.

off topic, why is there emoticons on this forum, arent they for windows noobs who cant read ascii???

---

### Post by Koselara on 2008-08-21
I started in late June or early July, and have had crash/lockup problems, too -- thought it was that I'd screwed up my profile, so I started over but soon started seeing trouble again.  I have a bad feeling that Firefox 3 is the culprit for both of us, because I had the exact same problems in Windows: the hard drive would randomly start spinning for seemingly no reason with CPU spikes so bad I couldn't type for minutes at a time, Firefox/Thunderbird closed randomly, etc.  (I haven't used Thunderbird in Linux.)

Anyway, maybe the solution is to try to avoid Mozilla stuff for a while and see if our systems work better?  _If_ the issue is Mozilla's code then no point blaming the OS...  FWIW I've been surprisingly happy with Konqueror 4 (and I normally use tons of add-ons in Firefox), and find Evolution Mail is pretty powerful with Balsa a good quick alternative.  Just a thought!  :)

---

### Post by Tatty on 2008-08-21
Try running firefox from a terminal, then when it next crashes it will hopefully output an error message into the terminal.

To do this load a terminal (Applications->Accessories->Terminal), then type firefox, and press enter.

---

### Post by Koselara on 2008-08-21
> **rdpsycho said:**
>  why is there emoticons on this forum, arent they for windows noobs who cant read ascii???

No, they're pretty much universal in web-based forums these days, as it's built into most of the common software for running one. They're used by people with all kinds of skills -- so is Windows, for that matter. 

You can always disable the emoticons if you have some kind of problem with it.  I believe it's in the user control panel.

---

### Post by gobbles414 on 2008-08-21
On my Ubuntu 8.04 system, I've been able to prevent Firefox and other programs from crashing by going *System => Preferences => Appearance => Visual Effects => None*, and then restarting my computer. Although this solution may not work for you, it's a potentially-easy fix that's worth trying.

Did this help?

---

### Post by meanburrito920 on 2008-08-21
> **Tatty said:**
> Try running firefox from a terminal, then when it next crashes it will hopefully output an error message into the terminal.

To do this load a terminal (Applications->Accessories->Terminal), then type firefox, and press enter.

This would be good to try, but I don't think it will address his problem because by the description he gave (the login screen reappearing after crash) it sounds like the entire Xserver is going down.

---

### Post by SunnyRabbiera on 2008-08-21
downgrading to firefox 2 is a good idea too.

---

### Post by Tatty on 2008-08-21
> **meanburrito920 said:**
> This would be good to try, but I don't think it will address his problem because by the description he gave (the login screen reappearing after crash) it sounds like the entire Xserver is going down.

Good point.  In that case perhaps it may be worth checking in /var/log for the xorg logs after the next crash.

---

### Post by jerzydirtracer on 2008-08-21
Ubuntu 7.10 and firefox 2 no problems or crashes what so ever after 6 mos, had ff3 and kubuntu in garage, got rid of ff3 and went back to ff2. Ff3 crashed all of the time. Dont know about Ubuntu ver8 I wont load until all bugs worked out.

---

### Post by Silent Ninja on 2008-08-21
Ubuntu installed on my work computer has never crashed that way.. no obstantly I've tried to install it multiple times on my Laptop (MSI M670) and suddenly when i'm doing one thing or another, it just crashes. I've had to switch to win-do´hs but, if it would get fixed I would be pleased to try again.

I also use Mozilla software, but it also happened when I'm not using them. I think it has to be something hard-related like the Wireless card.. or something like that, because it just happened to me on my laptop, and not on my desktop computer (which also is a sempron 3200+).

---

### Post by leo123 on 2008-08-22
Thank you all for your posts.

gobbles414 - Visual effects is not enabled.

SunnyRabbiera - Already downgraded to FF2 and 7.10 (which is what I'd used before w/o any problems) after all the crashing and it started crashing too.

If there are any more crashes, hopefully not, I will look at the xorg log files, even though I don't know what to look for.

I'd like to stick it out and get the issue resolved, but the constant crashing with no solution just isn't cutting it for me. 

Thank you

---

### Post by gobbles414 on 2008-08-22
Would you please post your computer's specs, leo123? Also, could you post a screenshot of *System => Administration => Hardware Drivers*? Thanks...

---

### Post by nhasian on 2008-08-22
> **leo123 said:**
> Not long after installing Hardy, the crashes started. After 3 months of constant crashes and no solutions found on the forums, I downgraded to Gusty...That too started crashing

I must concur with Silent Ninja.  It sounds like it may be a hardware problem.  especially since your crashing in both Hardy and Gusty.  Is your PC overheating?  Do you have any fans on the CPU, Video Card, or Powersupply that are not spinning properly?  Can you run some diagnostic tests on your computer's RAM and hard disk?  That may help you pinpoint any hardware problems.

---

### Post by lovinglinux on 2008-08-22
Funny to see this post, because Firefox 3 crashing 3 times per minute and random BSOD's made me install Ubuntu Hardy less than a week ago on dual boot with my previous Windows XP installation.

The problem with Firefox is random. Some times it crashes when scrolling a page, some times when clicking a link, sometimes when the computer is on "idle" state, with just Firefox opened and no user interaction whatsoever.

I discovered that the problem was a bad memory stick, but I'm not going back to Windows. Ubuntu Hardy runs much more smoothly on my system and Firefox 3 totally stopped crashing.

I guess this Firefox version is more prone to crashes on sub-par systems, nevertheless if you google it you will get a lot of complains about Firtefox 3 crashing nightmare.

---

### Post by leo123 on 2008-08-23
**Gobbles414** -
 
VIA VT8378 (KM400/A)
AMD Athlon 1826
1GB DDR

“Hardware Drivers” is not on the menu

**nhasian** - PC is not overheating and all fans are spinning correctly.

Diagnostic tests is not something I've done before. Can you point me in the right direction?


**lovinglinux** – Now that you mention it, I did add a new stick of memory in between the 2 different installs of Gusty. 

Probably need to upgrade the motherboard, memory and processor. Might as well upgrade the Windows box for my husband too. 

Any suggestions on cpu, motherboard combos for Linux and Windows?

Both boxes mainly used for e-mail, web browsing, listening to music, uploading pictures, ipod, etc...

Thank you

---

### Post by gobbles414 on 2008-08-23
> Gobbles414 -

VIA VT8378 (KM400/A)
AMD Athlon 1826
1GB DDR VIA hardware has never worked very well in Linux; VIA only recently started cooperating with the open source community on drivers and the like. So my first instinct is to blame the lack of drivers for your VIA hardware. But to be honest, the fact that your Ubuntu 7.10 was stable for a time doesn't agree with that assessment.

> “Hardware Drivers” is not on the menu That's extremely strange! *System => Administration => Hardware Drives* is part of the default Hardy install (called "Restricted Drivers Manager" in older version of Ubuntu). If you still can't find the control panel for hardware drivers on your computer, you should be able to enable it by using *System => Preferences => Main Menu*. If that fails as well, open a terminal window and enter *gksu -D /usr/share/applications/jockey-gtk.desktop /usr/bin/jockey-gtk*. If that fails too, then something is definitely wrong with your Ubuntu installation!

---

### Post by egalvan on 2008-08-23
> **leo123 said:**
> **Gobbles414** -
 
VIA VT8378 (KM400/A)
AMD Athlon 1826
1GB DDR

**nhasian** - PC is not overheating and all fans are spinning correctly.

Diagnostic tests is not something I've done before. Can you point me in the right direction?

**lovinglinux** – Now that you mention it, I did add a new stick of memory in between the 2 different installs of Gusty. 

Both boxes mainly used for e-mail, web browsing, listening to music, uploading pictures, ipod, etc...

Thank you

#1, what did you do to check the temperatures?

#2 A memory test is part of the LiveCD. Boot from it, choose language, then scroll down to the Memtest option. Let it run for several hours if possible.

#3 Remove and install the memory sticks. They may be loose.

#4 That doesn't sound like it would strain your computers. 

And last of all, check for dust. Heat-sinks and power supplies are prone to collecting it, and a less-than-optimum power supply can crash under the extra heat.

That said, is that an Athlon, or Athlon-XP? Athlons run HOT, -XP's run  cooler.

:popcorn:

---

### Post by leo123 on 2008-08-24
**Gobbles414**

> That's extremely strange! System => Administration => Hardware Drives is part of the default Hardy install (called "Restricted Drivers Manager" in older version of Ubuntu). If you still can't find the control panel for hardware drivers on your computer, you should be able to enable it by using System => Preferences => Main Menu. If that fails as well, open a terminal window and enter gksu -D /usr/share/applications/jockey-gtk.desktop /usr/bin/jockey-gtk. If that fails too, then something is definitely wrong with your Ubuntu installation! 

I previously removed jockey-gtk. I reinstalled it and there are "No proprietary drivers are in use on this system."


**egalvan**

> #1, what did you do to check the temperatures?

#2 A memory test is part of the LiveCD. Boot from it, choose language, then scroll down to the Memtest option. Let it run for several hours if possible.

#3 Remove and install the memory sticks. They may be loose.

#4 That doesn't sound like it would strain your computers.

And last of all, check for dust. Heat-sinks and power supplies are prone to collecting it, and a less-than-optimum power supply can crash under the extra heat.

That said, is that an Athlon, or Athlon-XP? Athlons run HOT, -XP's run cooler.

#1 The box is not hot to the touch and cool air is coming out of the vents.

#2 Will try this as soon as time permits.

#3  Checked the memory and it is seated properly.

Periodically, I clean out the dust.

Athlon XP

Thank you

---

### Post by VraiChevalier on 2008-08-24
After re-reading your thread starter I am lead to believe the problem may be hardware related. The GPU, whether on board or discrete, may be becoming faulty. I would try booting and running from a Live CD for a while and observe if there is any difference.

Also, actually pulling out and re-seating the RAM modules could help. Even if they look fine a microscopic layer of corrosion can interfere with the contacts. Running the Memtest would be a really good idea too.

---

### Post by hopkinsjeni on 2008-08-24
I had firefox crashing left right and center when I first installed. I found that some part of Deskbar applet was missing and a few other bits and pieces. Go into Administration > Software Sources and make sure you have the all the updates checked and hopefully your pc will automatically install the drivers, etc to fix the problem. It worked on mine anyway, hope it helps!

---

### Post by leo123 on 2008-08-24
What are the compatible motherboard/cpu combos for Ubuntu?

If it's a hardware issue, an upgrade would solve the crashing.

Since May, I've tried the helpful suggestions from others, done all updates, reinstalled, all to no avail. Ubuntu/Kubuntu is still crashing.

As stated earlier, this box is just used for the basics, such as e-mail, web browsing, uploading pictures, listening to music etc... so I don't need the latest and greatest motherboard/cpu combo.

Thank you

---

### Post by stalkier on 2008-08-24
> **SunnyRabbiera said:**
> downgrading to firefox 2 is a good idea too.

This saved the constant crashes for me. I don't the crashes on my laptop using FF3 and not sure why. Laptop runs fine. My desktop is running FF2 and has very few crashes now.

---

### Post by pizzavortex on 2008-08-24
I had terrible crashes in gutsy.  Kernel panics perhaps, although it's impossible to tell in X I believe.  Had to use Alt+SysRq R.E.I.S.U.B to restart my computer.  Drove me insane.  It never crashes in hardy. It's a shame how disappointing linux can be sometimes.

---

### Post by nhasian on 2008-08-25
I've been building/repairing PCs for over 10 years.  I prefer to stick with Intel Processors and Motherboards with Intel Chipsets.  I dont want to start a flame war, but I've had a lot of problems with AMD's running hot (and crashing) or causing the OS to crash because it didnt fully support AMD processors.  Anyway a quick check of pricewatch shows that the INTEL CORE 2 QUAD Q6600 2.4GHZ processor starts at $178.  thats four processors!  I wish my laptop had quad core hehe

> **leo123 said:**
> What are the compatible motherboard/cpu combos for Ubuntu?

---

### Post by thomman on 2008-08-25
Hi I was having problems with Thunderbird earlier I reinstalled and then the problem stopped. I was not having any problems whatsoever for the past 5 days on a clean install. However today morning I started seeing Thunderbird open up connect and then just close. If I disconnect my net connection it remains open. But the moment I have the net connected it shows this problem of closing after checking mail. I opened thunderbird in terminal mode and got the following error.

(gecko:6656): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Tahoma 9.75'
Segmentation fault

The only thing that I did in common was to copy my windows fonts into usr/share/fonts/truetype/msttcorefonts

Has anyone done the same at any time. This might be the problem. How would I revert.

---

### Post by xeth_delta on 2008-08-25
> **leo123 said:**
> **Gobbles414**



I previously removed jockey-gtk. I reinstalled it and there are "No proprietary drivers are in use on this system."


**egalvan**



#1 The box is not hot to the touch and cool air is coming out of the vents.

#2 Will try this as soon as time permits.

#3  Checked the memory and it is seated properly.

Periodically, I clean out the dust.

Athlon XP

Thank you

#1 I am not sure the outside box temperature will tell you very much about the health of the CPU. Please open a terminal and run the following, under the same conditions that produce a crash:
```
cat /proc/acpi/thermal_zone/temperature
``` that ought to show you the temperature as reported by the internal CPU thermal diode, or if not present, the one presented by the mainboard (many have (or used to have a thermocouple or diode for this purpose, though not as precise as a CPU o-board one).

#2 faulty memory seems like a certain candidate, but even if that is the case, you would not be loosing the entire range. The Linux kernel can discard defective memory ranges at boot time and not use them at all. This can be done by passing certain arguments to it, during boot. I can look it up, if you're interested.

---

### Post by thomman on 2008-08-26
I just remembered that my laptop had shutdown abnormally after the battery got drained out so I figured this might have caused the font file to have gone bad. I recopied the foint file tahoma.ttf from my windows fonts to /usr/share/fonts/truetype/msttcorefonts and now thunderbird  works fine. Earlier too my thunderbird used to crash stating a missing or bad font. I think all who experince teh problem should open it in terminal mode and see what the problem is.

---

### Post by MONODA on 2008-08-26
If you are using compiz fusion aka desktop effects, then the problem is your video card's driver. You either do not have it installed properly or the crashes are due to bugs in the proprietary nvidia driver.

---

### Post by addeboy on 2008-08-26
> **Silent Ninja said:**
> Ubuntu installed on my work computer has never crashed that way.. no obstantly I've tried to install it multiple times on my Laptop (MSI M670) and suddenly when i'm doing one thing or another, it just crashes. I've had to switch to win-do´hs but, if it would get fixed I would be pleased to try again.

I also use Mozilla software, but it also happened when I'm not using them. I think it has to be something hard-related like the Wireless card.. or something like that, because it just happened to me on my laptop, and not on my desktop computer (which also is a sempron 3200+).

If you haven't tried yet, check **[this post]("http://ubuntuforums.org/showpost.php?p=4963984&postcount=24")**. It worked for me, on a MSI M670.

---

### Post by gobbles414 on 2008-08-27
> What are the compatible motherboard/cpu combos for Ubuntu? I've had good luck with Gigabyte motherboards. Regarding processors, Intel and AMD have both worked equally well for me in Ubuntu.

Again, I'd advise that you stay away from VIA hardware. Please note that VIA also makes chips for many of the major motherboard manufacturers. So I recommend that you look at detailed specs for several motherboards before you make a purchase.

---

### Post by vikramaditya on 2008-08-27
> **rdpsycho said:**
> off topic, why is there emoticons on this forum, arent they for windows noobs who cant read ascii???
sorry for addressing the off-topic again, but i like emoticons for the emphasis they contribute to some posts.  with that in mind, i proposed adding some extra 'cons [here]("http://ubuntuforums.org/showpost.php?p=5661896&postcount=1"), but was swiftly shot down in flames by the gods of olympus. :(

---

