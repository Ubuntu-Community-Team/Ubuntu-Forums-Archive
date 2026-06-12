---
title: "Reported Menory(RAM) size?"
date: 2010-06-25
forum: Recurring Discussions
---

### Post by virsto on 2010-06-25
I am running a dual-boot system (Windows Vista, Ubuntu 10.04) which works quite well. However, I have noticed an inconsistency in the amount of memory (RAM) reported by the two different operating systems.

**In Windows Vista:**
 Memory (RAM): 4.00 GB

**In Ubuntu 10.04:**
 Memory: 3.00 GB

I have attached a screenshot *.jpg file that shows the hardware recognized by Ubuntu.

I would appreciate it greatly if someone could provide an explanation for this inconsistency.

Thank you, :)
--V

---

### Post by VH-BIL on 2010-06-25
I have this same issue. I was told by a technician that it was because 32bit can not detect more then 3gig but I don't think it is true, I think he was just being lazy and didn't look into it.

---

### Post by kalistona on 2010-06-25
ubuntu comes first (at start ), works in ram, and it comes after windows (dual-boot windows=1°part) why 3 and not 4 ? i suppose it is 3 free and 1 busy but i do not know why
exactly, sorry. (maybe windows keeps 1GO for crypted / security answer or for anti-virus ?)

---

### Post by Bachstelze on 2010-06-25
> **VH-BIL said:**
> I have this same issue. I was told by a technician that it was because 32bit can not detect more then 3gig but I don't think it is true, I think he was just being lazy and didn't look into it.

It is true.

---

### Post by VH-BIL on 2010-06-25
> **Bachstelze said:**
> It is true.

Good to know my techie is doing his job :p

---

### Post by kalistona on 2010-06-25
it is not ...where are coming from these false informations ...anyway it is not really important and serious...let's forget it.

---

### Post by VH-BIL on 2010-06-25
> **kalistona said:**
> it is not ...where are coming from these false informations ...anyway it is not really important and serious...let's forget it.

I have always wondered about this... Why have I bought so much ram if I can not use it etc...

---

### Post by chizzledfrmstone on 2010-06-25
As far as I know 32bit doesn't support more than 3.25gb ram.

How are you getting all of the 4gb to show in Windows? 64bit?

---

### Post by kalistona on 2010-06-25
well i do not want fight, it is only free discussion in respect each other, but i have followed the progress in ram/swap  since few years and i am sure that it can be.
the question was why so much ? absolutely usefull, that is opinions from users.
4go today is even not enough, every one asks more and more...so...we obtain more and more...

---

### Post by kelvin spratt on 2010-06-25
> **chizzledfrmstone said:**
> As far as I know 32bit doesn't support more than 3.25gb ram.

How are you getting all of the 4gb to show in Windows? 64bit?

Windows 7 32bit shows all your ram but only uses 3.25gb 
Ubuntu 32bit only shows what is usable 3.25gb unless you enable The PAE Kernel then you will get all your ram. But I think it is better to use 64bit my self.

---

### Post by VH-BIL on 2010-06-25
System Monitor shows 3gig for me but "sudo lshw" shows all the ram is installed.

---

### Post by philinux on 2010-06-25
> **VH-BIL said:**
> System Monitor shows 3gig for me but "sudo lshw" shows all the ram is installed.

Ubuntu 32 bit is showing you how much ram it can physically use. lshw is showing installed ram.

Answer is to run 64 bit OS, 32 bit pae kernel or live with it.

---

### Post by virsto on 2010-06-25
I am running a 32-bit Windows Vista OS and a 32-bit Ubuntu OS.

2^30 bytes = 1,073,741,824 bytes = 1 GB. Then it should be clear that 2^32 = 4x2^30 = 4 GB. Thus, IMHO a 32-bit OS should have access to 4.00 GB of RAM. ;)

--V

---

### Post by VH-BIL on 2010-06-25
Both my Windows XP and Linux don't show 4gig. I do not use Vista or Win7 so I don't know what is going on there.

Check this out:
[*_Ubuntu 4GB Ram Limitation and Solution_*]("http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/")

---

### Post by virsto on 2010-06-25
I am running a 32-bit Windows Vista and a 32-bit Ubuntu 10.04.

2^30 bytes = 1,073,741,824 bytes = 1 GB. 
It should be clear that 2^32 = 4 x 2^30 = 4 GB. Thus, IMHO, a 32-bit OS should have access to 4 GB Memory(RAM).;)

A good explanation on why **Windows Vista reports 4.00 GB** 
and **Ubuntu 10.04 reports 3 GB** would be appreciated.

--V

---

### Post by philinux on 2010-06-25
> **virsto said:**
> I am running a 32-bit Windows Vista and a 32-bit Ubuntu 10.04.

2^30 bytes = 1,073,741,824 bytes = 1 GB. 
It should be clear that 2^32 = 4 x 2^30 = 4 GB. Thus, IMHO, a 32-bit OS should have access to 4 GB Memory(RAM).;)

A good explanation on why **Windows Vista reports 4.00 GB** 
and **Ubuntu 10.04 reports 3 GB** would be appreciated.

--V

[http://support.microsoft.com/kb/946003](http://support.microsoft.com/kb/946003)

4 gig is the limit for a 32 bit os but some of that gets reserved for graphics card memory etc etc.
See the pros ans cons
[http://en.wikipedia.org/wiki/64-bit#32-_vs_64-bit](http://en.wikipedia.org/wiki/64-bit#32-_vs_64-bit)

---

### Post by burton247 on 2010-06-25
A 32 bit operating system can address 2^32 memory locations. Which is yes, 4GB. However you don't only have "RAM" (technicality read/write memory) you have separate memory for your graphics card and depending on whether you have mapped I/O or not you may have a bit for you I/O ect.

So a 32 bit operating system usually uses between 3 and 3.5 GB of "ram"

As other people have suggested, do you have a 64-bit version of vista?

> **VH-BIL said:**
> Good to know my techie is doing his job :p
Not a great one...

---

### Post by justleen on 2010-06-25
> **philinux said:**
> [http://support.microsoft.com/kb/946003](http://support.microsoft.com/kb/946003)

4 gig is the limit for a 32 bit os but some of that gets reserved for graphics card memory etc.

To add to that, lshw is reporting 4GB, for the same reason vista/7 report 4GB. They show the hardware installed, not the avail. mem.

---

### Post by philinux on 2010-06-25
Moved to Recurring Discussions.

---

### Post by virsto on 2010-06-25
Thanks to all that have tried to help..
I have executed the following (as suggested):

$ sudo lshw

I get a lot of information about the hardware; but, nowhere could I find that there was 4 GB of RAM. I do get many of the following:

*-memory:9 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: nVidia Corporation
             physical id: 1.2
             bus info: pci@0000:00:01.2
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:10 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: nVidia Corporation
             physical id: 1.3
             bus info: pci@0000:00:01.3
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:11 UNCLAIMED

etc.

--V

---

### Post by burton247 on 2010-06-25
width: 32 bits

Your bus is only 32 bits wide. So you can only address 4GB of ram

---

### Post by YeOK on 2010-06-27
> **burton247 said:**
> width: 32 bits

Your bus is only 32 bits wide. So you can only address 4GB of ram

The 32bit is reported from an unclaimed slot, they always show as 32bits. 

If you take a look at the section showing the installed memory, you should see it as 64bit.

Example: 

```

*-bank:3
             description: DIMM DDR2 800 MHz (1.2 ns)
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: DIMM_B2
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP78S [GeForce 8200] Memory Controller
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0

```


> **virsto said:**
> Thanks to all that have tried to help..
I have executed the following (as suggested):

$ sudo lshw

I get a lot of information about the hardware; but, nowhere could I find that there was 4 GB of RAM. I do get many of the following:

--- cut ---

--V

Can you post the whole report, you can attach as a text file.

---

### Post by soldier1st on 2010-07-13
i have a similar issue. i have 3GB ram but acording to the bios and Linux/Windows i can only use 2.5GB out of the 3GB but i have a 1GB video card but i am running 64bit but i cannot use the extra 512MB and i have PAE disabled in the bios and when i enabled it before i was still unable to use more ram even under a 64bit os but i do not want to enable bios remap as i am worried if linux will perform badly with PAE enabled and if i will have to recompile the kernel if linux will let me access all of it.

---

