---
title: "Ubuntu not recognizing full ram"
date: 2012-08-24
forum: New to Ubuntu
---

### Post by Dabo Ross on 2012-08-24
Hello, I installed Ubuntu on my old computer about a month ago and just realized that it is only recognizing 1.8 GB of my 4 GB of ram. I Wiped the drive prior to installed Ubuntu, so I can't check if windows would have recognized it now. My computer DID originally have only 2GB ram, but about a year ago I upgraded it to 4GB. I know that at one point at least, windows was recognizing all of that ram, so I know I installed the ram correctly.

The computer is a Dell inspiron 1501, about 3-4 years old. I was running windows 7, but That doesn't really matter because there is no trace of anything that existed before Ubuntu. 

I would like to go into boot settings, but another problem I have is that the back light for the computer built in screen is broken. I am using an external monitor, that works for while I am running the operating system, but it won't turn on during boot, so I can't tell what is happening then.

I would like to get Ubuntu recognizing full ram, as I am running a gaming server on it, and the more ram it can use, the more people the server can support.

I am running 64-bit Ubuntu 12.04 LTS.

Thanks if you can help!

---

### Post by SlugSlug on 2012-08-24
try re-seating the RAM

---

### Post by mcduck on 2012-08-24
How much of the RAM it *does* detect? And are you running 32- or 64-bit version of Ubuntu? You'll need to either use the 64-bit version or install the PAE kernel on 32-bit version to be able to use all 4GB of memory

---

### Post by SlugSlug on 2012-08-24
coffee time for duck ;)

---

### Post by sanderj on 2012-08-24
You can run the stuff below:

```
wget http://www.appelboor.com/dump/check-my-memory.py
python check-my-memory.py 
sudo python check-my-memory.py
```

It will report everything about your memory: hardware, BIOS, OS, etc, and will give advice.

---

### Post by mcduck on 2012-08-24
> **SlugSlug said:**
> coffee time for duck ;)

sure, I was still going through my morning cup of coffe when writing that,

Anyway, I'd still like to know how much of the RAM is actually detected. Just to know if it might be a case of some RAM module not being detected, or just the usual situation of the value of available RAM appearing a bit smaller than the total of installed memory caused by the fact that the kernel is loaded into RAM at boot and that part of RAM not counting as available (since it can't be freed or used for anything else, most programs don't include it into total amount of avaiable memory.)

edit: A quick google search for the computer's specs shows max RAM limit of 2GB. So it's a hardware/BIOS limitation. Check if Dell provides a BIOS update that increases the amount of suported memory, but if they don't you are out of luck.

---

### Post by NikTh on 2012-08-24
Hi  , 
I think a 
```
free -m
``` will clear up the situation. 
Thanks

---

### Post by spjackson on 2012-08-24
> **mcduck said:**
> edit: A quick google search for the computer's specs shows max RAM limit of 2GB. So it's a hardware/BIOS limitation. Check if Dell provides a BIOS update that increases the amount of suported memory, but if they don't you are out of luck.I'm not sure where that information comes from but I bought a Dell Inspiron 1501 with 4GB ram in 2007. Both Windows Vista and Ubuntu recognise 4GB ram.

@OP. It definitely sounds like a hardware fault. Try re-seating the RAM as has been suggested. If unsuccessful, remove the 2nd chip. If the computer still boots then the 2nd chip is probably faulty. If it doesn't boot, then the first chip is faulty. Also try the 2nd chip in the 1st slot to confirm your findings.

---

### Post by sanderj on 2012-08-24
@OP ... why not run my script ... It will tell you all details.

---

### Post by d4m1r on 2012-08-24
1) Run free -m in a terminal window and post the output here
2) How much RAM does Windows detect?
3) Run a memtest86+ test....2/4 hardware sticks (or however many slots you have) could have gone bad.

---

### Post by Dabo Ross on 2012-08-24
I am going to answer each question here.

SlugSlug -I will try re-seating the ram if nothing else works. 

mcduck -As I said in the first post, I am running 64 bit Ubuntu, and it detects 1.8 GB ram.

sanderj -Here are the results of that code:
```

newlanders@Newlanders:~/Server$ wget http://www.appelboor.com/dump/check-my-memory.py
--2012-08-24 14:28:08--  http://www.appelboor.com/dump/check-my-memory.py
Resolving www.appelboor.com (www.appelboor.com)... 176.31.156.230, 2001:41d0:2:bb58:dead:beef:8637:e45b
Connecting to www.appelboor.com (www.appelboor.com)|176.31.156.230|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8012 (7.8K) [text/plain]
Saving to: `check-my-memory.py'

100%[======================================================================>] 8,012       --.-K/s   in 0s      

2012-08-24 14:28:09 (75.6 MB/s) - `check-my-memory.py' saved [8012/8012]

newlanders@Newlanders:~/Server$ python check-my-memory.py 
check-my-memory.py - version: SJ 2012-06-03

Attention: please run as root with 'sudo'. This scripts uses command like 'dmidecode' which need root-rights.
Without root rights, you get less (or less correct) information.


ANALYSIS:
BIOS offers 1917 MB as usable
Memory seen by OS 1875 MB
CPU is PAE enabled
CPU is x86_64 64-bit enabled
OS is x86_64 64-bit

SUMMARY:
Attention: as you're not running this script as root, the summary below can contain strange numbers.
Memory difference between DIMM hardware and BIOS offering -1917 MB
Memory difference between BIOS offering and memory seen by OS 42 MB
Memory difference between DIMM hardware and memory seen by OS -1875 MB

Finished
newlanders@Newlanders:~/Server$ sudo python check-my-memory.py
[sudo] password for newlanders: 
check-my-memory.py - version: SJ 2012-06-03
OK, you're root
ANALYSIS:
Total of physical memory modules found 2048 MB in 2 memory module(s)
BIOS offers 1917 MB as usable
Memory seen by OS 1875 MB
BIOS version 08/23/2006
CPU is PAE enabled
CPU is x86_64 64-bit enabled
OS is x86_64 64-bit

SUMMARY:
Memory difference between DIMM hardware and BIOS offering 131 MB
Memory difference between BIOS offering and memory seen by OS 42 MB
Memory difference between DIMM hardware and memory seen by OS 173 MB

ADVICE:
Your physical memory is less than 3200 MB, and your system does not need special memory treatment

Finally: show more detailed memory info from lshw. This can take up to 30 seconds ...
       description: System Memory
       size: 2GiB
          description: DIMM DRAM Synchronous
          size: 1GiB
          description: DIMM DRAM Synchronous
          size: 1GiB
       description: BIOS
       size: 1023KiB
       capacity: 3520KiB

Finished

```

mcduck, A bios update? I am pretty sure that at one point, when I had windows 7 installed, it was recognizing 4 Gigs. 
I don't really understand anything else you said though...

nikth I ran that code and got this
```

             total       used       free     shared    buffers     cached
Mem:          1875       1712        163          0          9         75
-/+ buffers/cache:       1627        248
Swap:         1916        214       1702

```
spjackson - My computer did come with 2 GB ram. I will try re-seating it and the other things you suggested.

d4m1r - I no longer have windows installed, as I wiped the drive before installing Ubuntu. I believe it was detecting 4GBs, but I hadn't checked in a while when I did that. What would be the command for a memtest? I'm not really that experienced. 


I wasn't the one to upgrade the ram on my computer, but i believe I have the old ram somewhere. One of my relatives upgraded the ram as a surprise birthday present, so I'm not really sure how to re mount it. I will try all that though. Thank you. Any more tips post please!

---

### Post by sanderj on 2012-08-24
```
Finally: show more detailed memory info from lshw. This can take up to 30 seconds ...
       description: System Memory
       size: 2GiB
          description: DIMM DRAM Synchronous
          size: 1GiB
          description: DIMM DRAM Synchronous
          size: 1GiB
       description: BIOS
       size: 1023KiB
       capacity: 3520KiB

```

So that's only 2GB (plus a few MB's) memory in two DIMMs at the lowest hardware level you can imagine. 
Do you have more than 2 DIMMs? Or do you think you have more memory in the two DIMMs? See what happens when you *remove* one DIMM / just leave one DIMM.

---

### Post by Dabo Ross on 2012-08-24
I just checked my ram and saw that there are only 2 1GB sticks. I am like Wtf.

I have no idea what happened to the 2 2GB sticks, but they sure are not in my computer... 

Thanks for all this but I think the problem lies elsewhere.

So ya, I will try to find out what happened to those extra 2GB ram.

---

### Post by Terl on 2012-08-24
According to the specs for a Dell1501 found here: [https://support.dell.com/support/edocs/systems/ins1501/en/om_en/html/specs.htm]("https://support.dell.com/support/edocs/systems/ins1501/en/om_en/html/specs.htm") the max ram is 2 Gigs, the way I read the above is 2gigs are installed.

---

