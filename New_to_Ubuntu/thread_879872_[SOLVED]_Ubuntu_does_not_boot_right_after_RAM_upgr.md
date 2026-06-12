---
title: "[SOLVED] Ubuntu does not boot right after RAM upgrade"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by modman27 on 2008-08-04
I am having a problem with my Ubunty Hardy box. I installed it without a hitch, enabled the cube, got everything running fine. After some use I noticed it was starting to chug.

I forgot I used some of that system's RAM in another box and I was only running 256 MB. I know that 512 MB is recommended. So I went out and got 2 512 MB Dimms and figured that would fix the problem...I was wrong.

The motherboard sees the RAM and so does Ubuntu but it takes almost 20 minutes to get to the login screen, when before it only took 1 minute with 256 MB. ????

It says "loading please wait" then goes to a black screen for like 20 minutes. I have hit Alt F1 and watched as it struggles to go through the boot process and can't pin down where the issue is. 

Not only that, but it seems that Ubuntu runs slow at times once I finally get in the OS. 

Things I have tried:

I Disabling start up sessions like Blue tooth, find new hardware drivers, and a few others. 

Disabled swappiness

Took the 1 gig out and 256 back in - The 256 MB configuration is slow now too - ???

Reinstalled Ubuntu Hardy - took 30 min to boot the Live CD

Run the memtest86 - for about 3 hrs, no issues

Enabled ACPI - It was disabled for install
------------------------------------------------------------
I wonder if it is a Bios setting but not sure what to change. It is a MSI motherboard with a P4 and 1 Gig of RAM.
Any thoughts?:confused:

---

### Post by PCessna on 2008-08-04
> **modman27 said:**
> I am having a problem with my Ubunty Hardy box. I installed it without a hitch, enabled the cube, got everything running fine. After some use I noticed it was starting to chug.

I forgot I used some of that system's RAM in another box and I was only running 256 MB. I know that 512 MB is recommended. So I went out and got 2 512 MB Dimms and figured that would fix the problem...I was wrong.

The motherboard sees the RAM and so does Ubuntu but it takes almost 20 minutes to get to the login screen, when before it only took 1 minute with 256 MB. ????

It says "loading please wait" then goes to a black screen for like 20 minutes. I have hit Alt F1 and watched as it struggles to go through the boot process and can't pin down where the issue is. 

Not only that, but it seems that Ubuntu runs slow at times once I finally get in the OS. 

Things I have tried:

I Disabling start up sessions like Blue tooth, find new hardware drivers, and a few others. 

Disabled swappiness

Took the 1 gig out and 256 back in - The 256 MB configuration is slow now too - ???

Reinstalled Ubuntu Hardy - took 30 min to boot the Live CD

Run the memtest86 - for about 3 hrs, no issues

Enabled ACPI - It was disabled for install
------------------------------------------------------------
I wonder if it is a Bios setting but not sure what to change. It is a MSI motherboard with a P4 and 1 Gig of RAM.
Any thoughts?:confused:

Can it possibly be bad memory, and it is struggling to use the bad memory?

---

### Post by modman27 on 2008-08-04
Thats what I first thought but Memtest86 showed no issues(although I only let it run for 3 hours), and I put the old memory back in and had the same result.

---

### Post by Cresho on 2008-08-04
It could be that your ram is either, your using mixed memory speeds, bios is not configured correctly, voltages are wrong.

In any case, if your memory will not work.  Memory testing software will only work on correctly configured hardware.  It does not work on something that you "guestimated"<-is this a real word?.

check your bios, try to configure your memory according to spec.  I can't remember which one will boost it.  YOu probably disabled cache memory or something.  I cannot help you further since many bios are specific to a motherboard.  try optimized setting!

---

### Post by modman27 on 2008-08-04
The RAM is recommended by the motherboard manufacturer.

Do you know how I would verify that everything is configured properly?

---

### Post by DGortze380 on 2008-08-04
There are a lot of little things to worry about with ram. I would start by checking the voltages and timing. Just because the brand and size are recommended doesn't mean that it will work without an issue.

Timing will look something like 5-5-5-15, both that and the voltage should be listed on the packaging. Check it against your BIOS.

---

### Post by modman27 on 2008-08-04
i looked on the package for the ram and on the MFG's site and cannot find the DDR timing info. I looked on NewEgg and found the voltage so that is set at 2.5. 

I also looked at my motherboard MFG's website and they state that there are performance issues with the board if those settings are not set right in the bios. 

I called PNY and they are not open, is there a utility that will tell me that information?

I think that this is the issue, can anybody please help?

---

### Post by DGortze380 on 2008-08-04
> **modman27 said:**
> i looked on the package for the ram and on the MFG's site and cannot find the DDR timing info. I looked on NewEgg and found the voltage so that is set at 2.5. 

I also looked at my motherboard MFG's website and they state that there are performance issues with the board if those settings are not set right in the bios. 

I called PNY and they are not open, is there a utility that will tell me that information?

I think that this is the issue, can anybody please help?

try googling any serial/model numbers of the module, the timing is often printed right on the module too. I'm surprised newegg didn't list the timing, can you post a link to page for your RAM?

---

### Post by SunnyRabbiera on 2008-08-04
Well when I upgraded my ram I had a rough time making sure stuff worked, I ran into the same issues even under my windows system...
trust me this kind of issue isnt isolated to ubuntu.

---

### Post by modman27 on 2008-08-04
DGortze380:

I think that you are right about the root of the problem (thanks for all your help). I did google it and came up with nothing, execpt for the voltage. 

I also looked on the RAM itself and no dice. 

it is part number: D512MPC27OPTBB

going into a MSI 845GE max-L (MS-6580) with a P4

don't want to seem like I am lazy cause I have been looking for like 5 hrs.
but maybe someone else's researching skills are better than mine.

Please help...it would be much appreciated

---

### Post by aristotlewilde on 2008-08-04
I'd like to back Modman up here.  I have had similar issues w/ Hardy.  

First w/ a Celeron machine and later w/ a P4.  

I added new RAM, and both times, it would not boot.  First it was a Compaq machine )the Celeron) and next it was a Dell, so timings/voltage couldn't be changed.

The crappy part is, Windows installed and booted fien on both machines.  

Sticks of RAM tested to be fine.  

After some experimentation, I actually was able to get one of the new sticks of RAM (pc3200) to mix with a stick of pc2700 and boot/run normally.  

As soon as I add a second stick of PC3200, it stops booting.  

There seems to be some bit of finicky with the new kernel.

---

### Post by DGortze380 on 2008-08-04
> **modman27 said:**
> DGortze380:

I think that you are right about the root of the problem (thanks for all your help). I did google it and came up with nothing, execpt for the voltage. 

I also looked on the RAM itself and no dice. 

it is part number: D512MPC27OPTBB

going into a MSI 845GE max-L (MS-6580) with a P4

don't want to seem like I am lazy cause I have been looking for like 5 hrs.
but maybe someone else's researching skills are better than mine.

Please help...it would be much appreciated

You're right, thats very odd, I can't find the timing for this module anywhere I've looked. I would just call PNY tomorrow. 

If it helps some common timings (currently) is 5-5-5-15 or 4-4-4-12. try these if you like, **DISCLAIMER** Using the wrong timing my permanently damage your memory or motherboard. **END DISCLAIMER**

---

### Post by modman27 on 2008-08-04
I have built many Windows machines and swapped memory and never had an issue before.(Not badmouthing ubuntu, I love it, and am trying to move away from windows for good)  Also I have never done any overclocking. So this timing is a little new to me. 

Can someone explain the numbers what the numbers mean?

Is that the CAS latency, and other settings found in the DRAM timing section of the bios?

---

### Post by DGortze380 on 2008-08-04
> **modman27 said:**
> I have built many Windows machines and swapped memory and never had an issue before.(Not badmouthing ubuntu, I love it, and am trying to move away from windows for good)  Also I have never done any overclocking. So this timing is a little new to me. 

Can someone explain the numbers what the numbers mean?

Is that the CAS latency, and other settings found in the DRAM timing section of the bios?

yes it is, let me go pull up a link.

EDIT:
Honestly I never looked into enough to be able to explain it well, but check this out: [http://en.wikipedia.org/wiki/RAM_latency](http://en.wikipedia.org/wiki/RAM_latency)

---

### Post by hansdown on 2008-08-04
The most I've found is it is 333 MHz.

[http://www.shopwiki.com/detail/d=PNY_-_Optima_512MB_PC2700_DDR_DIMM_Memory_-_D512MPC27OPT-BB/jumpToFirst=t/](http://www.shopwiki.com/detail/d=PNY_-_Optima_512MB_PC2700_DDR_DIMM_Memory_-_D512MPC27OPT-BB/jumpToFirst=t/)

Also your mobo.  [http://www.msicomputer.com/product/p_spec.asp?model=845GE_Max-L](http://www.msicomputer.com/product/p_spec.asp?model=845GE_Max-L)

---

### Post by Cresho on 2008-08-05
one time I disabled a ram feature and took my operating system like 10 minutes to boot.  I cannot recall what caused this but in bios, there is a setting, "set optimized setting"  I clicked that and it ran fine after.This setting autodetects and adjusts things accordingly

Just because a manufacturer says it only supports these types of rams, it does not mean it does.

try the optimized settings in bios.

i will see if i can replicate this in my system and post what setting caused slow boot

---

### Post by DGortze380 on 2008-08-05
> **Cresho said:**
> one time I disabled a ram feature and took my operating system like 10 minutes to boot.  I cannot recall what caused this but in bios, there is a setting, "set optimized setting"  I clicked that and it ran fine after.This setting autodetects and adjusts things accordingly

Just because a manufacturer says it only supports these types of rams, it does not mean it does.

try the optimized settings in bios.

i will see if i can replicate this in my system and post what setting caused slow boot

It depends entirely on his motherboard, not all boards and bios have the same settings and options. Definitely take a look in the BIOS, but I would also try to find the timing info.

---

### Post by hansdown on 2008-08-05
> **hansdown said:**
> The most I've found is it is 333 MHz.

[http://www.shopwiki.com/detail/d=PNY_-_Optima_512MB_PC2700_DDR_DIMM_Memory_-_D512MPC27OPT-BB/jumpToFirst=t/](http://www.shopwiki.com/detail/d=PNY_-_Optima_512MB_PC2700_DDR_DIMM_Memory_-_D512MPC27OPT-BB/jumpToFirst=t/)

Also your mobo.  [http://www.msicomputer.com/product/p_spec.asp?model=845GE_Max-L](http://www.msicomputer.com/product/p_spec.asp?model=845GE_Max-L)


Most of the info is here.

---

### Post by DGortze380 on 2008-08-05
> **hansdown said:**
> Most of the info is here.

but not the timing, and thats the only thing he hasn't been able to verify.

---

### Post by modman27 on 2008-08-06
I finally figured out the problem! 

Turns out the timing was not the issue, although thinking so pointed be me in the right direction. 

(By the way PNY would not give me the timing info because they said they don't like people overclocking their products...WTF??)

It was a setting in the bios for "Internal Graphics Select." I set it to 8 MB which is the highest setting I could use.

I don't fully understand why this would of caused a problem, but it kinda makes sense. When the problem existed there was no Ubuntu status bar when booting. Only a blank screen for about 20 minutes until the login screen appeared. Once I changed the Internal Graphics Select setting, the status bar appeared and the system booted in 1 minute.

Maybe the system was struggling to load that screen? I dunno...
----------------------------------------------------
I have never posted on the forum before, although I have read through them. I was surprised to see how fast and willing everyone was to help me. Thanks to all!!!

---

### Post by cariboo on 2008-08-06
I've found with MSI motherboards if you set the default in BIOS and then change what you need, like boot order, they run like a top.

Jim

---

### Post by janesh on 2008-08-29
I faced the same problem and found the following solution. The steps are as follows:

1. Remove all the RAM disks and boot. You should here a beep sounds. There would be no display on the screen.

2. Shutdown the system by pressing on the power button.

3. Put the RAM disk(s) and boot the computer. This time the boot should be FINE.

This worked consistently for me.

---

