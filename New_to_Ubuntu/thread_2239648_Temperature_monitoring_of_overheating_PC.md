---
title: "Temperature monitoring of overheating PC"
date: 2014-08-15
forum: New to Ubuntu
---

### Post by AbleTassie on 2014-08-15
My PC is apparently overheating. It shuts down instantly without warning. It did this often with Lubuntu 13.10; I just upgraded to Lubuntu 14.04 LTS and it has done it a few times as well. I am afraid too high a temperature may damage the PC. 

It seems to be running pretty hot to the touch underneath the PC. I used Fedora 14 for years, and I don't remember it doing this. I don't remember it doing this with Windows XP either. 

QUESTION: What is the best way to monitor temperatures in the PC while using Lubuntu 14.04 LTS? 

I am dual booting Lubuntu 14.04 LTS and Windows XP.

QUESTION: Can I compare the temps while using Lubuntu 14.04 LTS with temps while running Windows XP? 

I read some stuff online that seemed to indicate that fan drivers in Lubuntu may not work well for my PC. My PC is a Toshiba Satellite L25-S1216 Laptop. Other than trying to clean dust out of the PC and maybe working with the software that runs the fans, I am not sure what else to do. Any comments or suggestions would be welcomed.

Thanks,

R.

---

### Post by QIII on 2014-08-15
Hello!

The easiest way to monitor is in a terminal.

You will first want to install lm-sensors

```
sudo apt-get install lm-sensors
```

Then go through

```
sudo sensors-detect
```

In the terminal:

```
watch -n 2 sensors
```

Which will update every two seconds (replace the 2 with another increment if you want).

There is also gkrellm, which is available in the repos.  If you want to go high-speed, you can start messing around with conky and end up with something crazy like this:

[ATTACH=CONFIG]255500[/ATTACH]

---

### Post by Sanctimonious_Ape on 2014-08-15
I use Psensor - low overhead, easily configurable, temps can trigger pop-up notifications, nice graphing (visually see how long your CPU can go at 100% before the temp gets too high, for example).  If your CPU is overheating, then make sure you minimize the impact of whatever app you choose by lowering the update frequency to something like every 3 seconds.

---

### Post by Sanctimonious_Ape on 2014-08-15
Might also wanna look at [this article](http://www.techrepublic.com/article/quiet-noisy-computer-fans-with-a-drop-of-oil/) in case your fan is in need of some TLC.

---

### Post by AbleTassie on 2014-08-15
Thank you Qlll and Ape,

Is there any way to monitor fan performance?

Is there any way to monitor temps in Windows XP, to see if this is an operating system problem or a PC problem? The article Ape cited suggests a Windows temp monitoring software called MotherboardMonitor. Some stuff I've read suggests that Ubuntu has some problems with fan control for certain kinds of PCs, but the factory Windows OS does not because the PC was designed for the Windows OS. Any comments on this?

Any suggestions as to determine if dust build up in the PC is a/the problem and how to deal with dust? 

Thanks,

R.

---

### Post by QIII on 2014-08-15
sensors should pick up whatever is made available by your motherboard.

From sensors:

```
fan1:        1266 RPM  (min =    0 RPM)
```

For Windows, speedfan is freeware.  It monitors temps, voltages, fan speeds, etc.

---

### Post by AbleTassie on 2014-08-15
Thanks again Qlll and Ape,

I installed lm-sensors, P sensor and Gkrellm. What I get from lm-sensors (as a 2 second read) is below. It appears to be just one temp, temp1 (there is, for example, no info about fans). From P sensor there is again, just one temp, temp1 and also % CPU usage. (P sensor also does have max temp and CPU usage and graph capability.) Temp1 in lm-sensors and P sensor looks the same. So it looks like the motherboard just has a temp1 sensor. I still have to figure out how to use Gkrellm. I read somewhere to remove the battery, I did that and I think may be helping. 

QUESTION: The readout from lm-sensors says 110 C is the critical temperature. Does that mean the PC will shut down at 110 C?

Temp1 seems to be leveling out at about 85 C, but that is with pretty low demand on the CPU.

Any other comments or suggestions you or anybody else has would be welcomed.

**lm-sensors readout:**

Every 2.0s: sensors                                     Fri Aug 15 11:15:37 2014

acpitz-virtual-0
Adapter: Virtual device
temp1:        +86.0°C  (crit = +110.0°C)

Again, thank you so much :p 

R.

---

### Post by Sanctimonious_Ape on 2014-08-15
According to the [specs on Toshiba's site for your laptop]("http://support.toshiba.com/support/staticContentDetail?contentId=1250449&isFromTOCLink=false"), you only have a single core CPU so that's fine ([s]Toshiba apparently skimped on a zoned temp sensor[/s] [*ed: I was probably wrong about this, see next message*], but I don't know how useful that'd really be anyway - mine's consistently lower than the CPU temp by a handful of degrees).  What I find odd is the "Crit" temp is 10°C above [Intel's own specs for that CPU]("http://download.intel.com/design/mobile/datashts/30311008.pdf") (thermal stuff is at the end) which say the design max is 100°C and that the CPU will shut down (presumably just stop working entirely) at 125°C.

Kinda suprised even at those specs because 100°C is the boiling point of water and extremely hot - there must be some significant cooling going on in that laptop to make it usable on, well... a lap top. :rolleyes:   Mine is similarly spec'd to yours (slightly older, I think), but uses an AMD CPU and it usually tops out at 73°C CPU temp when going full bore.

Regardless, if you continue having heat-related shutdown issues, maybe your laptop's heat sink isn't making as good a connection as it used to (due to being tossed around, maybe) or perhaps the fan on the heat sink needs some attention.  There's plenty of info on the web about thermal paste, heat sinks, etc. or get a decent repair shop to check it for you.  I've even seen people who expanded their laptop's thermal dissipation using thermal pads and aluminum foil, but you've really gotta know what you're doing there or you'll likely short something out and cause bigger problems.

---

### Post by Sanctimonious_Ape on 2014-08-15
Some further thoughts: 

> **RMcGinnis said:**
> 
Temp1 seems to be leveling out at about 85 C, but that is with pretty low demand on the CPU.

That seems rather high for idle to me.  What do you get when idle in Windows?  If about the same, then that lends credence to a heat sink/fan issue.  Until you get this sorted, you could also try setting "powersave" mode as [described here]("http://unix.stackexchange.com/questions/88136/linux-fan-control") although that will make your laptop run more slowly but should keep your hardware safe(r) until the thermal issue is tackled.  You might also experiment with the other modes listed to see how that works out.


> **RMcGinnis said:**
> 
**lm-sensors readout:**

Every 2.0s: sensors                                     Fri Aug 15 11:15:37 2014

acpitz-virtual-0
Adapter: Virtual device
temp1:        +86.0°C  (crit = +110.0°C)


Just noticed that it says "acpitz" - on my laptop that indicates the "thermal zone" sensor which is NOT the CPU sensor, but instead one located elsewhere on the motherboard.  If that's truly the case, then you do indeed have a problem and should get it looked into before you destroy the CPU (which the paranoia freak in me says might already be happening and is why you're not getting a proper CPU temperature, but it may just be a bug with your particular laptop).  Also, if Linux can't read the CPU temp properly, then it's probably not driving the fan properly due to that fact.

I'd definitely get on checking your laptop's temp under Windows straight away and decide what to do from there.  I couldn't find any info specific to your laptop, Linux, and fan issues, so it may well be a hardware cooling problem.

---

### Post by AbleTassie on 2014-08-15
Thanks, I am educating myself about disassembly, cleaning of dust,thermal paste between the CPU and heat sink (Arctic Silver seems popular,) etc. May also take it to somebody.

R.

---

### Post by Sanctimonious_Ape on 2014-08-16
I woudn't play with the heat sink directly if you're unsure what you're doing - it's easy to mess up the thermal conductivity if you don't get it right.  Start with a good cleaning, certainly (don't use WD40, though - will eat plastics and cause short circuits) - then see how it runs.  But you really should confirm whether it's just under Linux that you have this problem before you go much further than that and risk permanent damage to your laptop by taking it apart.  Odds are that it really is the hardware needing attention, but you should always try to confirm that before performing open heart surgery on it.

I'd also try to find out if you can get a true CPU temperature reading under Windows.  If you can get one there, but not under Linux then you risk damage to your laptop due to Linux mismanaging your fan because it doesn't know the true CPU temperature.  You might still be able to get away with it like that if you stay on top of keeping an unobstructed air flow for your laptop, but if that's what you wind up doing then remember to keep an eye on the temperature for the long haul.  Also realize that running hot like that **will** shorten both the CPU's *and* the battery's lifetimes (and potentially any other nearby heat-sensitive/expanding parts such as the hard drive).

Whatever you do, I wish you luck.

---

### Post by AbleTassie on 2014-08-16
I think my laptop, a Toshiba Satellite L25 S1216 is overheating. It shuts off without warning. It is 8 1/2 years old and has never been cleaned.

In lm-sensors I get a readout of: 

Every 2.0s: sensors                                     Fri Aug 15 22:54:03 2014

acpitz-virtual-0
Adapter: Virtual device
temp1:        +77.0°C  (crit = +110.0°C)

QUESTION: is this a high temperature? What does this temperature mean?

Any other comments would be welcomed.

Thanks,

R.

---

### Post by deadflowr on 2014-08-16
Yes your temp is a little high.
I would peg a normal temp as half that, normally.

the temp1 most likely is the cpu temp, it is probably the best comment that the module used can give you.
When you configured sensors, it probed the system and loaded the best modules for it, or at least what it deemed to be the best modules for it.
The temp1 output is just how that particular module writes it.
If that makes sense...

---

### Post by Mike_Walsh on 2014-08-16
> **Sanctimonious_Ape said:**
> According to the [specs on Toshiba's site for your laptop]("http://support.toshiba.com/support/staticContentDetail?contentId=1250449&isFromTOCLink=false"), you only have a single core CPU so that's fine ([s]Toshiba apparently skimped on a zoned temp sensor[/s] [*ed: I was probably wrong about this, see next message*], but I don't know how useful that'd really be anyway - mine's consistently lower than the CPU temp by a handful of degrees).  What I find odd is the "Crit" temp is 10°C above [Intel's own specs for that CPU]("http://download.intel.com/design/mobile/datashts/30311008.pdf") (thermal stuff is at the end) which say the design max is 100°C and that the CPU will shut down (presumably just stop working entirely) at 125°C.

Kinda suprised even at those specs because 100°C is the boiling point of water and extremely hot - there must be some significant cooling going on in that laptop to make it usable on, well... a lap top. :rolleyes:   Mine is similarly spec'd to yours (slightly older, I think), but uses an AMD CPU and it usually tops out at 73°C CPU temp when going full bore.

Regardless, if you continue having heat-related shutdown issues, maybe your laptop's heat sink isn't making as good a connection as it used to (due to being tossed around, maybe) or perhaps the fan on the heat sink needs some attention.  There's plenty of info on the web about thermal paste, heat sinks, etc. or get a decent repair shop to check it for you.  I've even seen people who expanded their laptop's thermal dissipation using thermal pads and aluminum foil, but you've really gotta know what you're doing there or you'll likely short something out and cause bigger problems.

I find this kinda interesting, I must admit.

I'm running PSensor myself. I have an elderly Compaq Presario desktop PC (okay, LOTS more space inside to move air around, I know)... It's running a single core AMD Athlon 64 (to my mind, one of the very best of the older single-core CPUs). 

Now, curiously I have not one, but three temp readouts. And that's in addition to the hard drive readout, and the CPU load; there's one other, as well, but I can't check it at the moment, as I'm writing this in Mint 17. (I currently have half-a-dozen different distros on here, and PSensor is installed in Ubuntu 14.04, and Zorin's Core OS 9...)

If the CPU gets much above 40C, I start getting worried; that indicates some serious work is going on, coupled with CPU load usually in excess of 95% for a while.Normally, she runs somewhere in the region of 28-30C; probably sounds ridiculously low to some of you!

I've always run temp monitoring software of some kind, ever since I had XP on an old Dell Inspiron 1100 laptop....that thing used to regularly pull temps of 80C+, and it used to FRIGHTEN me..!

When the Compaq was running XP, up till May this year, I ran HWMonitor. The temps used to tally consistently with the temps that I experience now, so I'm guessing it may not be the OS that may not detect the true temp, but it might  be down to the piece of individual software that you decide to use. I tried many temp monitor programs under Windows, and found by experimentation that HWMonitor was the most accurate out of all of them.


Regards, 

Mike.

---

### Post by AbleTassie on 2014-08-18
Thanks deadflowr,

I took apart the PC, cleaned out the fan, lubricated the fan, removed and put new thermal paste between the cooling fin and CPU, GPU,etc. It is running cooler and quieter now, temp1 is about 51-58 now.

R.

---

### Post by JDorfler on 2014-08-19
Seems you got it down, but seems a bit high.  What is your Processor and are you overclocking?  I'm just curious.

Nevermind.  Googled it and seems your temp is normal for that config.  Interesting.

---

### Post by Sanctimonious_Ape on 2014-08-19
> **Mike_Walsh said:**
> Now, curiously I have not one, but three temp readouts.
Might  be the GPU (graphics chip - particularly if the video's integrated on  the motherboard), the  "[Northbridge]("http://en.wikipedia.org/wiki/Northbridge_(computing)"),  and/or the  [Southbridge]("http://en.wikipedia.org/wiki/Southbridge_(computing)")  chips.  Without specifics regarding your rig, it's impossible for me to  research (and I'm sure you could research it yourself if you cared  enough to).

> **Mike_Walsh said:**
> If the CPU gets much above 40C, I start  getting worried; that indicates some serious work is going on, coupled  with CPU load usually in excess of 95% for a while.Normally, she runs  somewhere in the region of 28-30C; probably sounds ridiculously low to  some of you!
My laptop is already in the mid-30s by the time it boots up and I  log in (Psensor starts automatically).  Unfortunately, I don't know  what temps it ran at when it was new.  I looked up my processor and couldn't find a  nice detailed spec sheet like the Intel one.  I found info stating max temps anywhere from 69°C (AMD's own site, but a *very* generic page that didn't seem specific to my processor - plus that exact number had been listed elsewhere as a *desktop case* max temp, not mobile CPU) on up to 90°C.  

This made me think my laptop running up into the low 70s might be dangerously close to overheating as well, so I went ahead and took the case apart (what a PITA on a laptop) and made liberal use of a can of compressed air.  I didn't lubricate the fan or do anything else and already my max temp dropped by over 10°C.  I tested this by running two YouTube playlists (sound muted) in two tabs simultaneously (YT always sucks up the processor time on my laptop) for over an hour, never exceeded 62°C and took significantly longer to ramp up to the top temperature.  After that I let it idle for ten minutes and it leveled out at 40°C, whereas before idle was usually in the high 40s range.

***NOTE:** I am NOT responsible for anything that happens should you attempt to follow the suggestions I give below.  Continuing to read this post constitutes your acceptance of these terms.  Just covering my...*

This experience suggests to me that if you have **any** uncertainty about how warm your CPU is running, then you should go ahead and clean your machine.  Pick up a can of compressed air from your local office supply store for between $5-10.  If you're not up for taking apart your laptop, you can still improve things a bit.  Unplug everything from your laptop and remove its battery so it doesn't turn on even by accident.  Be sure to **keep the can upright** while spraying to minimize any chemical liquids that might come out (this is usually stated on the can itself -- you should *most definitely* read the instructions on the can thoroughly before beginning this procedure).

Blow the compressed air **in short bursts** through any and all vents near the one where the hot air is blown out (as well as that vent itself) - usually it's near a corner, so you'll want to do vents on both sides that make up the corner (as well as possibly underneath).  Watch for where the dust comes out to get an idea whether you're getting all the vents involved.  **Rotate** through the various **vents repeatedly** and get the *entire length* of the vent, not just from one spot.  Shoot the air from different directions (again while still keeping the can upright) at the vent.  If you can see the fan itself through any of the vents, try to make sure you've cleaned it off as best you can.  When it doesn't appear you're getting much more dust out, then let the laptop sit for a while (preferably overnight) before reattaching anything so the chemical liquids that might have escaped the compressed air can and gotten into the machine have a chance to evaporate before power can be applied and potentially short-circuit something.  Might even be good to prop your laptop up on an angle while letting it "dry" so the liquid that might have gotten in there runs out the vents.

To be honest, I kept my can upright and didn't wait very long before reconnecting things.  However, if you want to try to ensure that you have no problems then you should certainly take as many precautions -- such as those described above -- as you can.  Whatever you do, though - don't let your laptop overheat and potentially cause a fire (although most CPUs have a built-in cutoff to prevent this as the original poster described, you should assume the worst possibility of that mechanism potentially failing for whatever reason).

Good luck, all.  I'm glad I read this thread and thought to look at my own PC for similar issues.

---

### Post by Sanctimonious_Ape on 2014-08-19
Yeah, I'm thinking higher temps are the norm for larger process dies - mine's 90nm and runs in a similar range.  As processor dies were shrunk (can't believe how small they've gotten - 14nm for the new Broadwell chips!!), they probably needed to reduce the heat generated to keep them reliable.  Or maybe the reduced temperatures are a byproduct of lower power requirements.  Or both.  What do I know about processor design?  :rolleyes:

---

### Post by dave131 on 2014-08-19
I just tried psensor myself, and I have a temp1 at the top as well.  When psensor started (I ran it from a terminal) it gave an error about unable to retrieve nvidia information (it's an Intel GPU), so I can only assume as well that temp1 must be the GPU (I currently have no disks - just running off a SD card until a disk gets here Wednesday), so that's pretty much all that's left (Dell laptop).

As a side note/question/hopefully provide useful information for others reading/will read this thread:

What are the "normal" temps for things like CPU's?  This laptop has Intel Core 2 Duo and it's showing both cpu's in the upper 40's (in Celsius), with a max in the very low 50's.  

What are the "normal" ranges on things like hard disks, SSD's, etc.?

Thanks

---

### Post by dave131 on 2014-08-19
Isn't the same as another thread you have on this?  I didn't think we were supposed to open more than 1 thread for the same problem.  You may want to ask if they can be merged somehow so you (and others) don't have to watch 2 seperate threads for the same thing.

---

### Post by Sanctimonious_Ape on 2014-08-19
Yeah, I'm thinking OP wanted more than just the input I was giving in the other thread and tried to be somewhat subtle about it.  Was curious how that would go so I didn't poke my nose into this one until OP's issue appeared to be resolved.

---

### Post by Sanctimonious_Ape on 2014-08-19
I think "normal" really depends upon the design.  That's why I go searching for the original manufacturer's specs on the specific model of whatever device I'm dealing with.  Unfortunately, it seems AMD's got the documentation for older devices on a server that isn't functioning right now (or they've screwed up the web address for reaching it), so I'm SOL and just making educated guesses based upon as many other sources of relevant info I can find.  Even found an in-depth review of my exact processor that was several pages long, but still didn't mention this particular info.  **sigh**

You might start [here](http://www.intel.com/support/processors/sb/CS-030615.htm) for your processor info.

---

### Post by mastablasta on 2014-08-19
> **dave131 said:**
> 
What are the "normal" temps for things like CPU's?  This laptop has Intel Core 2 Duo and it's showing both cpu's in the upper 40's (in Celsius), with a max in the very low 50's.  

What are the "normal" ranges on things like hard disks, SSD's, etc.?



depends on the model. the one in raspberry pi for example can run quite high and does not need a cooler.for example: [http://www.mobileappsystems.com/blog/raspberry-pi-overclocking-overvolting#test](http://www.mobileappsystems.com/blog/raspberry-pi-overclocking-overvolting#test)

btw I just struggled with older dualcore Celeron and in the end after cleaning and reapplying the paste I got 40-50C (much better than 70-90C and then shutdown...). I have single core Athlon that runs at 35C. now these Athlons they can be overclocked quite a bit. in which case they would run hotter and would need extra cooling. but I never did it or felt the need. 

you also have motherboard "CPU" and the temp from that is also usually measured. 

disks also depend. I had a WD black that was working for over 10 years with no issues. and the temp keep showing it to be quite hot (I think it was around 46 C). anyway when it broke down it was the controller it seems (or rather one of capacitors inside)  not the disk. I can actually still use that disk just not for OS as it couldn't boot from it well anymore.

my point it get you model number and all that and then check the specs online. some CPU run cooler than others. I know some older Athlons were running quite hot as well as some Pentiums. between 30 and 60 C would be something of a normal temp range for desktop CPU. not sure about mobile, since they have less space to move the air around.

---

### Post by Mike_Walsh on 2014-08-19
@sanctimonious ape; Yep, I have to agree with you about disassembling laptops! It's a nightmare (or can be if you're not meticulous about noting where every little bit came from, and keeping them in some sort of order. I normally lay everything out on a sheet of cardboard)...

In a way I suppose I'm lucky, in that my laptop is a very elderly Dell Inspiron of approx 2002 vintage; it's a 'brick' by modern standards (compared to something like a current Macbook Air, say), largely due to the sheer size of the battery pack.....but it has significantly more space to play with, and therefore it's easier to clean out.

My current 'rig' is a 2004-vintage HP/Compaq Presario SR1619UK desktop PC. 

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00519847&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=1147955](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00519847&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=1147955) 

It uses an MSI motherboard that MSI won't even admit to having made, since I believe their policy on manufacturing under license was that the licensee should assume responsibility for the product, once it was received! I did manage to find an owner's handbook for it, however:-

[http://www.elhvb.com/mboards/oem/hp/manual/amethystM_manual.pdf](http://www.elhvb.com/mboards/oem/hp/manual/amethystM_manual.pdf)

Now, with it being a tower, and having large amounts of space, and several fans, you would think "How could it possibly overheat?" It was inherited from my sister about 7 months ago. She had it from new, and was getting rid of it, since, like most non-technical people, she was worried about OS end-of-life (it used to run Win XP).

My bro-in-law is a DIY fanatic, and sis has spent the larger part of her marriage living in what amounts at times to a building site! I always clean anything electronic, if it's second-hand, and that was what I did with the Presario. I took the CPU fan off to have a look at the cooler, and was glad I had.....the heatsink was clogged solid with brick dust, and fluff, and other assorted crap. Sis only ever used to buy and sell stuff on Amazon, and play 'The Sims' on it, so it had a very easy life with her, and is consequently in 'good nick' for it's age..!

Cleaning it out lowered the CPU temp (Temp1 on Psensor) from high 40's to high 20's/low 30's.....and I 'spring-clean' it every 3 months, too. However, I'm led to believe that AMD's temp sensors don't report as accurately as Intel's , so it may not be running as cool as I think it is..!

   ==============================================================================

@dave131; If you have a look here, this site will tell you all you ever wanted to know about your CPU; just enter the relevant bits of info in the right places, or be patient and spend a few minutes browsing through it..... 

[http://www.cpu-world.com](http://www.cpu-world.com)

CPU temps (as I understand it) can range wildly, anywhere from my own relatively low temps (low to mid 30's normally, though in the depths of winter I HAVE seen it start as low as 17c!), up to high 70's/low 80's even, depending on location and usage. Laptops have very convoluted, narrow airways, and consequently run quite warm (modern netbooks and stuff are better in this respect, since they run on considerably lower voltages.....and it's higher voltages that produce that heat).

Towers, on the other hand, have far more space and usually lots more fans and bigger heatsinks to dissipate the heat generated.

I'm not an expert by any means; most manufacturers seem to quote 60c as being a maximum for hard drives, (though some, like Seagate, tend to quote lower) although general rule of thumb is that anything over 50c for prolonged periods does NOT do a hard drive much good.

SSD's, I haven't had anything to do with, so can't really help you there, but this post may help:-

[http://www.mmo-champion.com/threads/1312336-High-SSD-Temp](http://www.mmo-champion.com/threads/1312336-High-SSD-Temp), as may this:-

[http://www.buildcomputers.net/hdd-temperature.html](http://www.buildcomputers.net/hdd-temperature.html)

Hope that helps.

Regards,

Mike.

---

### Post by dave131 on 2014-08-19
Thanks for the replies on what the normals are.  I know it helps me and believe it will help anyone else who reads this thread now or in the future.

---

### Post by AbleTassie on 2014-08-21
Dave,  I'm not sure how to ask to merge the two threads.  In my mind they are related, but kind of different. It would be fine with me to merge them.    R.

---

### Post by AbleTassie on 2014-08-21
All,             I looked around on the web and I think temp1 may be the temperature at the base of the CPU die and acpitz-virtual-0 stands for acpi temperature zone virtual device 0 or something similar. I think people may be correct that the temp1s I am getting are normal for this laptop.    It definitely seems to be running cooler since I took it apart, oiled the fan, cleaned out the dust and added new thermal paste to the heat sink. I've been watching my temp1. With the CPU in "idle" temp1 varies between about 51C and 55C.  When temp1 gets up to about 54 or 55C, the fan comes on briefly for about 108 seconds. Then temp1 drops down to 51C, the fan shuts off for about 24 seconds, the temp slowly goes up to 54 or 55 C and the cycle repeats. It does this in both Windows XP and in Ubuntu.    Using Speedfan 4.49 in Windows XP, when I first turn on the PC, temp1 is about 40C and rated OK. After some time temp1 slowly starts to rise. Temp1s of 41C to 49C are rated with a red arrow pointing upward. Temp1s 50 up to 55 are rated with a little red flame beside it. Since this Speedfan rates these temps high with a flame, I am somewhat concerned. Perhaps temp1 is still too high.  Regarding the meaning of temp1, temp1 seems to be associated with "sys/class/thermal/thermal_zone0" in the app “Temperature Monitor” in Ubuntu and in Ubuntu in the app “lm-sensors” I get this output:    acpitz-virtual-0  Adapter: Virtual device  temp1:        +51.0°C  (crit = +110.0°C)     Any more comments will be welcomed, but I am probably OK now.    Thanks Dave, Ape, DeadFlwr, and J              R.

---

### Post by tgalati4 on 2014-08-22
You can research what your processor maximum temperature is rated to.  Most are rated to 110C so if you were running 77C and the BIOS has a safety shutdown temperature at 90C then you could hit that quickly.  55C is high for most processors, but an older, 90 nm process, 90-watt Total Dissipated Power (TDP) processor it is probably normal.  I had an audio server running Xeon's at 75C and it only lasted 3 years (24/7), so higher temperatures mean shorter life.  The replacement server runs at 64C--obvious design changes.  The closer you run to the maximum rated temperature, the shorter the expected life of the processor.  Normally the motherboard fails (delaminates) under the CPU at higher temperatures and fails before the CPU.

Since most laptops are designed for 3-4 years, you have gotten double the life expectancy.  By cleaning and reseating, you can go another 8 years!

---

### Post by JKyleOKC on 2014-08-22
> **RMcGinnis said:**
> Dave,  I'm not sure how to ask to merge the two threads.  In my mind they are related, but kind of different. It would be fine with me to merge them.    R.In the lower left of each message I see a "Report post" button. You can press that and send a message to the forum moderators; in that message you can ask them to merge the two threads.

I'm participating in a couple of other threads dealing with this same sensor since on one of my machines it seems to be frozen at 40 degrees C no matter what the CPU is doing, and was told that for AMD chips the sensor module never reports accurately so it's advisable to add or subtract an offset to get closer to the actual temperature. It's quite possible that your Windows program and lm-sensors are doing this and using different offsets! Personally, I'd trust speedfan more than lm-sensors, if dual-booting, since it seems to be much better maintained... However I wouldn't run Windows just to be able to use speedfan!

---

### Post by AbleTassie on 2014-08-22
Thanks tgalati4,  The specs for my CPU are at [http://ark.intel.com/products/27146/Intel-Celeron-M-Processor-380-1M-Cache-1_60-GHz-400-MHz-FSB](http://ark.intel.com/products/27146/Intel-Celeron-M-Processor-380-1M-Cache-1_60-GHz-400-MHz-FSB). Max TDP is 21 Watts and lithography is 90 nm. So maybe it is OK, but the Max TDP is significantly higher than 90 Watts.  Interestingly, there is a review of thermal pastes at this link [http://skinneelabs.com/2011-thermal-paste-review-comparison/2/](http://skinneelabs.com/2011-thermal-paste-review-comparison/2/)  .  The paste I used, Arctic Silver Ceramique2, is not that highly rated, so it might be worth trying to lower the temps with another kind of paste. I suppose modifying the heatsink in some truly knowledgeable way might be an option too.  I've raised the bottom of the laptop up on bottle caps, that may be helping some too. Any other comments from you tgalati4 or anybody else would be welcomed.   Thanks,  R.

---

### Post by AbleTassie on 2014-08-22
> **JKyleOKC said:**
> In the lower left of each message I see a "Report post" button. You can press that and send a message to the forum moderators; in that message you can ask them to merge the two threads.

Thanks Jim, I'll do that.
> **JKyleOKC said:**
>  I'm participating in a couple of other threads dealing with this same sensor since on one of my machines it seems to be frozen at 40 degrees C no matter what the CPU is doing, and was told that for AMD chips the sensor module never reports accurately so it's advisable to add or subtract an offset to get closer to the actual temperature. It's quite possible that your Windows program and lm-sensors are doing this and using different offsets! Personally, I'd trust speedfan more than lm-sensors, if dual-booting, since it seems to be much better maintained... However I wouldn't run Windows just to be able to use speedfan!

I am really getting the same temp1s in Windows XP (and Speedfan) as I am in Lubuntu (with lm-sensors), so this appears to be driven by hardware, not software. 

Thanks,

R.

---

### Post by Mike_Walsh on 2014-08-22
Interesting.

I'm running an AMD Athlon 64 3200+. It's a 10-yr old design, on a 90 nm process. According to a search I did:-

[https://www.google.co.uk/#q=Normal+operating+temperature+of+AMD+Athlon+64+3200%2B+CPU](https://www.google.co.uk/#q=Normal+operating+temperature+of+AMD+Athlon+64+3200%2B+CPU) ,

a lot of people have reported, over the years, 'normal' temps ranging anywhere from  low 30's to mid 70's. I would guess this is probably about right. Mine's installed in a Compaq Presario desktop PC (lots of room for moving cool air around, it's true); at the height of summer, it averages around 38-45C under load. Springtime & autumn, around 28-30C. In the depths of winter, even with the central heating on, it rarely gets above 25C, and often starts out showing just 17-18C; and this is with the bog-standard OEM cooler and fan.  Perhaps mine's just a good one, I don't know.....but on the rare occasions it gets anywhere near 45-50C in summer, I start getting concerned!

As of this moment, PSensor is currently reporting an average of 22-24C (I'm writing this in Zorin right now, but it's installed in this OS, too) ; that's cool for the time of year, but we're in the middle of a cold spell over here in the UK.

According to CPU World, the Athlons were rated for a maximum range of around 50-65C:-

[http://www.cpu-world.com/CPUs/K8/AMD-Athlon%2064%203200%2B%20-%20ADA3200DAA4BW%20(ADA3200BWBOX).html](http://www.cpu-world.com/CPUs/K8/AMD-Athlon%2064%203200%2B%20-%20ADA3200DAA4BW%20(ADA3200BWBOX).html)

Bearing in mind it IS an older design, with a larger process size, and utilising rather higher voltages than are normal nowadays, you WOULD expect it to produce more heat. Tgalati is, I think, correct in this assumption, but mine has always seemed to run well below the oft-quoted averages. I'm certainly not complaining..! 

Perhaps the fact that I carry out a regular 3-monthly 'spring-clean' (all fans removed, including CPU fan...cleaned, re-lubricated, and replaced; heat-sink, PSU & vents all blown out with short bursts of compressed air, and everything else brushed out with a very old, very soft, sable-hair artist's paint brush) has helped to prolong the machine's operating lifespan.

In my experience, the older Pentiums always seemed to produce more heat (average 10-15C higher) than the Athlon, which was more or less their direct competitor in the market at the time.

Pre- May 2014 (Win XP), I always ran HWMonitor. Post- this date (when I switched to Linux), I now run lm-sensors, hddtemp, and PSensor. The temps have always been consistent, regardless of the OS I've been using.

Regards,

Mike.

******************************************************

@JCKyleOKC: Agree with you about the AMD sensor not reporting accurately. I've been told this by many people, and have read the same in many other forum posts and blogs. It's quite possible that my old girl's not running as cool as I think she is! BTW, saw your reply to kc1di the other day. My late uncle, too, was a radio ham, until he passed away about 10 years ago; it was an interest he'd had since returning from Burma as a released POW at the end of WW2. He always predicted that the the rise of the internet would spell the end for amateur radio operators, and to a large extent I think he was right... It was from him that I learnt a lot of what I currently know about electronics. 

We have relatives over there in Midwest City. Mike.

---

### Post by tgalati4 on 2014-08-23
90 watts TDP are for desktop and server processors of that vintage.  My thinkpad T43p Centrino runs about 21 watts under load and it is rated at ~25 watts TDP.  Understand that many laptops have the GPU and CPU share the same heatsink with a copper bridge.  The GPU's tend to run 10C higher than the CPU's so your actual reported temperature depends on the workload--watching video will heat up the entire heatsink so the CPU can't throw as much heat off.

For extra ventilation I use an aluminum tray called an iLap designed for a mac.  I also use large rubber feet that I get from audio amplifier kits.  They raise the laptop off the table to allow more air to circulate.

Cleaning and maintenance is always a good idea.  I have a collection of pastes including Artic Silver.  Anything is better than 10-year-old crud.  I have reseated laptops, desktops and servers and I have always noticed at least a 10C drop with new paste and an oiled fan.  It's not rocket science.  Air cleaning alone will get you 1 to 3C.  Undervolting will get you 5 to 7C on a Thinkpad and a 20% increase in battery life.  From 21 to 17 watts under load and less fan use overall.

Many laptops have a really crappy heat sink design and will get super hot underneath and cause CPU shutdowns regardless of measures taken.  For these, you need a towel and an icepack and only use them for 1/2 hour at a time.

---

### Post by dave131 on 2014-08-23
Have you tried one of those laptop trays with the built in fans that sits under you laptop and plugs in to a USB port?  I have one for my laptop and it does help some - not a lot, but some.  I guess just moving that air around helps.  If you haven't already, and you are looking at doing something like reseating in a laptop, you might as well be sue the heatsink is good and clean - particularly if it has any fins.  Also check the case fans - sometimes they get dirty and don't want to spin as good as they should.  As with any computer, the cleaner the better, the more air space, the fans working correctly, the properly sized heat sink, the proper heat sink compound, etc., etc., etc., the better for temperatures.

---

### Post by sandyd on 2014-08-23
Merged as per OP's request.

---

### Post by AbleTassie on 2014-09-04
Just to let everybody know what happened, I am marking this as SOLVED, see follow-up story below.

I tore it apart and cleaned out the fan; resources on how I did it are  below. I used irisvista instructions disassembly ( [http://www.irisvista.com/tech/laptops/ToshibaL25/satellite_L25_laptop_overclocking_1.htm](http://www.irisvista.com/tech/laptops/ToshibaL25/satellite_L25_laptop_overclocking_1.htm) ) and printed out large color  pictures at a local library. I also used a tacklebox for screws, etc. as  described in the DIY Tech video. I got less dust out than I thought I  would, but I did get a fairly big wad of dust out of the fan. I also  lubricated the fan with sewing machine oil ([http://www.techrepublic.com/article/quiet-noisy-computer-fans-with-a-drop-of-oil/)]("http://www.techrepublic.com/article/quiet-noisy-computer-fans-with-a-drop-of-oil/%29")  and replaced the thermal paste; I used Arctic Silver Ceramique2 and the  pea method. FYI here is a link that gives thermal paste ratings: 
[http://skinneelabs.com/2011-thermal-paste-review-comparison/2/](http://skinneelabs.com/2011-thermal-paste-review-comparison/2/)

It is running cooler and quieter now, Temp1 is running between 50 and 55C.

I get this output when using the "lm-sensors" utility in Ubuntu:  acpitz-virtual-0    Adapter: Virtual device   temp1:     +51.0°C  (crit =  +110.0°C). In Windows XP while using "Speedfan" utility I only get two parameters, temp1 (which is the same as in lm-sensors) and HD1. 

As nearly as I can tell this temp, temp1 is fine, is much lower than the T junction max ( [http://ark.intel.com/products/27146/Intel-Celeron-M-Processor-380-1M-Cache-1_60-GHz-400-MHz-FSB](http://ark.intel.com/products/27146/Intel-Celeron-M-Processor-380-1M-Cache-1_60-GHz-400-MHz-FSB) ),  and probably is close to the temp at the base of the CPU. 


**Some links to Youtube videos I watched that helped are below (links are above the underlined video titles/topics) .**

[http://www.youtube.com/watch?v=jlO5crblG64](http://www.youtube.com/watch?v=jlO5crblG64)

_**How to Toshiba Satelite Laptop Disassemble Guide & Fan Cleaning**_
_**DIY Tech**_
_**DIY Tech**_

[http://www.youtube.com/watch?v=qOOhiIefBdk](http://www.youtube.com/watch?v=qOOhiIefBdk)

_**Toshiba laptop overheating fix** _

[https://www.youtube.com/watch?v=I9mtY-8DkKk](https://www.youtube.com/watch?v=I9mtY-8DkKk)

_**Toshiba Satellite - cleaning cooler and replacing thermal paste** _

[https://www.youtube.com/watch?v=-hNgFNH7zhQ](https://www.youtube.com/watch?v=-hNgFNH7zhQ)

[https://www.youtube.com/watch?v=8rn0BqMyXBM](https://www.youtube.com/watch?v=8rn0BqMyXBM)

_**How To Apply Thermal Paste** _

[https://www.youtube.com/watch?v=I3gx6c62D7I](https://www.youtube.com/watch?v=I3gx6c62D7I)

_**How to Remove and Apply Thermal Compound [Updated Tutorial]** _

[https://www.youtube.com/watch?v=FwmaszoRyHM](https://www.youtube.com/watch?v=FwmaszoRyHM)

_**"Toshiba Satellite Overheating Solution"**_
 
Thanks to everybody,

R.

---

### Post by mastablasta on 2014-09-05
> **RMcGinnis said:**
> 
It is running cooler and quieter now, Temp1 is running between 50 and 55C.

if that is on idle it is still very high. however if it really doesn't increase much beyond that, then it's fine.

my bor couldn't get the temp down no matter what (eventhough that cooler and all worked well for a couple of years before). so he invested into proper heat sink and got a really nice temp on idle. but the question is if in this case it is worth investing into such old stuff....

---

### Post by AbleTassie on 2014-09-05
> **mastablasta said:**
> if that is on idle it is still very high. however if it really doesn't increase much beyond that, then it's fine.

my bor [bro?] couldn't get the temp down no matter what (eventhough that cooler and all worked well for a couple of years before). so he invested into proper heat sink and got a really nice temp on idle. but the question is if in this case it is worth investing into such old stuff....

Temp1 in lm-sensors is running between 50 & 55 C when I cruise the internet, burn a CD or write Libre Office docs. So I don't think it gets over 57 C much. It might be worth trying a better rated thermal paste in a few months. Aric Silver Ceramique2 is not that highly rated, see skinneelabs.com/2011-thermal-paste-review-comparison/2/ 

Thanks,

R.

---

