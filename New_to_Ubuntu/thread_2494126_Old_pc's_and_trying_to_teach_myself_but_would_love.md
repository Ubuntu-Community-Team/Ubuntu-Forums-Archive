---
title: "Old pc's and trying to teach myself but would love some direction"
date: 2024-01-06
forum: New to Ubuntu
---

### Post by notentirlynewb on 2024-01-06
Ok so I would love to be on the lowest of levels with some of you..but unfortunately I'm a self-taught another man's trash desktop reviver..lmao..so I recently found linux..Ubuntu officially..have several older like early 2000's desktops..and just can't stand micro..so I tried several times to install through USB and may have changed how the drive was read.??..so I couldn't access it anymore..after lots of trial an more error I finally got it on a little newer but still old sata drive desktop and am curious as to if I can use it with a crossover cable to fix the other pc's cause I have been studying servers and would like to use them for this process..any help good or bad greatly appreciated..thanks love the linux group it's been a awesome experience as this far

---

### Post by wildmanne39 on 2024-01-06
Moved to New to Ubuntu, welcome to the forum.

---

### Post by notentirlynewb on 2024-01-06
Hope I haven't overlooked this in another post somewhere..I've tried multiple variations of phrasing but to no avail..so thought I'd try for some assistance..like I said even negative assistance may lead me to the path..but thanks again for any and all the help

---

### Post by wildmanne39 on 2024-01-06
You just need to be patient and give the forum members that can help you time to reply, our members are in different times zones all across the world so the one that can help may be a sleep.

---

### Post by notentirlynewb on 2024-01-06
Yes sir thanks..I just wanted to be clear that I hadn't just started here begging for help..I've honestly put some hours in lol..thanks again

---

### Post by Bashing-om on 2024-01-06
notentirlynewb; Hello

To fix an old PC my go-to tool is a liveDVD (desktop installer).
Boot the liveDVD >> try ubuntu mode  >> terminal:
see what state the hard drive(s) is in:
```

sudo fdisk -lu

```
as a place to start the looking.

[INDENT]welcome to the fray
[/INDENT]

---

### Post by notentirlynewb on 2024-01-06
Thanks for the reply..is this terminal command on the machine that works properly or on the one that doesn't boot due to my inexperience..i do have a crossover cable and thought I had found a way for that to work..kinda controlling the bad from the good but the more I read the more I'm unsure lol..thanks again and I love Ubuntu and the whole Linux group

I'm sorry I believe that I just now understood what you were saying..use the Ubuntu USB that I was previously using to install and work from terminal..is that right

---

### Post by Bashing-om on 2024-01-06
notentirlynewb;

> 
use the Ubuntu USB that I was previously using to install and work from terminal..is that right

If that installer is of a "desktop" variety (server installer does not have the "try ubuntu" option) - then yeah -
And if the old PC's support booting from a USB.

[INDENT]we have the tools
[/INDENT]

---

### Post by notentirlynewb on 2024-01-06
Ok seems like I remember some of this flashing back from all the bumps in the road from the brutal lessons I got from hardware that wouldn't give me any direction...thanks again and I'm about to pull one of the relics out and see if I can undo maybe just a little damage...thanks again so much

---

### Post by Bashing-om on 2024-01-06
notentirlynewb;

Help is what we do :D

When at that next bump - holler at us.

[INDENT]we make a path
[/INDENT]

---

### Post by notentirlynewb on 2024-01-06
Yes sir will do..trying to find all the cords had kinda figured I'd made them boat weights lol..but thanks so much..if I make it through this..might try to learn code or programming..I'm just guessing but it's something in the neighborhood of the DOS version on the old Tandy pcs..man I may have said that I'm old lol

Thought I'd throw it out there for a good laugh..got my first lab rat out it's got a big XP on it lol..waiting for the dial-up tones to stop as we speak

Definitely showing my age that was in form of question..dos..tandy

---

### Post by yancek on 2024-01-06
You would likely get more help if you posted some details on the hardware you are using.  Trying to install a current Ubuntu on a 20 year old machine is not likely to work.  Some Linux systems are designed more to work on older machines, AntiX or MX Linux for example.  The manufacturer and age of computer would be useful information and if it had originally some windows OS on it, which it was.  Windows XP was released over 20 years ago for example.

---

### Post by notentirlynewb on 2024-01-06
I'm away from them currently but seems like 2 dells that are pentium 4 2.8ghz and an hp with Aathon maybe 64bit..but yes sir I did some research and decided on the mate distro and it seems to run ok on a 20yr old Vista inspiron..but honestly don't know the first thing about the proper or correct way of doing all this..kinda was just seeing if I could and I guess in someway I have but screwed the pooch on a couple before I got there

---

### Post by TheFu on 2024-01-06
Vista isn't 20 yrs old.  Incorrect answers don't help. If you don't know, say that instead.

---

### Post by Morbius1 on 2024-01-06
Windows Vista isn't 20 years old but the Dell Inspiron it's running on might be.

---

### Post by oldfred on 2024-01-06
What are specs of systems?
If very old & 32 bit, Ubuntu does not support those systems anymore.

If 64 bit but lower spec, then a lightweight flavor may work.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)

Full Ubuntu is really for newer computers. 
I tried to install Ubuntu on a 2006 Intel 64 bit BIOS only system with 1.5GB of RAM. It would not install. Server installed. And I added lightweight gui.
I was a bit surprised I could install Kubuntu as it is more of a mid-weight flavor that I use on my newer systems. But it really only worked reasonable well with my external SSD with 22.04 Kubuntu. Old hard drive was very slow.

Also shows minimum hardware requirements, but better to have more than minimum.
[https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)

---

### Post by TheFu on 2024-01-06
> **Morbius1 said:**
> Windows Vista isn't 20 years old but the Dell Inspiron it's running on might be.

True.  I had a Dell laptop that came with MS-Vista. Fortunately, it was killed by a small drop and CC insurance replaced it. It was a Core2 Duo system.  The replacement was a Core i5-2550. The performance difference was amazing between Win7 and Vista.  I still have the Dell Win7/Core i5 laptop, though it hasn't been booted in a few years. It worked the last time I needed it.

I don't know **anybody** who upgraded from MS-XP to MS-Vista. Everyone waited until MS-Win7.  If a system had Vista on it, it was delivered with Vista.  Remember, all the driver issues?  Vista broke nearly all peripherals that weren't bought at the same time.  Anything older never got updated drivers.  

Vista is what forced me to switch to Linux for my desktop. None of my peripherals worked and updated drivers weren't ever available.  It was like a parting of the Red Sea - before and after Vista.  BTW, I'm still using printers and scanners that never worked again under MS-Windows, but work great under Linux.

Of course, there are exceptions. There always are.

---

### Post by notentirlynewb on 2024-01-06
Thanks for all the replies...and I've said from beginning I don't know anything...but git some specs maybe everything you're looking for...first off the inspiron 531s I've been running mate on roughly a year..64 bit version..currently updated to mantic minotaur...it's got the AMD 64x2 dual core 4000+ x2 nv4c graphics and 675gb drive with only 1.7gb ram 

Next is a dell 8300 pentium 4 3 ghz with 1.25gb ram and  about 200gb drive..currently finishing up on the mate version 18.04.06 32bit

---

### Post by notentirlynewb on 2024-01-06
And it seems to be moving along better that the 531..just going by lag time from click to action..but what do I know lol

---

### Post by notentirlynewb on 2024-01-06
If yall don't mind..I installed the 8300 alongside the winxp..however I do have 2 drives and put os on one and mate on other..unfortunately mate is the slave drive so it boots xp less I catch f12..was just reading and seen several commands to run to address this..but I was thinking originally that I'd just open side panels and swap cables..will that be OK or do I need to work through terminal..thanks again

---

### Post by yancek on 2024-01-06
If you have Mate on a separate physical drive, you 'should' be able to permanently set that drive to first boot priority in the BIOS.  The F12 key is usually for a one time boot change but that all varies with manufacturer.

---

### Post by notentirlynewb on 2024-01-06
Yes sir..but for some reason it won't allow me to highlight the drives so that I can change them from slave to master..like I said I'm not experienced at all but have made several Frankenstein throughout the years and have previously been able to swap drives around like you had said...maybe it's the version of bios but I'd be guessing for sure..but seems from your response that I could possibly just swap the cables and that would be OK too?.. thanks again you guys have been awesome baby stepping me lol

---

### Post by notentirlynewb on 2024-01-06
Just one more question..which of the two would be better to actually use daily? Cause I'm torn the 8300 operation is awesome maybe even better than when it was new..but seems like the 531s has better cpu and such but takes 5mins to load web browser and can't have multiple apps running or it freezes to a hard shutdown..just curious as to your expert advice thanks so much

---

### Post by oldfred on 2024-01-06
I think I mentioned before, I was able to use external SSD on my 2006 laptop that was originally XP (Vista Ready). But it only had 1.5 GB of RAM and loading more than one large app like Firefox & smaller app like Zim that I use to keep notes in would then go to swap. With old slow HDD, I would get a minute or two of blank screen, or it was going to swap. With SSD, it was so quick it just seemed like a hiccup. But I still only tried to use one large app as RAM was too limited. 

My old Desktop also from 2006, was getting older in 2011. I planned a new system, but MicroCenter had an OEM 60GB SSD for less than $100, so I planned on using it in new system, but installed it in old  system. It make old system so much better, it was 2014 before I built new Desktop.

While I have used many flash drives, most are slow, a few a bit faster. But an external SSD it so much better an flexible as you can use it with different system. My UEFI SSD is a NVMe drive in a NVMe to USB3 adapter. I use it with my 2017 desktop sometimes, with my newish Laptop that has Windows 11 and with my old 2006 laptop (originally XP). 

Kubuntu is light enough to work with older systems, but fully functional for me for my newer  systems.

---

### Post by MAFoElffen on 2024-01-07
Your Dell Inspiron 531S has a old 64bit CPU. But at least is is 64bit. You say the system now has 1.75GB RAM... But is upgrable to 4GB RAM. I would concentrate on that as your first system. Maybe just salvage the drive from the other, and scrap the rest of it. Even then, I would probably go with something light, like Lubuntu.

The other system is only 32bit.

---

### Post by notentirlynewb on 2024-01-14
Thanks for all the help..I'm definitely doing some research

---

