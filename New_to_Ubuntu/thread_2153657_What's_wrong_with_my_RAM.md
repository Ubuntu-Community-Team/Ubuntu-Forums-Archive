---
title: "What's wrong with my RAM"
date: 2013-06-11
forum: New to Ubuntu
---

### Post by Annadin on 2013-06-11
So while scavenging through old computers for parts i found old RAM drives that are a lot bigger than mine and i could really use them. But when i plugged them in Ubuntu freaked out and and errors just started shooting up out of no where. In example, it wouldn't load the GUI after booting up if i let it run a check on /dev/sda1, I'm not able to run fsck, and it won't connect to the internet at all. I decided to snoop around in the /dev/shm folder but all i could find was a pulse audio thing. Is there a way to format RAM drives or get rid of the viruses I'm pretty sure that are in these things?

---

### Post by BBQdave on 2013-06-11
> **Annadin said:**
> So while scavenging through old computers for parts i found old RAM drives that are a lot bigger than mine...

Not sure if I am following you... but most likely the RAM - *memory* is not compatible with your hardware.

If you are working with scavenged hard drives, who knows the hardware fail involved with old abandoned parts - would not trust my data on abandoned, possibly damaged hard drives.

---

### Post by zemega on 2013-06-11
The RAM is probably damaged. In any case you should run a memory test first with that RAM.

---

### Post by deadflowr on 2013-06-11
Most likely, if RAM, just plain old bad RAM. Not much can be done about that, but to chuck it.
Anyway, if RAM, there wouldn't be any Viruses on it, as information on RAM disappears when the system shuts down.

If, however it's actually a hard drive situation, then it could be any number of things. From a dying hard drive to a misconfiguration of how the drive is used by the system.

---

### Post by squakie on 2013-06-12
If it's actually a old drive, it might even be one of the old ones that just plain isn't compatible with today's' hardware - things like old mfm drives, etc.  I'm also curious if this is really a ram drive - they do exist.

---

### Post by Mark Phelps on 2013-06-12
> **Annadin said:**
> So while scavenging through old computers for parts i found old RAM drives... 

Which are WHAT, exactly?  

There is RAM (which is memory) and there are drives.  A RAM Drive is a space in memory that is mapped to resemble a file system.  When the memory is removed, any "drive" that might have been previously mapped there disappears.

---

### Post by grahammechanical on 2013-06-12
You need to confirm that these memory modules are compatible with the motherboard and that they are fitted into the slots accurately and that they are compatible with any other memory modules that are fitted. You could try booting without the hard drive connected. You could allow the machine to run and display its Power On Startup Tests (POST). You could enter the BIOS and see if that shows anything wrong with these memory modules. You could run a memory check when the machine is first switched on.


If Ubuntu was working fine, and then you change the memory modules and now Ubuntu is broken, then the culprit is likely to be those memory modules.

---

### Post by zemega on 2013-06-12
Apparently RAM drive is not popular enough that people mistake it as RAM Disk. OP is talking about external drive, which is made out of RAM. He's not talking about standard RAM being inserted at the motherboard. Its an actual external collection of RAMS housed inside a special drive. Which has some usage a long time ago, where hard disk barely pass 5 MB. It can be internal as well, but I said external to clearly differentiate things.

It can't be posioned as you phrased it, because there's no data inside, its volatile, it cannot hold any data when there is no power supply. If you can rule out 1:there's no physical damage to the drive, 2: There's no chemical/electronic decomposition inside it, 3: You are giving it the actual power supply that is suitable for it, then the RAM Drive can be used.The main problem is that I think there's no driver support for your RAM harddisk. And your question just jumped from absolute beginner to pro level. You probably got to hunt for the drivers, rewrite it back in current programming language and recompile it for Ubuntu. Its not an easy task either. How do you even connect the drive? PATA?

In any case, OP need to clarify things up.

---

### Post by bab1 on 2013-06-12
> **zemega said:**
> Apparently RAM drive is not popular enough that people mistake it as RAM Disk. OP is talking about external drive, which is made out of RAM. He's not talking about standard RAM being inserted at the motherboard. Its an actual external collection of RAMS housed inside a special drive. Which has some usage a long time ago, where hard disk barely pass 5 MB. It can be internal as well, but I said external to clearly differentiate things.

It can't be posioned as you phrased it, because there's no data inside, its volatile, it cannot hold any data when there is no power supply. If you can rule out 1:there's no physical damage to the drive, 2: There's no chemical/electronic decomposition inside it, 3: You are giving it the actual power supply that is suitable for it, then the RAM Drive can be used.The main problem is that I think there's no driver support for your RAM harddisk. And your question just jumped from absolute beginner to pro level. You probably got to hunt for the drivers, rewrite it back in current programming language and recompile it for Ubuntu. Its not an easy task either. How do you even connect the drive? PATA?

In any case, OP need to clarify things up.

There are also physical drives called *RAM Drives *.  They are DVD-RAM Drives.  See [[COLOR="#FF8C00"]**here**[/COLOR]]("http://www.panasonic.com/industrial/optical-drives/dvd-ram-cartridge-drive/index.aspx").  So yes;  OP,  we need more information on what the drive really is.

---

### Post by squakie on 2013-06-13
Years ago there were actually a precursor to todays Solid State Drive's that was actually a called a ram disk.  I don't believe I heard of them outside of the mainframe and mini world.  They actually did preserve data across power cycles.  They used what we might today call "flash" memory and were very expensive in their day.  For me we're talking about the early 1980's.

---

### Post by uRock on 2013-06-13
I changed your thread title, as it appears to not have anything to do with the security breach implied by the old title.

I am not an expert on RAM, so I would have tossed the stick as soon as I noticed they didn't work.

---

### Post by squakie on 2013-06-14
With the price of everything these days, I would chuck it too and look for something a little more promising - either physical memory or if you are looking for a drive - I've had fairly good results with those types of things via Ebay.

---

