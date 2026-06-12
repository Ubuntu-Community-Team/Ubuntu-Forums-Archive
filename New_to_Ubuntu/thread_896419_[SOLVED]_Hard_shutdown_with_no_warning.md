---
title: "[SOLVED] Hard shutdown with no warning"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by talsemgeest on 2008-08-21
There is quite a serious problem with my computer. Quite randomly, it will suddenly shut off, almost like a power cut but with power still supplied. Most often when I try to turn it back on, all that happens is the hard drive light flashes once and the fans in the case twitch, before turning back off. After switching off the power for a few minutes it will usually allow me to turn it back on.

I am very sure that it is a hardware error, as it happens both on windows and ubuntu, and after a reinstall of both os's. I have also reset the bios settings to the defaults, changing only what is necessary, so I am reasonably sure the problem does not lie there, however I am not 100% sure.

After the hard shutdown, I have felt the different components to rule out overheating. Case temperature is only a few degrees hotter than the external temperature, CPU feels well below 40, HDDs feel a bit hotter, possibly 45 degrees C.

The shutdown seems to be reminiscent of when my graphics card failed, being an instant shutdown with the computer refusing to start until the graphics card was removed.

What I really want to know is if there is any way of narrowing the problem down to a specific component, and find out what the specific problem is and how to fix it. All help/comments are welcome and appreciated.

Just in case it helps, here are my system specs:

AMD athlon 4200+
Asus m2a-vm hdmi motherboard
2 x 1GB DDR2 667 RAM
Creative sound blaster audigy OEM
Asus P7131 Hybrid tv tuner card
Asus DVD RAM drive
Floppy drive
40GB IDE HDD with ubuntu 8.04 installed
160GB WDC SATA HDD and 320GB Seagate SATA HDD set up with fake raid) to make:
320GB RAID0 with vista installed
160GB in RAID0 with itself as a backup HDD

Thank you in advance for your help.

---

### Post by coffeecat on 2008-08-21
> **talsemgeest said:**
> After switching off the power for a few minutes it will usually allow me to turn it back on.

It could be many things, but this sounds like the CPU overheating.

> **talsemgeest said:**
> CPU feels well below 40

How long after the shutdown did you feel it? If you mean that the heatsink on the CPU cooler didn't feel particuarly warm, that doesn't necessarily mean the CPU isn't too hot. If you mean that you can feel the CPU directly, do you actually have a CPU cooler? What type is it? Is the fan working?

Go to Synaptic and install one or both of 'computertemp' and 'gkrellm'. The first is a Gnome panel app, the second a stand-alone app and both will give you a readout of CPU temperature **if** your motherboard supports this. See what temperature you are getting just before shutdown. Also, check in the BIOS to see what temperature is selected for autoshutdown - I know you reset to defaults but it would be useful to know what the actual tripping temperature is.

---

### Post by jonabyte on 2008-08-21
I'd have to agree with the above, probably the cpu overheating as it will definitely cause the system to shutdown without warning.

It could also be the power supply, I have seen that in the past as well.

---

### Post by talsemgeest on 2008-08-21
> **coffeecat said:**
> How long after the shutdown did you feel it? If you mean that the heatsink on the CPU cooler didn't feel particuarly warm, that doesn't necessarily mean the CPU isn't too hot. If you mean that you can feel the CPU directly, do you actually have a CPU cooler? What type is it? Is the fan working?

Sorry I wasn't more specific, I just felt the heatsink, and that felt only slightly warm. I am using the stock cpu cooler, with some aftermarket thermal paste.

The fan that is on the heatsink is controlled by the motherboard, with the speed lowered when the temperature is low, and is sped up when the cpu gets hotter. The speed hasn't notably sped up so I assume the temperature being reported by the cpu is well within limits.

As for it being the power supply, is there any way of confirming that, other than buying a new psu?

---

### Post by coffeecat on 2008-08-21
> **talsemgeest said:**
> As for it being the power supply, is there any way of confirming that, other than buying a new psu?

Have you got a PSU in another machine you could try out? Or could you borrow one? I can understand you not wanting to go to the expense of buying one and finding it makes no difference.

Back to the CPU temperature though. With the fan behaviour you describe I agree this is unlikely to be the problem, but try one or the other of the apps I suggested.

Another thing is to look in /var/log/messages. Do this after an unexpected shutdown and check the messages for the minute or so before it shut down. There might just be a clue there.

How about faulty memory? Except that if the machine was behaving OK until recently this is unlikely.

---

### Post by talsemgeest on 2008-08-21
Unfortunatly the only other psu I have has too low of a power rating, so that is out of the question, and I don't think my friends would want to go without a psu for a day. But even then, the problem seems random, I can't reproduce it when I want to and so I can't say for sure that the problem is still there or if it is fixed.

As for the programs you suggested, computertemp stayed at 40 degrees, no matter what the load which means that it is not properly detecting the temperature. As for the other one, should I start it from the command line, because I don't think it is on the menu.

I think I will run memtest tonight to make sure it isn't a memory related problem.

---

### Post by coffeecat on 2008-08-22
> **talsemgeest said:**
> As for the programs you suggested, computertemp stayed at 40 degrees, no matter what the load which means that it is not properly detecting the temperature. As for the other one, should I start it from the command line, because I don't think it is on the menu.

That's a pity about computertemp. That's possibly an incompatibility with the data coming from the motherboard, because it works fine for me in a couple of machines, but in an older one it tells me the temperature is fluctuating rapidly between -20C and 140C - or something like that. :?

Sorry - I forgot that you don't get a menu entry for gkrellm. I had to add one myself. It's simply 'gkrellm' from the command line. Right-click on the upper right corner of the gkrellm window, or away from the data areas, to do general configuration. CPU temp is not switched on by default - you'll find that under options > builtins. And you'll probably need to increase the width of the gkrellm window in the main options pane.

Having said that, I believe gkrellm relies on the same kernel sensors as computertemp, so you may get the same result. I only suggested both apps, because gkrellm is more comprehensive than computertemp, but it uses more screen area.

---

### Post by talsemgeest on 2008-08-22
I am going to be switching back to windows for a bit to play some games, so I will use the utilities that came with my motherboard to monitor the temperature from there.

---

### Post by talsemgeest on 2008-08-24
I have noticed that the temperature of my cpu is higher than it used to be. It used to average around 35, going up to 40 under load. Now it averages 45 going up to 60 under load. It seems that it is more likely to happen when under load (i.e. encoding video, playing games, watching 1080 h.264 streams...) but still havent been able to get an accurate temperature reading just before shutdown.

Also, once it has shutdown it is getting more and more unlikely that pushing the power button will turn my computer back on. I have ruled out my pci devices and my hard drives being the problem by unplugging them and then seeing if my computer will turn on, but none of them did anything. It certainly seems like a heat problem as the longer I leave my computer off the more often it will turn back on. I am also starting to see it turn on, get to the os loading screen only for it to shut down there.

This is effectively driving me crazy. All help is very very welcome.

---

### Post by talsemgeest on 2008-08-25
This morning it shut down at a temperature of around 36, so I dont think that the problem is entirely cpu overheating. Unfortunately that last shutdown has killed my computer. I have taken out all the parts except my motherboard, PSU and cpu, and the exact same thing happens when I try to turn it on (Fans twitch then nothing). When I take the cpu and turn it on the same thing happens again.

So I am guessing it is either that my cpu is dead and because of that my motherboard doesnt pick it up, or my mother board is dead.

Any ideas/opinions?

---

### Post by aimpau on 2008-08-25
Is your CPU overclocked?
Did you smell something like melted plastic?
If you turn your board on, does it still turn on?

I think this is a case of overheated CPU.

Try this setup after you've cooldown your PC:

1. 1GB Memory
2. Ubuntu HD
3. Mouse
4. Keyboard
5. Monitor

Remove everything else. Clean your PC case.
If it turns on, go to BIOS, reset everything.

I also notice that you only have a TV tuner? No vidcard? Are you using the onboard VGA?

---

### Post by talsemgeest on 2008-08-25
> **aimpau said:**
> Is your CPU overclocked?
Did you smell something like melted plastic?
If you turn your board on, does it still turn on?

I think this is a case of overheated CPU.

Try this setup after you've cooldown your PC:

1. 1GB Memory
2. Ubuntu HD
3. Mouse
4. Keyboard
5. Monitor

Remove everything else. Clean your PC case.
If it turns on, go to BIOS, reset everything.

I also notice that you only have a TV tuner? No vidcard? Are you using the onboard VGA?
I had actually underclocked my cpu before it finally gave out, and the last temperature I saw (maybe 30 secs before the final shutdown) was 36 degrees, which makes me think it is not a simple burnout of the cpu.

However, when I took the cpu out the thermal paste was like cement. I tried to pull the heatsink off but ended up ripping my cpu out of its socket. I really dont think it should be like that since the paste has only been there for about 7 months.

I tried turning the computer on with only a motherboard and PSU, all it did was make the fans twitch for a second, and then shut off, and after that the power button does nothing until I pull out the power plug for a few seconds. If I put the CPU back in I get the same results. If I put everything else in I also get the same results.

I suspect that if the motherboard does not detect a cpu it would shut down, so perhaps that is why I get the same result with and without the cpu installed?

I have cleaned out every speck of dust that I could and have stuck every part back in except the cpu.

As for the graphics, I am using the inbuilt ati Radeon x1250 graphics on my motherboard. I got a Nvidia 9600GT a few weeks ago but that died and the shop refuses to fix it until I replace the chipped fan. But for most of my purposes the X1250 has been fine.

---

### Post by vasiauvi on 2008-08-25
I had the same problem on one of my PC's and a BIOS reset was enough. You can try it!!

---

### Post by talsemgeest on 2008-08-25
> **vasiauvi said:**
> I had the same problem on one of my PC's and a BIOS reset was enough. You can try it!!
I have. CMOS has been reset thereby resetting the bios as well. Still nothing...

---

### Post by cocodaclown on 2008-08-25
I had this problem with the wifes computer. It turned out to be nothing more than a fried PSU. 

Before going through the expense of buying new cpu etc, I would go to your local dealer, get a new psu and try it. If it still fails then at best you can return said psu or at worst you have a new psu for you next machine. Not incredibly helpful I know, but in my experience, 9/10 its the psu thats failing.

---

### Post by talsemgeest on 2008-08-26
I did a few tests today, just on the power supply however. First I plugged my power supply into another computer, and that worked. Then I plugged the power supply from that computer into mine and mine turned on. Then I put my PSU back into my computer and almost everything worked. Admittedly I hadn't actually tried to turn the computer on today, so I can't say if it was something I did or just time passing that fixed it.

Only problem is that when I first turned my computer it gave me and error message about usb using dangerous voltage (or something like that any way), and gave me 20 seconds before it shut down. I changed the setting in the bios to turn off EHCI(? USB 2.0) and then it does turn on, however with no USB 2.0 or usb on the front panel.

---

### Post by thumper13 on 2008-08-26
> **talsemgeest said:**
> 
The fan that is on the heatsink is controlled by the motherboard, with the speed lowered when the temperature is low, and is sped up when the cpu gets hotter. The speed hasn't notably sped up so I assume the temperature being reported by the cpu is well within limits.


Just a thought... Back when I ran windows, one of the TSR programs in windows was used to control the fan speeds. When I switched to Ubuntu, I was experiencing some issues similar to this, and it turns out the program would increase/decrease speeds in windows, but would default to the "low" setting without the TSR program. Something you could research about?

---

### Post by talsemgeest on 2008-08-26
> **thumper13 said:**
> Just a thought... Back when I ran windows, one of the TSR programs in windows was used to control the fan speeds. When I switched to Ubuntu, I was experiencing some issues similar to this, and it turns out the program would increase/decrease speeds in windows, but would default to the "low" setting without the TSR program. Something you could research about?
Quite possibly. But the temperature doesn't seem to be a problem, even the lowest setting seems to keep the temperature at an acceptable level.

---

### Post by aimpau on 2008-08-27
Any updates?

Have you cleaned your RAM? Use a rubber eraser for cleaning the contacts.

Sometimes, the error isn't that obvious at first. I haven't replied to you yesterday because my PC won't boot up. It was stuck on the opening screen even before it loaded GRUB. My HD busy LED was alight all the time. The problem? Floppy disk drive. I don't know why but it's the cause of the error, so I just removed it.

I doubt it's your PSU since if it's broken, you couldn't have turned your PC on. I'm more leaning to your RAM, CPU or any other PCI cards that you may have,

Can you get a screenshot of your motherboard?

---

### Post by talsemgeest on 2008-08-27
Yeah, I will try to get a screenshot tonight. The good thing is, the problem still hasn't happened since the major breakdown. The only thing I can think of was that I replaced the thermal paste.

I have to agree with you on the power supply, my tests showed pretty conclusively that it still worked.
But as for the ram, I ran memtest for a few hours and it didn't kill my computer, so I think that rules out bad RAM. That pretty much leaves the cpu and the motherboard. I am leaning a bit towards the motherboard, because when I turned my computer back on, it gave me an error about high usb voltage, even though there were no usb devices plugged in.

---

### Post by aimpau on 2008-08-28
I don't know about your motherboard, but my USB frontpanel requires 8 distinct pins to be plugged in and that means 8 separate wires. Check your motherboard manual, probably the frontpanel was connected incorrectly.

About the thermal paste, let's just say, without it, it's like driving a ferrari w/o oil and fuel. :)

---

### Post by talsemgeest on 2008-08-28
Yeah, it is quite possible that they were plugged in wrong, but then I unplugged them and I still got the same error. I left it for a while and then everything worked, so I am guessing it was a charge that had built up in a capacitor by the initial wrong wiring that had caused the error. But now, even though I have ensured the right wiring I am getting an average 11 bytes p/s transfer speed, but I am going to have a play around to see what the problem is.

Sometime soon I will buy some high end thermal paste so hopefully that will help.

I am going to wait to see if the problem re-presents itself before I do much else. I know I havent actually done anything to fix the problem, but it seems to have gone into hiding for now. I won't mark the thread as solved just in case it flares up again, but I will leave it for now.

Thanks aimpau for all of your help, you have given me a lot to think about.

---

### Post by aimpau on 2008-08-28
Not just me, everyone else. :)

Also, try to add more fans. The intake in the lower part front of the CPU tower and the exhausts on the upper side, just above the processor and upper back of the tower.

---

### Post by talsemgeest on 2008-08-28
> **aimpau said:**
> Not just me, everyone else. :)

Also, try to add more fans. The intake in the lower part front of the CPU tower and the exhausts on the upper side, just above the processor and upper back of the tower.
I have lots of fans. I have one lower front intake, mid-side intake, upper back intake and one in the middle to keep the air flow going (not counting the ones in the PSUand the one on the fan). Surely that should be enough?

---

### Post by ralyon on 2008-08-29
I personally wouldn't rule out the psu yet. I didn't see anywhere that you had actually checked the voltage. Most mbs allow you check the voltages from the bios screen. I would run something intensive for a while to get the temps up and then immediately restart into bios and check the *voltage* there. If they're more than 10% off you should probably consider replacing it, more than 15% I would definitely recommend replacing it. Bad voltages can cause damage gradually and damage other hardware as a result.

Also, if you have a lot of fans they each take some voltage as well. If your psu is barely capable of handling the system, the fans might be pushing it over the edge.

Good luck,
ralyon

---

### Post by talsemgeest on 2008-08-29
Ok, I will look into it. Luckily I have a utility that lets me check the voltages from the os, unfortunately it is windows only...

---

### Post by talsemgeest on 2008-08-31
Ok it is the psu. Plug psu into motherboard and push power --- Nothing. Plug older psu into motherboard and push power ---fan starts spinning things start up etc...

The psu I'm testing with doesn't have all of the cables I need so I think I will go buy a new one.

Thank you to everyone who has helped out, you have really helped me out a lot.

---

### Post by stedevil on 2008-09-02
I was just about to reply to you that it's VERY likely your PSU.

I have very close to the same hardware setup (same MB and similar cards and number of HDDs) and I started having this sudden restarts and computer and failing to start before it cooled down. Though for me it happened only when running HOMMV under Wine for extended periods of time (otherways it runs without a hitch for weeks without reeboot). 

In any case, the fail to start again was a sure sign of overheating, but CPU wasn't too hot (I as well still tried underclocking both CPU and GPU without much luck). The only thing that possibly seemed a bit warm was the Motherboard North bridge chip. Then I once put my hand on the PSU... AUCH... My fanless PSU apparently was building up a LOT of heat, probably due to much increased powerdemands while running the 3D-game. 

Have a fan attached to the PSU now that I turn on when I play HOMMV... no more sudden crashes.


BTW The computertemp gnome panel util works on our motherboard. You just need to change the setting from Monitoring "ACPI" to "Kernel i2c sensor (hwmon)"

---

### Post by talsemgeest on 2008-09-02
Mmm thanks for that. Yeah, a new power supply has fixed the problem, and now I have a bit of power to spare. And thanks for the tip about the temp monitoring, I am sure that will come in handy...

---

