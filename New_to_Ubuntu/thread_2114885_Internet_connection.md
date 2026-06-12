---
title: "Internet connection"
date: 2013-02-11
forum: New to Ubuntu
---

### Post by BDogg718 on 2013-02-11
Im running ubuntu 12.04 with a wired connection, and yet my internet will drop off very often. Is there a bug or something that anyone knows about?

---

### Post by TheFu on 2013-02-11
> **BDogg718 said:**
> Im running ubuntu 12.04 with a wired connection, and yet my internet will drop off very often. Is there a bug or something that anyone knows about?

Do you have any more information that pinpoints the issue to be Ubuntu?
I would assume this is the root cause myself:
* ISP down?
* bad cable?
* router port failure 
* specific hardware issues?

Have you checked the system logs?
**sudo egrep -i 'error|warning' /var/log/*log**
will find issues in the logs.

There are issues with certain Intel cards failing due to SIP or other highly specialized traffic that is uncommon, but those cards become completely dead until a full power cycle. Reboot isn't enough. This is a hardware/firmware issue regardless of OS.

**lshw -C network** output might be helpful so you can search for specific issues.

---

### Post by BDogg718 on 2013-02-11
thanks for the reply. Everything as far as hardware is brand new. I ran the command you gave and didnt see any problems. Gonna try to dig a lil further. Thanks again.

---

### Post by Mopar1973Man on 2013-02-11
Wireless or wired?

If its dropping on wireless you might research the wireless driver for Linux. Like my brand new Toshiba laptop did work out of the box with Ubuntu but the signal would come and go. So finding out RealTek has Linux drivers and install the linux driver problem solved for me. So you might look up what hard you got and see if there is a updated driver for it.

---

### Post by TheFu on 2013-02-11
> **BDogg718 said:**
> thanks for the reply. Everything as far as hardware is brand new. I ran the command you gave and didnt see any problems. Gonna try to dig a lil further. Thanks again.

As you know, brand new HW still fails.  Try a different switch/router port and a different ethernet cable.

If the ethernet chip is well known, it is unlikely to be a driver issue, but a corrupt HDD or flaky RAM can appear as that.  Tonight, you might consider running memtest86 for 10+ hrs.  Could heat or power be an issue?  Did you overclock any parts?

There are too many possible causes to narrow anything down at this point.

---

