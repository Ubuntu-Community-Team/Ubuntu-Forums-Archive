---
title: "Not a Ubuntu Specific Question, more a general Computer Queston"
date: 2011-09-30
forum: New to Ubuntu
---

### Post by DavidG24 on 2011-09-30
hey guys,

my computer has been randomly freezing over the pass couple of weeks and after a tonne of testing I have finally isolated that it is CPU that is broken.

My current setup is:

1 x Intel Core i7 930 Processor LGA1366 2.8GHz 8MB Cache CPU		
2 x Asus DRW-24B1LT 24x DVDRW SATA LightScribe	
2 x Western Digital 1TB SATA3 64M(WD1002FAEX)	
1 x CoolerMaster GX750W PSU 80+	
1 x Asus Rampage III Extreme MB, Socket 1366, X58	
2 x Gigabyte N98TSL-1GI 9800GT 1G GDDR3 HDMI
3 x Kingston 4G(2x2G) DDR3 1600MHz CL9 HyperX
1 x Pioneer BDR-205BK 12X Blu-Ray Writer Drive SATA Black OEM


I'm hoping to have the CPU replaced but am not sure if the following will 'fit' with the other components so to speak:


Intel Core i7 960 Processor LGA1366 3.2GHz 8MB Cache CPU 

If anyone could let me know, I'd be very appreciative.

Cheers,

David

---

### Post by Zill on 2011-09-30
> **DavidG24 said:**
> ...my computer has been randomly freezing over the pass couple of weeks and after a **** tonne of testing I have finally isolated that it is CPU that is ******...
While I do not understand why you are so certain your problem is in the CPU, you can quickly check CPU compatibility against the motherboard specs. i.e.

[http://www.asus.com/Motherboards/Intel_Socket_1366/Rampage_III_Extreme/#CPUS]("http://www.asus.com/Motherboards/Intel_Socket_1366/Rampage_III_Extreme/#CPUS")

From this webpage, it does appear that the Core i7 960 Processor is suitable (since BIOS 0402).

---

### Post by seawolf167 on 2011-09-30
[LIST]
[*]How did you isolate a "broken CPU"?
[*]Does it freeze for all OS's or just Ubuntu/Windows?
[*]Does it freeze doing anything in particular?
[*]Does it freeze at any particular times?
[*]Did you run Ramtest (from the Grub2 boot menu) to check for bad ram? (for 7+ hours)
[*]If you have Windows on your computer did you run Prime95 for 24+ hours to see if it is stable?
[/LIST]

---

### Post by Denver Dave on 2011-09-30
I had a similar "freeze" problem with my old PC which I ended up replacing.  My suspicion is that it overheated and some component would go bad, but can't say for sure.  Taking the side cover off the PC helped somewhat, but not enough.

Does you PC freeze under both Windows and Ubuntu?  Does it freeze if you boot into Windows safe mode?

---

### Post by DavidG24 on 2011-09-30
Hi Guys,

From the responses, it seems I may have misdiagnosed my computer.

To start off, I did running Windows 7 on my PC for about a week when I first got the computer (~8 months ago) but have been running Ubuntu solid from there - have changed from 10.04 -> 10.10 -> 11.04  -> 10.10  (all x64).

I have no idea what was causing my computer to freeze, every now and then it would just go from 0-10% CPU usage to 99% out of no-where. I wouldn't be doing anything dramatic, just watching a movie whilst chatting on fb, diaspora, etc. 
Now before I go into how I 'solved' the problem, let me preface this by saying that I have limited comp knowledge and just applied (what I hoped was basic common sense).

(1) Firstly I hoped it would just be the version of Ubuntu - maybe I installed something that was causing it, so I re-installed making sure to fully reformat the drive before I did so.

The problem came back.
I then thought it may be hardware, so bit by bit I tried testing everything out

(2) starting with my two DVD drives and blue ray drive, I took one out at a time - ran the comp and the problem continued

(3) I have two GPU's, so I took one out, ran, still had problem, swapped with other GPU, still had problem - took both out and used old GPU - still had problem

(4) My next guess was the CPU, now I didn't know how to test it specifically, but I thought if I ran something directly off it (or as close to) that may isolate it; so I tested out CPU intensive apps; it was when I was running DeVeDe (which isn't overly CPU intensive admittedly)that I started to have problems, the computer would freeze and when I would force a restart, it would come up with the error message 'CPU - Over Temperature Error'

I tested this a couple of times and had the same issue. Hence why I thought it could be the CPU.

That said, I agree it could be the Ram or the Motherboard, but thought I would have a look around at CPUs whilst I find out how to test them. I notice that some of the contributors to this thread have outlined programs to use, could I ask for detailed instructions, given my noob status?

Thanks to all for contributing,

Cheers,

David

---

### Post by DavidG24 on 2011-09-30
> **seawolf167 said:**
> [LIST]
[*]How did you isolate a "broken CPU"?

Using a very shitty method, outlined above

[*]Does it freeze for all OS's or just Ubuntu/Windows?

Am only running Ubuntu, and haven't tested for Windows

[*]Does it freeze doing anything in particular?

Generally when watching media and playing flash games, but it is 
very random.

[*]Does it freeze at any particular times?

More at night, but I rarely use my personal PC during the day (@ uni using their's)

[*]Did you run Ramtest (from the Grub2 boot menu) to check for bad ram? (for 7+ hours)

No, could I ask you to tell me how to do it?

[*]If you have Windows on your computer did you run Prime95 for 24+ hours to see if it is stable?

as before..

[/LIST]

Thanks for your input, 

Much Appreciated,

David

---

### Post by -kg- on 2011-10-01
I can find little fault with your troubleshooting techniques, except for the RAM.

While you can run RAMTest (from the GRUB menu) for 7+ hours, you can also test it another way.  Unplug 1 of the RAM Modules and run the computer and see if the problem pops up again.  If it does, then plug that back in and unplug the other one.  If unplugging one of them solves the problem, then you know what to do.  If neither of them do, then it's on to the processor/MB.

When troubleshooting, you really want to eliminate the easiest/cheapest things to fix it, and work your way up.  It would be hell to buy that processor, only to find a $30 RAM module would have done the trick.

Now, if it is the processor/MB...you might want to just replace them both.  It's usually a lot less expensive to buy a processor/MB combo package than it is to buy each separately, which is what you'll be doing if you buy the processor only to find out it was the MB all along.

If you're an experimenter like me, though, that may not make any difference to you.  I built my current desktop from the ground up and it's still running almost 7 years later. :mrgreen:

---

### Post by anewguy on 2011-10-01
If your cpu is going over temperature, be sure of the following:

- there is PLENTY of air space both around the CPU and above the fan

- there is PLENTY of air flow INTO the area (cooler air) and out of the area (warmer air)

- is the CPU fan working?  Use a utility and check its speed

- do you have any extra case fans?

- are any of the fans blocked by cables, etc.?

- *IF* you have the skills to do so, remove the heatsink/fan from the cpu, clean both, and put new heatsink compound between the cpu and heatsink and reassemble them

- DO test your memory and possibly put heat spreaders on them


And ..... +1 if you replace your CPU you should go ahead and replace the motherboard.  There can be issues on the motherboard that could also cause your CPU to overheat.


Dave ;)

---

### Post by LowSky on 2011-10-01
if its a temperature issue, just remove the heat sink and check the thermal paste. Use an after-market product like Arctic Silver 5 before you remont the heat sink, then check the fan if it is spinning. Check the BIOS to see if you accidentally set the threshold too high.

My guess is your power supply isn't enough to power 3 optical drives, 2 hard drives, and two graphics cards. You should be using a 850 or better by my math, A 950 or 1KW would be a safe assumption. Those older Nvidia cards ran on a lot of juice.

---

### Post by michaelb28 on 2011-10-01
I assume you've checked your heatsink & fan. It shouldn't be clogged with dust and if you have ever removed the heatsink, thermal paste will need to be cleaned off the cpu and reapplied.

---

### Post by egalvan on 2011-10-01
> **LowSky said:**
> if its a temperature issue, just remove the heat sink and **check the thermal paste**.
 Use an after-market product like Arctic Silver 5 before you remont the heat sink, then check the fan if it is spinning.
 Check the BIOS to see if you accidentally set the threshold too high.


> **michaelb28 said:**
> I assume you've** checked your heatsink & fan.**
It shouldn't be clogged with dust and ..., **thermal paste will need to be cleaned off the cpu and reapplied.**


A  VERY common cause of over-heating.
I've lost count of how many CPU "replacements" were averted by **CLEANING FAN, HEAT-SINK AND REPLACING THERMAL PASTE.**

---

### Post by Zill on 2011-10-01
> **DavidG24 said:**
> ...That said, I agree it could be the Ram or the Motherboard, but thought I would have a look around at CPUs whilst I find out how to test them. I notice that some of the contributors to this thread have outlined programs to use, could I ask for detailed instructions, given my noob status?...
You may find the Ubuntu Community Documentation on [FaultyHardware]("https://help.ubuntu.com/community/FaultyHardware") of interest as this covers various areas that *could* be causing your problems.

The documentation entitled [MemoryTest]("https://help.ubuntu.com/community/MemoryTest") details how to check RAM.

However, as others have suggested, I suggest you first ensure that all your fans are running correctly and that there are no obstructions to airflow.

---

### Post by DavidG24 on 2011-10-02
hey guys,

Thanks for all your responses, I thought I would run a memtest, its been going for nearly 24 hrs, I took a photo of the output:
[IMG]http://img706.imageshack.us/img706/1525/img0554fa.jpg[/IMG]

Do I still need to keep it running, and if not, should the next step be to take out the CPU, clean, reapply gel and hope for the best! 

Thanks again everyone,

David

---

