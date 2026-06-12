---
title: "2 year old cpu/mobo - worthwhile to upgrade hardware alongside Ubuntu upgrade?"
date: 2014-01-04
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2014-01-04
I have been running 10.04 on my Intel Core i3-2120 3.30GHz CPU with 16GB RAM on a MSI H67A-G43 (MS-7750) mobo. I am finally upgrading to 12.04 and wonder if it is worthwhile to move to newer hardware. With 16GB of RAM, I can keep lots of windows open (preferred work habit), each with multiple tabs, and this is still a fast system.

Nonetheless, I have to restart every week or so, depending on what I am doing as the System Monitor/Resources/ Memory and Swap History shows % memory used gradually rises to over 90% during the course of sustained use. Unsure what causes this as the processes tab does not show substantial CPU use (jumps around between 4 and 40% depending on what might be happening, and is usually under 20%).

Is this likely a result of 10.04's inability to manage memory efficiently and it gradually becomes congested with not fully closed processes which are no longer active/in use and/or open processes?

Or is it some sort of hardware issue which a newer computer, probably a four core CPU, might resolve?

Any guidance appreciated, including ideas on how to determine what might be causing the current memory use issue?

---

### Post by mörgæs on 2014-01-04
You have strong hardware and there's no need to consider buying more. A fresh install of 13.10 is worth trying.

---

### Post by Impavidus on 2014-01-04
Running **top** in a terminal can tell you which processes are using most memory. Start top, hit > to sort according to memory use. Hit q to close again.

---

### Post by ajgreeny on 2014-01-04
I think you may misunderstand the manner in which Linux manages memory, which is best explained by the "if it's empty it is being wasted" comment.

Memory is filled by the system when opening applications, but it does not empty it straight away when the application is closed, but keeps useful libs etc etc in cache within the ram.  Note how much quicker a slow opening application will open the second time you open it for exactly that reason; it did not have to search for and open the libraries it needs as they are already open and immediately usable.

The **free -m** command will show you a lot of info about memory use but the important part is the **-/+ buffers/cache:        847       6836** line which in my case shows that 847MB is used but the top line shows over 2GB used.

---

### Post by jdeca57 on 2014-01-04
> **Odyssey1942 said:**
> With 16GB of RAM, I can keep lots of windows open (preferred work habit), each with multiple tabs, and this is still a fast system.

Let's rephrase that question: you're happy with your system, but maybe the upgrade to 12.04 might slow it down. 
Yes, that's a possibility, but not very probable.
But why don't you try it out? There is nothing lost if you find it to slow after an upgrade, you can always buy better hardware afterwards. And with that amount of RAM I doubt you'll see a big difference unless there would be an issue with graphics, like drivers or so.
Of course, if you really want to buy a quad-core... don't try to rationalize it. ;-)

---

### Post by Odyssey1942 on 2014-01-04
top: (turns out this is pretty tricky to capture, but finally manage to grab the top bit)

> Swap: 15624184k total,   367240k used, 15256944k free,   929476k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                  
 4952 robert    20   0 3640m 1.0g  73m S    8  6.6 915:07.76 chrome                                                   
 1778 robert    20   0  279m  54m  12m S    6  0.3 817:35.39 gnome-system-mo                                          
 2378 robert    20   0 1378m 458m  42m S    4  2.9 331:18.82 chrome                                                   
10892 robert    20   0 1872m 933m  39m S    4  5.8 697:09.61 1835 robert    20   0 1353m 306m  45m S   57  1.9   2:51.53 chrome             
 2238 robert    20   0 3669m 883m  31m S   49  5.5   0:59.54 chrome             
 2707 robert    20   0  946m  88m  23m S   21  0.6   0:03.22 chrome             
 2072 robert    25   5  915m  60m  21m S   19  0.4   0:01.03 chrome             
 2758 robert    20   0  904m  58m  20m R   19  0.4   0:00.81 chrome             
 1296 root      20   0  279m 120m  10m S    8  0.8   0:33.27 Xorg               
 1880 robert    20   0 1151m 226m  15m S    8  1.4   1:18.31 chrome             
 1978 robert    20   0  936m 104m  22m S    5  0.7   0:01.79 chrome             
 1578 robert     9 -11  464m 6972 5176 S    4  0.0   0:10.48 pulseaudio         
 3331 robert    20   0  914m  59m  22m S    3  0.4   0:02.53 chrome             
 3953 robert    20   0  947m  90m  20m S    3  0.6   0:02.40 chrome  chrome                                                   
 1183 root      20   0  465m 270m  18m S    2  1.7 831:22.57 Xorg                                                     
 2682 robert    20   0 1034m 146m  28m S    2  0.9  75:34.76 chrome                                                   
 2421 robert    20   0 1791m 832m  15m S    2  5.2 106:16.85 chrome                                                   
 4238 robert    20   0 1020m 122m  30m S    2  0.8  26:16.35 chrome                                                   
 2924 robert    20   0 1176m 314m  27m S    1  2.0  72:46.97 chrome                                                   
 3871 robert    20   0 1124m 230m  28m S    1  1.4  43:41.04 chrome                                                   
 3928 robert    20   0  934m  64m  22m S    1  0.4  74:02.57 chrome 

> free -m
             total       used       free     shared    buffers     cached
Mem:         15986      15446        540          0        140        922
-/+ buffers/cache:      14383       1603
Swap:        15257        358      14899


Now going to restart and run these again.

top:

> top - 13:59:06 up 8 min,  2 users,  load average: 5.36, 4.39, 2.14
Tasks: 306 total,   6 running, 300 sleeping,   0 stopped,   0 zombie
Cpu(s): 40.7%us,  4.8%sy,  7.9%ni, 37.3%id,  8.6%wa,  0.1%hi,  0.6%si,  0.0%st
Mem:  16370348k total,  7261440k used,  9108908k free,    79300k buffers
Swap: 15624184k total,        0k used, 15624184k free,   953724k cached

 1835 robert    20   0 1353m 306m  45m S   57  1.9   2:51.53 chrome             
 2238 robert    20   0 3669m 883m  31m S   49  5.5   0:59.54 chrome             
 2707 robert    20   0  946m  88m  23m S   21  0.6   0:03.22 chrome             
 2072 robert    25   5  915m  60m  21m S   19  0.4   0:01.03 chrome             
 2758 robert    20   0  904m  58m  20m R   19  0.4   0:00.81 chrome             
 1296 root      20   0  279m 120m  10m S    8  0.8   0:33.27 Xorg               
 1880 robert    20   0 1151m 226m  15m S    8  1.4   1:18.31 chrome             
 1978 robert    20   0  936m 104m  22m S    5  0.7   0:01.79 chrome             
 1578 robert     9 -11  464m 6972 5176 S    4  0.0   0:10.48 pulseaudio         
 3331 robert    20   0  914m  59m  22m S    3  0.4   0:02.53 chrome             
 3953 robert    20   0  947m  90m  20m S    3  0.6   0:02.40 chrome 

> free -m
             total       used       free     shared    buffers     cached
Mem:         15986       7912       8074          0         80        968
-/+ buffers/cache:       6864       9122
Swap:        15257          0      15257

This info does not mean a lot to me. And as I review this, I see that I did not get the very top bit in the first "top" capture. Is this critical? Any insights appreciated.

---

### Post by grahammechanical on 2014-01-04
If you want to buy new hardware, then just buy it.

If you had installed Ubuntu 12.04 back in May 2012 you would have found that hardware specification more than adequate. I had no problems running Ubuntu 12.04 with hardware dating back to 2007. I am still using the same machine. Intel Core 2 Duo 2.4GHz + 1GB Ram + Nvidia GT220. and I am running Ubuntu Trusty Tahr (14.04 under development). Memory usage has improved and will get better as more of the work done on the Ubuntu phone platform comes into the Ubuntu desktop platform. There has been a massive improvement to the speed of the Unity Dash. Work is also being done to identify which system services can be stopped once they are not needed and then re-started if they are needed again.

My advice would be to install Ubuntu 13.10 and then upgrade to Ubuntu 14.04. I cannot explain it better than this person has in his blog

[http://nhaines.livejournal.com/67141.html](http://nhaines.livejournal.com/67141.html)

[http://www.jonobacon.org/2013/10/18/reflections-on-ubuntu-13-10/](http://www.jonobacon.org/2013/10/18/reflections-on-ubuntu-13-10/)

I hope to never see the day when Ubuntu needs to copy the Microsoft approach to OS development. Want the latest version of the OS?. Then go out and buy the most up to date and powerful hardware there is and you will have a good user experience.

Regards.

---

### Post by Odyssey1942 on 2014-01-04
Thanks for all the good input, especially:

> But why don't you try it out? There is nothing lost if you find it to slow after an upgrade, you can always buy better hardware afterwards. And with that amount of RAM I doubt you'll see a big difference unless there would be an issue with graphics, like drivers or so.

Of course, if you really want to buy a quad-core... don't try to rationalize it.

My Microsoft "conditioning" must be showing. Of course it is always nice to have a new (and always faster) computer, but I will try jdeca57's suggestion and see how I get on.

However, if anyone sees anything in the CLI captures above and has any further thoughts about the issue, I remain interested.

---

### Post by sandyd on 2014-01-04
Chrome seems to be eating a bunch of memory

Otherwise, you still have 1603MB memory left

---

### Post by flyfisherbryan on 2014-01-04
Being new to this I am not sure if i should comment, but here I go.  The amount of memory used for cache went _up_ slightly after you restarted, but overall memory usage was cut in half.  Is it coincidence that the number of processes (is this a correct term for Linux?) being run is half what it was.  So it seems there is a correlation between leaving too many things open (esp. chrome) and your memory usage.

---

### Post by Odyssey1942 on 2014-01-04
Anyone who fly fishes should be listened to. Full stop.

I am certain that the massive number of windows and tabs within are a critical factor, but there is also another or other factors. I have my browsers set to open where I was when they close. So when I restart, I return to where I left off, but the System Monitor shows the total memory use to be about 35-50%, depending on what and how many I had open, then gradually creeps up to as much as the mid-90's % of memory in use, and of course the room begins to tilt.

It's what causes the % to rise over several days that I am ignorant about and hope that one of you wise and learned souls will enlighten me. (BTW, I hope that someone hasn't already explained it and it went right over my head!)

---

### Post by Impavidus on 2014-01-05
Chrome is your problem.

I don't use Chrome myself, but I think that to become faster it caches everything in RAM, eating memory until you close it. If used long enough, Chrome can fill memory of any size. Maybe there is a setting somewhere where you can limit the amount of cache it uses in RAM (and on disk). If properly designed, there must be such a setting. It's the kind of design choice that is a feature but sometimes works like a memory leak.

(As a sidenote, I recently found that grep has a similar feature. When searching a list of 20000 unique words for 10000 unique words, it consumed all my 3GB of memory in about 15 seconds. It appeared I had to tell it explicitly to use simple string matching instead of regular expression matching, which made the whole operation a lot faster too.)

---

### Post by flyfisherbryan on 2014-01-05
The thing is, if you look at the numbers posted, cache actually went up slightly after total memory usage went down by half.  I do not know how Chrome acheives its speed but it does seem to be a likely suspect in your problem.  Perhaps a week using a different browser?  (Says the FireFox aficionado.)

---

### Post by Odyssey1942 on 2014-01-05
Thanks Impavidus and Bryan,

Will use FF exclusively for a few days as a test. 

BTW, no comment requested unless incorrect, but I suspect that Chromium would equate to Chrome. I use both.

---

### Post by flyfisherbryan on 2014-01-05
Please be sure to keep us informed.  I am trying to learn from eveyone's experiences.

---

### Post by novarcr on 2014-01-05
Lol, I had a home built combo last 8 years with XP. Single core 3.0 Ghz, 3.5 G memory, AGP graphics interface. My Gigabyte MB finally crapped out on me. Finding a used MB that was the same cost me almost what the board cost new 8 or 9 years ago. I was able to get the same version with RAID though which I wasn't able to afford when it was new.  

I finally bit the bullet and upgraded all the hardware. What you have doesn't seem that bad though. On my system comparing the resources used by Win 7 or Linux KDE, they seem relatively close. 

My system now is maybe a year or so old and it runs pretty well in Win 7 with Aero. I think my Win 7 performance score is 7.1. But I prefer Linux now that I have been getting more accustomed to it. 

Gigabyte H77M-D3H M\B, i5-2320, 16 gb corsair, Zotac GT 640 2G DDR5, Corsair 650 Watt P\S.       I want to get a i7-3770, but I'm waiting for the prices to come down. My M\B should work with the 3770- ivy bridge.

---

### Post by novarcr on 2014-01-05
I kind of went off on a tangent, but I would lean towards the CPU. 

More cores equals more multi-tasking. More concurrent tasks with more cores.

I have 16 Gb RAM and I'm never really using more than 4 Gb.

---

### Post by whitesmith on 2014-01-05
> **grahammechanical said:**
> I hope to never see the day when Ubuntu needs to copy the Microsoft approach to OS development. Want the latest version of the OS?. Then go out and buy the most up to date and powerful hardware there is and you will have a good user experience. In a single statement you have perfectly captured the philosophy(?!), attitude and business plan of the gnomes of Redmond. A hat tip to you, sir.

---

