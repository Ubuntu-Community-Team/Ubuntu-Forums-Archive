---
title: "TV tuner woes"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by doctorbighands on 2008-10-06
Hi there everyone,

All I want to do is watch cable TV on my computer. It's proving to be extraordinarily hard, and I can't understand why!

I don't know the make/model of my TV tuner card, except that it's an Angel something-or-other. Here is the relevant data according to "lshw"...
```

*-multimedia:0 UNCLAIMED
                description: Multimedia video controller
                product: Dual Tuner/MPEG Encoder
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 0b
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64

```

I've tried installing MythTV; what an amazing pain! It tells me something about "No UPnP Backends Found" each time I try to configure the frontend, and that's as far as I get. I've tried installing another TV program from the repos, but it tells me it can't find my tuner card!

Why is this so hard? What do I do to get it working? Oh, and please, I'm not interested in Mythbuntu, because I don't want to have to reinstall th OS *AGAIN*, and I don't like XFCE.

Help! :)

---

### Post by doctorbighands on 2008-10-06
...bump?

---

### Post by robalcorn on 2008-10-06
Don't know if it will help but have you tried tvtime?

---

### Post by seeker5528 on 2008-10-06
I'm not sure, but think:

> **doctorbighands said:**
> 
*-multimedia:0 UNCLAIMED]

: is and indication that no driver is loaded for the card. Not familiar with any NEC TV cards, google wasn't very helpful, or els my google fu wasn't up to snuff.

> I've tried installing MythTV; what an amazing pain! It tells me something about "No UPnP Backends Found" each time I try to configure the frontend, and that's as far as I get.

You have to configure the back end first, or have a previously configured backend on another machine that is available over the network.


> I've tried installing another TV program from the repos, but it tells me it can't find my tuner card!

Even if the driver is there and working correctly, many of the TV programs don't know what to do with encoded data, the expect something different that may not be provided by cards that do encoding, or if the hardware is capable, it may be something that is not implemented in the driver.

> Why is this so hard?

I blame the hardware people for not supporting their hardware in Linux either directly by having people on staff to do it, or indirectly by making the information available so support can be provided independently.  

>  What do I do to get it working?

I would suggest starting with the PCI ID, try the command line:

lspci -nn

: should be a line in the output with something about a multimedia controller and includes the PCI ID, something like [10b9:5247], that corresponds with the vendor and device and is in many cases more productive to use as a search on Google than a product name.

Later, Seeker

---

### Post by doctorbighands on 2008-10-07
Okay, so, I tried swapping the previous tuner card with another I had on hand. This one uses the Conexant cx23883 ("cx2388x") chip. MeTV reports that there's no card installed, and TVtime closes as soon as it's opened (I see the briefest flash of an open window, and it closes immediately).

I believe the new card is recognized by lshw and has a driver present (at least it doesn't read "UNCLAIMED" any longer).

What do I do now?

---

### Post by doctorbighands on 2008-10-08
...bump again?

---

### Post by indytim on 2008-10-08
First off, I can't offer any specific assistance to your situation.  If you haven't gone the route already, try:

1.  Search : TV Tuners
2  Do a post in the multimedia and hardware boards

Sorry I can't offer up a fix to your problems.

IndyTim

---

### Post by seeker5528 on 2008-10-18
I don't know much about these cards and the range of support they offer.

There is a wiki:

[http://www.linuxtv.org/v4lwiki/index.php/Cx88_devices_(cx2388x](http://www.linuxtv.org/v4lwiki/index.php/Cx88_devices_(cx2388x))

: which links to a list of known cards:

[http://linuxtv.org/hg/v4l-dvb?cmd=file;file=linux/Documentation/video4linux/CARDLIST.cx88;filenode=-1;style=raw](http://linuxtv.org/hg/v4l-dvb?cmd=file;file=linux/Documentation/video4linux/CARDLIST.cx88;filenode=-1;style=raw)

: If you have not got help elsewhere, the output of:

lspci -vn

: and :

dmesg

: relating to the card is needed and if you know it the company that made the card and name the card was sold under.

Later, Seeker

---

