---
title: "How To: Disable cpu scaling in 9.04 and 9.10"
date: 2009-07-10
forum: Outdated Tutorials &amp; Tips
---

### Post by tad1073 on 2009-07-10
To disable cpu scaling you will need to install **"[SIZE=2][COLOR=Red]RCCONF[/COLOR][/SIZE]"**

**[SIZE=3]1. [/SIZE]**```
 sudo apt-get install rcconf
```**[SIZE=3]2[/SIZE].** To run it, open a terminal and enter:

```
sudo rcconf
```A list will appear in the terminal window, use the arrow keys to navigate and space bar to select, de-select options.

[SIZE=3]**3. **[/SIZE]For cpu scaling, look for **"[SIZE=2][COLOR=Red]ONDEMAND[/COLOR]"[/SIZE]**
Once at the entry, with the space bar un-check the box.

[SIZE=3]**4. **[/SIZE]To save the configuration hit the tab key so that "[COLOR=Red]**OK**[/COLOR]" is highlighted then enter to save and reboot.

CPU scaling should be disabled.

To undo the changes, repeat steps 2, 3 and 4.

---

### Post by Elep.Repu on 2009-07-11
I'm just curious.
For what reason would 
I do this?

---

### Post by Labello on 2009-07-11
Yeah that's what I am asking myself too.

---

### Post by tad1073 on 2009-07-11
Well, this tut. would be mainly for desktops. I have a 2.67 core 2 quad which gets scaled down to 1.6. If I wanted a 1.6 then I would have bought a 1.6 not a 2.67. So, for me this works fine, besides, I have been in threads that talked about cpu scaling so I wrote this tut. for those people that are like me.

---

### Post by Arup on 2009-07-11
The speedstep is a power saving featrue incorporated by CPU manufacturers to save power and run the CPU cool. Disabling it will have no performance gain as most CPUs scale quite well on demand. In case you do wish to set it at performance level permanently, all you have to do is right click on top gnome panel and select CPU frequency scaling monitor which allows you to do what you intented to via an easy GUI.

---

### Post by tad1073 on 2009-07-11
> **Arup said:**
> The speedstep is a power saving featrue incorporated by CPU manufacturers to save power and run the CPU cool. Disabling it will have no performance gain as most CPUs scale quite well on demand. In case you do wish to set it at performance level permanently, all you have to do is right click on top gnome panel and select CPU frequency scaling monitor which allows you to do what you intented to via an easy GUI.

When you reboot, cpu scaling reverts back to ondemand, with the method in my tutorial it doesn't.

---

### Post by houseonfire on 2009-07-12
When the processor needs to speed up it will.
It is scaled down the extend the processors life span

---

### Post by Copernicus1234 on 2009-07-12
I just disabled it in BIOS.

---

### Post by Barph633 on 2009-11-12
So, I really need to disable this, but I'm just unable to do so.  Here's what I've done so far:

1.  Tried the rcconf in this thread.  No joy.
2.  Modified the scaling_min_freq (it resets after a reboot) to be hard set at my max clock speed.
3.  Hard set my system on "Performance".
4.  Disabled acpi in the kernel (won't boot).
5.  Disable acpi in rcconf (cpu still modifies frequency)
6.  Set "Performance" governor to always use 1200000, but again no luck.
7.  Set chmod -x on all CPU related items under rc#.d.
8.  Verified that I had no CPU related items installed through Synaptic.

So, I've got an Intel Core2Duo 1.2Ghz processor on a Dell D430.  Before someone tells me that I shouldn't need to do it because it will use the CPU when it needs it, I should be saving power, or I should disable it in the bios so here's why I'm doing it.  This is the third site I've posted about this, and for some reason nothing elicits a smart alec response about why I'd want to do this as much as this question.

First, if I disable speedstep in the bios it sets the speed to the lowest step (800mhz) at all times.  There is no way to turn it off to set it at 1.2Ghz.  I very rarely use my PC on battery power, and when I do it's not for long periods of time.  

Scaling just doesn't seem to work properly at all.  There are times when I'm 100% on both CPU's and it's still scaled at 800mhz, so it's obviously not scaling correctly no matter what I've tried.  Manually setting the CPU applet to 1.2Ghz immediately reverts back to what it wants to run at.  Using the cpu-freq-utils does the same as the applet.  Basically, no matter what setting I've messed with the CPU still steps the speed down at random times, and it's very frustrating.

One other note:  In Jaunty, I simply had to remove the cpu frequency utility from Synaptic and it held my CPU at 1.2.  Ever since the upgrade to Karmic I've been unable to do anything about it.

Hopefully someone has some information that can help me here.  I'd appreciate any help I can get.

---

### Post by cupantae on 2009-11-14
I just want to say that for me, this does give a very noticeable performance boost. I don't know is it just that my cpu doesn't scale well or what. If you don't need to do it, great, but I don't think there's anything wrong with wanting your processor to work as it says on the box.

Also, tad1073 there's a typo in your first post. it says
```
sudo apt-get install rdconf
```
instead of
```
sudo apt-get install rcconf
```

...And finally, thanks very much!

---

### Post by ahnise on 2009-11-24
had problems following direction with installing 

"sudo apt-get install rdconf" 

I think this is a typo. the following command worked:

 "sudo apt-get install rcconf"

---

### Post by amilak on 2010-01-09
I have this system which freezes when cpu scaling is on. Disabling from BIOS does not work. In one of the previous versions of ubuntu I manage to fix it by removing "powernowd". Recently I installed mythbuntu 9.10 in to this system and ran in to the same problem and when I check "powernowd" already not installed. So I was searching for a solution and came across this post and followed your instructions... it worked like a charm. Now no more system freezes.

Thank you very much!! This was really useful :D

---

### Post by ALIENDUDE5300 on 2010-01-09
When a CPU is scaled down, it's to make it last longer. I was able to get my Core2 Quad to at least 90% on all cores without disabling this, because of the tasks I am doing. There is no good reason to turn CPU scaling off, as it makes your CPU last longer and saves power which results in you paying less on your electricity bill.

---

### Post by SlugSlug on 2010-01-09
> **Copernicus1234 said:**
> I just disabled it in BIOS.


+1

:popcorn:.............

I leave mine as my CPU is rarely / never maxed out in ubntu so why waste the power / generate heat?

---

### Post by amilak on 2010-01-10
This method may not be for everyone but cases like mine (I explained earlier) it is a must do thing, so this works.


By the way after I did this I did a software update (including kernel) and "ONDEMAND" was enabled again. Had to go to safe mode and disable it again.

---

### Post by Kixtosh on 2010-01-29
I tried this (with the spelling correction mentioned) on an old Toshiba Portégé (see signature)  but it doesn't help. The Mobile Pentium III Speedstep is limited to 500MHz, and always shows as 500MHz (when I add the tool in the top panel). 

Thas has been the case ever since I loaded a Live CD of Knoppix 3.7 in 2005! It doesn't even show correctly in Windows any more (it did before). It should have a maximum of 700 MHz, and I have never found anything I could do about it.

If anyone has any ideas, it would be terrific, because it's been a great workhorse, and only weighs about 3 lbs, despite is age.

FYI, the System Monitor identifies the CPU as a Pentium III Coppermine. I'm not even convinced that this information is correct!

---

### Post by HostileJava on 2010-02-01
Let's be honest, I've read at least two posts in here stating that CPU scaling is to extend the life of the CPU.  It's not, if the CPU is used as designed chances are it will not fail within it's lifetime.  It's for power savings and that's it.  When is the last time anyone has had a CPU go bad when running it at it's rated clock setting.  I think I've run across one that died on it's on in my 10 years of being a tech.  Most of the time they get burnt up from being overvolted, overclocked, some combination of the both, lack of cooling due to a fan failing or heatsink falling off, or some sort of power surge.  

> **ALIENDUDE5300 said:**
> When a CPU is scaled down, it's to make it last longer. I was able to get my Core2 Quad to at least 90% on all cores without disabling this, because of the tasks I am doing. There is no good reason to turn CPU scaling off, as it makes your CPU last longer and saves power which results in you paying less on your electricity bill.

---

### Post by Kixtosh on 2010-02-01
> **HostileJava said:**
> Let's be honest, I've read at least two posts in here stating that CPU scaling is to extend the life of the CPU.  It's not, if the CPU is used as designed chances are it will not fail within it's lifetime.  It's for power savings and that's it. ... Well, without any technical expertise in the field, I'd tend to agree with you, FWIW. 

I also wonder how much real power you could possibly save ... I mean: my laptop power supply is something like 40W or maybe 70W, and that includes everything, so how much power would I really save? How much power does a desktop actually use, without the screen? Perhaps limiting the processor also limits the amount of power needed to drive the fans or something? Would you even save $10 in a whole year? Maybe somebody could do some testing with a Kill-A-Watt meter to measure actual consumption between the different settings ...

I suppose it adds up, if everybody does it ...

---

### Post by Barph633 on 2010-02-13
For what it's worth, I still haven't figured out how to disable this.  It's extremely annoying, and more so to have people ask "whey would I do this" crap when someone is just asking how to make their PC work better, and especially on Linux where everything is supposed to be configurable and you're supposed to have complete control over your OS, and everyone hates Windows, etc.  Bottom line, if I want to do it, I should be able to.  Who cares why I would want to?

Look, not all PC's work the same, and some, like my Dell Latitude D430 just don't handle CPU scaling well.  I'm on here right now becasue I'm trying to watch a video on my TV from my laptop, and since it's a flash video it takes a lot of CPU.  Fine, but my laptop, no matter what I do won't go over 800mhz.  So, I've got freezing video, can barely even bring up firefox, and it's taken me 20 minutes to type this stupid post.

All I want is to disable CPU scaling.  I don't understand why it's so hard to do.  I'm getting fed up with Ubuntu, and I'm about ready to go back to XP, where I don't have to worry about this crap.  For the last 3 years I've used Linux, and you know, for all the fixes I've had to do to make things work, everything has been OK because I like the feel, but this is a deal breaker.  If I can't get CPU scaling (and no the fixes in this thread have done nothing to help) then I'm just done with it.  To utilize 2/3 of my CPU power on a regular basis is just stupid.

Sorry, but the responses here are egotistical and ridiculous.  Basically all I've heard is "Deal with it, my computer has never used all I need so it doesn't matter, and why would you want to use more energy?"  I don't care if I have a gas generator running my house at $2 an hour, if I want my Computer to run at 1.2Ghz at all times I should be able to make it do so...

---

### Post by Natty Dreed on 2010-02-13
Thank  u 

i was looking for this long time ;)
I have a dead battery and not looking for power-safe 
easy to follow tutorial ^

---

### Post by auh2o on 2010-02-13
> **Barph633 said:**
> Bottom line, if I want to do it, I should be able to.  Who cares why I would want to?

I'm sorry, you failed to give a complete bottom line. Here, I'll fix it for you:

If you want to do it, you should be able to. Nobody cares about why you would want to. But if you want others to do it, then it is advisable to give them an explanation as to why it would be at all desirable to them in the first place, and which results it would yield. Otherwise, your information would be of less value. Of course, there is always Google, but then again that could be said for the complete How-To, could it not? If you bother to say A, then why not say B?

---

### Post by nanohead on 2010-02-25
Thanks for this.  I hope it works.   I hate that CPU frequency control has no adjustments in 9.10, really ridiculous.   I don't need the Ubunutu developers to decide what my power policies are going to be.  I can do that myself.   I like snappy performance (and Compiz wobbly windows too!)

Sometimes it throttles back and is so slow I want to pull my hair out (if I had any).    I like power management, but this is ridiculous.

And for those here with silly opinions about it...   Automatic frequency scaling as enabled by the CPU vendors has ZERO to do with CPU life.  It originally came from laptops for battery life extension.  For desktops, it started with the noisy fans, where the only way to lower the noise was to lower the clock speed so it wouldn't produce so much heat.  

Now it has become intrusive, where nearly ALL desktop enthusiasts I know turn it off immediately, both in BIOS and in software (Windows allows this).   I even turn it off on my laptop.  Slow is slow, period.  If I want torture, I'll use my netbook (OMG its slow)

Anyway, thanks and I hope it actually works.

---

### Post by Rebootkid on 2010-05-16
> **Barph633 said:**
> For what it's worth, I still haven't figured out how to disable this.  It's extremely annoying, and more so to have people ask "whey would I do this" crap when someone is just asking how to make their PC work better, and especially on Linux where everything is supposed to be configurable and you're supposed to have complete control over your OS, and everyone hates Windows, etc.  Bottom line, if I want to do it, I should be able to.  Who cares why I would want to?

Look, not all PC's work the same, and some, like my Dell Latitude D430 just don't handle CPU scaling well.  I'm on here right now becasue I'm trying to watch a video on my TV from my laptop, and since it's a flash video it takes a lot of CPU.  Fine, but my laptop, no matter what I do won't go over 800mhz.  So, I've got freezing video, can barely even bring up firefox, and it's taken me 20 minutes to type this stupid post.

All I want is to disable CPU scaling.  I don't understand why it's so hard to do.  I'm getting fed up with Ubuntu, and I'm about ready to go back to XP, where I don't have to worry about this crap.  For the last 3 years I've used Linux, and you know, for all the fixes I've had to do to make things work, everything has been OK because I like the feel, but this is a deal breaker.  If I can't get CPU scaling (and no the fixes in this thread have done nothing to help) then I'm just done with it.  To utilize 2/3 of my CPU power on a regular basis is just stupid.

Sorry, but the responses here are egotistical and ridiculous.  Basically all I've heard is "Deal with it, my computer has never used all I need so it doesn't matter, and why would you want to use more energy?"  I don't care if I have a gas generator running my house at $2 an hour, if I want my Computer to run at 1.2Ghz at all times I should be able to make it do so...

Ever heard the phrase, "Catch more flies with honey?"
You're acting entitled to help, rather than asking nicely.

I get that you're frustrated, and rightfully so, but taking it out on the volunteers who are in a position to help you, so not the proper way to do it.

Lastly, I've got a Dell 1330, and had the same problem. Updated the BIOS to version A15 from Dell's website, and then the  CPU Frequency Scaling Monitory worked. Just added it to the system tray in Lynx, selected 2.0ghz, and I'm off and running.

For those who want to know the "why" question: I run Portal via Wine on my laptop. If the CPU scales in the middle of the game, the sound lags out.

---

