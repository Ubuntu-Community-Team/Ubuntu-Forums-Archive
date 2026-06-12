---
title: "Battery power seems to have taken a huge dip."
date: 2011-09-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by kaldor on 2011-09-01
I was never affected by the previous claims of power regressions, but on Oneiric it seems to have hit me quite hard.

Fedora 15 (kernel 2.6.40) gives me my expected ~45 minutes to an hour of battery life (this laptop is old). After running Oneiric for *only about 5 to 10 minutes* I get low battery warnings which make very little sense. The one that popped up after a few minutes of use was something like "*19 minutes remaining (75%)*" and it continues to get worse from there. How is it that earlier in the development cycle, it was fine? Also, wasn't this so-called power regression introduced long before kernel 2.6.40, which I use on a regular basis? 

Note that it *is* actually draining and not giving false warnings. 

Can anyone else confirm this, or am I just going insane?

_Specs_

[LIST]
[*]NVIDIA GeForce 8400m
[*]2 GB RAM
[*]Intel Centrino 1.8 Ghz dual core processor
[*]250 GB HD
[/LIST]

---

### Post by quarternote on 2011-09-01
It could be something to do with this.

PCI Express Active-State Power Management

[http://www.phoronix.com/scan.php?page=news_item&px=OTg2Mg]("http://www.phoronix.com/scan.php?page=news_item&px=OTg2Mg")

---

### Post by aeronutt on 2011-09-01
This is not a good trend. My Oneiric battery life is about 35% less than Natty. But this article implies nothing will likely change between now and final release.

---

### Post by foutes on 2011-09-01
I read somewhere there is problems with the new kernel and power management that lead to a lot less battery life which is why I am sticking with 11.04 for a while.

---

### Post by shuttleworthwannabe on 2011-09-02
I have tried [this work around]("http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html")--seems to have made some difference; but not a whole lot. There are [other solutions]("http://askubuntu.com/questions/23404/laptop-battery-life-drastically-decreased-compared-to-windows-7")--but results vary.

---

### Post by aeronutt on 2011-09-02
Wow, ok, so here's the trend. (I just loaded Oneiric beta1). My battery usage over a few versions:

Natty, (11.04): ~950ma
Oneiric alpha 3 (11.10): ~1500ma
Oneiric beta 1 (11.10): ~2350ma

So, latest beta is using 2.5x the battery current compared to Natty. Wow.

---

### Post by aeronutt on 2011-09-02
> **shuttleworthwannabe said:**
> I have tried [this work around]("http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html")--seems to have made some difference; but not a whole lot. There are [other solutions]("http://askubuntu.com/questions/23404/laptop-battery-life-drastically-decreased-compared-to-windows-7")--but results vary.

Thanks, tried these. But none helped.

---

### Post by lucazade on 2011-09-02
@aeronutt

have you tried to see what is draining battery with 'powertop' ?

---

### Post by aeronutt on 2011-09-02
> **lucazade said:**
> @aeronutt

have you tried to see what is draining battery with 'powertop' ?

I'm headed down that road.:)

---

### Post by aeronutt on 2011-09-02
Hmmm....what does this mean? (top 2 on powertop):

```
Usage   Events/s    Category       Description
100.0%              Device         Audio codec hwC0D3: Intel
100.0%              Device         Audio codec hwC0D0: IDT
```

---

### Post by RJ12 on 2011-09-02
> **aeronutt said:**
> Hmmm....what does this mean? (top 2 on powertop):

```
Usage   Events/s    Category       Description
100.0%              Device         Audio codec hwC0D3: Intel
100.0%              Device         Audio codec hwC0D0: IDT
```

I don't know anything about powertop input/output, but I'm going to take a guess that your sound devices are taking the power, and if they're connected via PCI, it might be the PCI bug.

---

### Post by shuttleworthwannabe on 2011-09-02
> **aeronutt said:**
> Thanks, tried these. But none helped.

As I said, results may vary. It is upsetting that this bug will not even be addressed in the next 2 releases. 
IS this an Ubuntu kernel issue or generally affecting all distro's using these kernels?

---

### Post by gunksta on 2011-09-02
The kernel power regressions are global. Switching to another distro won't help. There also appears to be a bug in the current release of zeitgeist. On my machine and several others, zeitgeist seems to peg to 100% and then eventually die. 

Make sure zeitgeist isn't going crazy before you run a powertop assessment. I'm sure my battery life with one processor stuck @ 100% would be atrocious.

Its also worth noting that not all systems are affected by this bug. My Lenovo X220 seems to be fine (unless zeitgeist goes on a tear).

---

### Post by pressureman on 2011-09-03
On my system I notice that when idling, ubuntuone-syncdaemon is consistently in the top 5 power-consuming processes. Since I don't have an Ubuntu One account, and have no intention of using this service, I'd really like to disable this, like I could in Natty (from the startup services control panel applet). I haven't yet found a way of doing that in Oneiric.

I guess I could uninstall ubuntuone-client, but I'd really just rather opt out of running it all the time, in case I later change my mind.

---

### Post by aeronutt on 2011-09-03
Zeitgeist doesn't seem to be the problem on my laptop. I'm also thinking that the increase in power between alpha and beta (from 1500mA to 2500mA) couldn't be the kernel bug either? So maybe there's hope it'll get fixed (at least back to 1500mA) prior to final release.

---

### Post by Appleshare on 2011-09-05
Same here, my Macbook Pro went from ca 4h:30min battery life with Natty to 2h:15min with Oneiric. 

[EDIT: this might not be true, I realize I don't know how to interpret the (new?) powertop output. Need to look into it]
With powertop, the top power user is:
100,0%                      Device         Audio codec hwC0D0: Cirrus Logic
[/EDIT]

Is there a bug report for this in Launchpad where we can add info and watch status? I couldn't find one. 

While I appreciate the complexities of kernel work, it seems slightly ridiculous that Oneiric  makes the final move to a small-screen (hence, mobile) GUI with Unity and Gnome 3, and at the same time nearly halves battery life.

Edit: This one I guess: [https://bugs.launchpad.net/ubuntu/oneiric/+source/linux/+bug/760131](https://bugs.launchpad.net/ubuntu/oneiric/+source/linux/+bug/760131)

---

### Post by aeronutt on 2011-09-05
Agreed. My only hope is that this power problem is particular to Oneiric beta, and not the kernel. Why do I think this might be true? I've seen reported that 'the power bug' starts with kernel version 2.6.38. But, that's the version (2.6.38-11-generic) that I'm running in Natty with >4hours battery life. But, heck if I know for sure.

---

### Post by donniezazen on 2011-09-05
My laptop battery is severely hit. The temperature ranges from 65-70 degrees which makes Thinkfan run crazy. I get atleast 2 hours of extra battery on Windows 7. Hope this is fixed soon. I can't put my new hardware to constant 20 degrees extra heat.

Arch Linux seems to be little less harsh on my hardware but it is too much work to setup.

---

### Post by aeronutt on 2011-09-07
Here's an intersting piece of data. Previously, I reported:
Natty, (11.04): ~950ma
Oneiric alpha 3 (11.10): ~1500ma
Oneiric beta 1 (11.10): ~2350ma

But yesterday, I did a new install of 11.04, and checked battery usage in Unity, and got ~1500ma. Then installed gnome3/shell, and battery usage went down to ~950ma without any other changes. So, updated table:

Natty, (11.04) with Gnome3/shell: ~950ma
Natty, (11.04) with Unity: ~1500ma
Oneiric alpha 3 (11.10): ~1500ma
Oneiric beta 1 (11.10): ~2350ma

---

### Post by lucazade on 2011-09-07
Has anyone said compiz? :) just guessing!

side note, unity-2d is going to ship a new opengl backend based on qt4.. can't wait to try.

---

### Post by deadite66 on 2011-09-07
another problem is the wrong cpu freq governor being loaded.
with maverick and lower acpi-cpufreq gets loaded which supports under volting for less power and heat.
with natty and above p4-clockmod will load which doesn't support under volting and is too slow for ondemand.

i've tried a few mainstream distro's and this seems to be a common problem.

Pentium M 2Ghz EST flag in /proc/cpuinfo

seems to be a problem none of the devs want to fix.

---

### Post by ft_ on 2011-09-08
I just want to add that battery usage is lower with kubuntu 11.10 than 11.04.
I do not use desktop effects.

---

### Post by JonM33 on 2011-09-08
I really didn't have any negative change in my battery life. No significant positive change though either.

---

### Post by cariboo on 2011-09-08
I'm running a pretty unscientific experiment on my netbook. Previously I was getting about 2.5 hours of battery usage, yesterday after a fresh install I ran:

```
powertop --calibrate
```

since then I've gotten 3 hours, with a notification just popping up that I've got 20 minutes left before it goes into hibernation.

I've done updates and rebooted a couple of times. My netbook is an atom 270 powered Compaq Mini 1100, with no pci-e to be seen.

I used powertop 1.97-2 that is available in the repositories.

---

### Post by aeronutt on 2011-09-26
I loaded Beta 2, and my battery usage is still at ~2500mW, compared to ~800mW using 11.40.  If this holds at final release, I don't see updating to Oneiric at 3X the power draw.

---

### Post by LinuxFan999 on 2011-09-26
Ubuntu 11.10 is not Final yet, so people shouldn't be expecting great battery life on laptops that have it installed. Battery life should be better once the final release of Ubuntu 11.10 comes.

---

### Post by cariboo on 2011-09-26
The developers are well aware of the problem, it has been suggested that at UDS-P this should be one of the items discussed and fixed for 12.04

---

### Post by tekstr1der on 2011-09-26
> **LinuxFan999 said:**
> Ubuntu 11.10 is not Final yet, so people shouldn't be expecting great battery life on laptops that have it installed. Battery life should be better once the final release of Ubuntu 11.10 comes.

You know this how? What bugs/sources are you tracking that promise power management/battery life improvements between beta 2 and release? You do realize just how strict they get on commits as of the final freeze (3 days from now)?

> FinalFreeze

EXTREMELY anal-retentive, high-caution period until the FinalRelease goes out. ReleaseTeam and relevant section team confirmed fixes only!

Exceptions requiring confirmation:

    Release critical bugs
    Security critical bugs
    Exceptional circumstances
    Acts of God, Buddha, Vishnu, Zeus, etc 


Or, is the "it's not Final yet", "it's alpha software, so expect bugs" just your canned response to people experiencing issues during the development cycle?

---

### Post by cariboo on 2011-09-26
> **tekstr1der said:**
> You know this how? What bugs/sources are you tracking that promise power management/battery life improvements between beta 2 and release? You do realize just how strict they get on commits as of the final freeze (3 days from now)?

Or, is the "it's not Final yet", "it's alpha software, so expect bugs" just your canned response to people experiencing issues during the development cycle?

It's more an uninformed answer, as the problem is with the kernel and not an Ubuntu specific problem, other distributions that use the same kernel are affected too. The problem won't be solved for this release, so we'll have to wait fro the kernel developers to fix the problem. It also doesn't affect all users, as you can see from my post above. 

Hopefully the problem will be solved for all users in 12.04.

---

### Post by tekstr1der on 2011-09-27
> **cariboo907 said:**
> It's more an uninformed answer, as the problem is with the kernel and not an Ubuntu specific problem, other distributions that use the same kernel are affected too. The problem won't be solved for this release, so we'll have to wait fro the kernel developers to fix the problem. It also doesn't affect all users, as you can see from my post above. 

Hopefully the problem will be solved for all users in 12.04.

I know, and understand this. As a linux system admin, I follow kernel development closely. I just get frustrated with the spread of disinformation on these forums. It seems more frequent these days. Sorry. I'll try to keep my posts helpful and informative.

---

### Post by kaldor on 2011-09-27
> **cariboo907 said:**
> The developers are well aware of the problem, it has been suggested that at UDS-P this should be one of the items discussed and fixed for 12.04

It's understandable to be present in 11.10. It's an upstream issue after all. I would consider this an extremely high priority bug for an LTS, though. If it isn't fixed by 12.04 it would be a huge dent to the "reliability" of Ubuntu.

A solution would be to work closer upstream in the manner that Fedora does. The problem with the Ubuntu project is that Canonical is trying to separate from the Linux world by doing their own thing (which is great) but is still tied down to the FOSS ecosystem and depends heavily upon it. Canonical needs to put more manpower into working upstream with the kernel. 

Hope I'm not coming across too arrogant, because I'm not intending to.

---

### Post by ventrical on 2011-09-27
> **kaldor said:**
> It's understandable to be present in 11.10. It's an upstream issue after all. I would consider this an extremely high priority bug for an LTS, though. If it isn't fixed by 12.04 it would be a huge dent to the "reliability" of Ubuntu.

A solution would be to work closer upstream in the manner that Fedora does. The problem with the Ubuntu project is that Canonical is trying to separate from the Linux world by doing their own thing (which is great) but is still tied down to the FOSS ecosystem and depends heavily upon it. Canonical needs to put more manpower into working upstream with the kernel. 

Hope I'm not coming across too arrogant, because I'm not intending to.

  It will take many hours of burning the midnight oil to get these bugs fixed ... and Canonical should take  note that Microsoft and Apple are fast on their heels with their newer version soon to be released and the competition is fierce.. so they have to really get Unity and other bugs fixed real fast or they will loose that cutting edge predominance in the overall scheme of the FOSS concept of things.

  Personally I think the newer workings of Unity are just great... but the PC -Tablet world is moving a lot faster than Unity and Compiz are right now. If their is crow to be eaten - Ubuntu will have the greater portion come release day.
 However , from what I've seen so far with the progressive development, I have a good confidence there are going to be some more surprises to come under the hood.

---

### Post by keithpeter on 2011-09-27
> **cariboo907 said:**
> I'm running a pretty unscientific experiment on my netbook. Previously I was getting about 2.5 hours of battery usage, yesterday after a fresh install I ran:

```
powertop --calibrate
```

since then I've gotten 3 hours, with a notification just popping up that I've got 20 minutes left before it goes into hibernation.

I've done updates and rebooted a couple of times. My netbook is an atom 270 powered Compaq Mini 1100, with no pci-e to be seen.

I used powertop 1.97-2 that is available in the repositories.

The --calibrate option has powertop switching various things on and off, it took about 5 minutes on this Asus EeePC 1000 also with an N270 processor. Powertop is claiming power use of 7.8W with the back light one level up from lowest and firefox running a couple of tabs. This is the lowest I've seen so far on this machine, comparing with 10.04

Is there a pattern around hardware to the laptops seeing lower battery life/ higher power draw? Anyone running a tally?

---

### Post by donniezazen on 2011-09-27
I wouldn't call it unscientific but I have not conducted tests and have no data to provide. Even after patching kernel line which reduces temp by 10C Ubuntu can't give me as good battery performance as Windows. On windows temp hangs around 47-50C and after doing all the tweaks temp is over 55C and hangs around 60-65C. Arch with same modifications give me better battery life than Ubuntu. I have run these setups consistently for a while to call them scientific results. I am running i7 2620M 2.7Ghz processor, 8GB RAM and Nvidia NVS4200 1GHz graphics.

---

### Post by keithpeter on 2011-09-27
> **donniezazen said:**
> I wouldn't call it unscientific but I have not conducted tests and have no data to provide. Even after patching kernel line which reduces temp by 10C Ubuntu can't give me as good battery performance as Windows. On windows temp hangs around 47-50C and after doing all the tweaks temp is over 55C and hangs around 60-65C. Arch with same modifications give me better battery life than Ubuntu. I have run these setups consistently for a while to call them scientific results. I am running i7 2620M 2.7Ghz processor, 8GB RAM and Nvidia NVS4200 1GHz graphics.

Hello donniezazen

Is that Ubuntu 11.10 worse than previous Ubuntu (i.e. the kernel power regression) or Linux in general worse than Windows (which I've seen mentioned for various kinds of hardware)?

---

### Post by donniezazen on 2011-09-27
> **keithpeter said:**
> Hello donniezazen

Is that Ubuntu 11.10 worse than previous Ubuntu (i.e. the kernel power regression) or Linux in general worse than Windows (which I've seen mentioned for various kinds of hardware)?

From what i read power regression issues have plagued several releases of kernel past 2.6.37 to 3.0. My old system Dell Inspiron E1505 did not suffer from kernel issues but the new system Thinkpad T420 is just too sensitive. In general, windows 7 gives me best battery life and lowest possible temperature compared to Linux. Arch is better than Ubuntu, in both power consumption and battery life, in my experience. Of course, it took me a couple of months to get Arch the way i want. Unlike Ubuntu which i love for it's simplicity.

My new system has a Sandy Bridge chip and Nvidia Optimus. Ubuntu does not handles optimus that well. Both power consumption and temp reduces significantly if i disable it from BIOS. Use it or not (as their is no default way to do it for now), it sucks up power.

For some reason flash, java, chromium, thunderbird, etc take too much cpu each around 20% making it worse.

---

### Post by aeronutt on 2011-09-27
> **donniezazen said:**
> From what i read power regression issues have plagued several releases of kernel past 2.6.37 to 3.0. ....

This is what I've read also, but this confuses me as to why my 11.04 (with 2.8 kernel) is running at 1/3rd the power of 11.10b2 (with 3.x kernel).

---

### Post by cariboo on 2011-09-28
@donniezazen, comparing Arch to Ubuntu is like comparing Apples to Oranges. If you installed all the same enhancements that Ubuntu does, your Arch install would show similar figures. You would be better off comparing Ubuntu to openSUSE or Fedora, because at least they aren't DIY distributions like Arch.

---

### Post by donniezazen on 2011-09-28
> **cariboo907 said:**
> @donniezazen, comparing Arch to Ubuntu is like comparing Apples to Oranges. If you installed all the same enhancements that Ubuntu does, your Arch install would show similar figures. You would be better off comparing Ubuntu to openSUSE or Fedora, because at least they aren't DIY distributions like Arch.

Apple vs Oranges is a cliche but you are right Arch is not for everyone. It is *nix anyways. The fact is usability. If Arch can get same thing done with significantly lower resources, it does not matter what Ubuntu offers. Philosophical discussions aside. I want to get back to Ubuntu but can't until these power and heating issues are fixed.

Thanks.

PS:-I am not complaining but reporting and willing to try solutions if you guys have any.

---

### Post by cariboo on 2011-09-28
> **donniezazen said:**
> Apple vs Oranges is a cliche but you are right Arch is not for everyone. It is *nix anyways. The fact is usability. If Arch can get same thing done with significantly lower resources, it does not matter what Ubuntu offers. Philosophical discussions aside. I want to get back to Ubuntu but can't until these power and heating issues are fixed.

Thanks.

PS:-I am not complaining but reporting and willing to try solutions if you guys have any.

Unfortunately, I don't see your issues being fixed for this release. You can setup a minimal Ubuntu installation that uses low resources, but you have to do it yourself, as there isn't a lot of documentation on the subject. The higher resource usage is due to the enhancements that Ubuntu uses in order to make the system easier to use for new/less experienced users.

---

### Post by donniezazen on 2011-09-30
What's up with this 100% PCI usage.

---

