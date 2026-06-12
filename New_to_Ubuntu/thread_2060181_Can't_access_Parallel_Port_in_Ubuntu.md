---
title: "Can't access Parallel Port in Ubuntu"
date: 2012-09-19
forum: New to Ubuntu
---

### Post by foberle on 2012-09-19
I recently installed Ubuntu 12.04 as a dual boot on a Windows machine. Among many issues I've encountered, one annoying one concerns the lack of support for the parallel port. I had earlier posted questions about this on another forum, but got NO responses whatever, so I thought I would try here.
 

 Here's the data about the card provided by the command “lspci -vv”:
 

 ```
[FONT=Courier New, monospace][SIZE=2]03:07.0 Communication controller: NetMos Technology PCI 1 port parallel adapter (rev 01) [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]    Subsystem: LSI Logic / Symbios Logic Device 0010 [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]    Interrupt: pin A routed to IRQ 3 [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]    Region 0: I/O ports at ce00 [/FONT] 
 [FONT=Courier New, monospace][SIZE=2]    Region 1: I/O ports at cd00 [/FONT] 
 [FONT=Courier New, monospace][SIZE=2]    Region 2: I/O ports at cc00 [/FONT] 
 [FONT=Courier New, monospace][SIZE=2]    Region 3: I/O ports at cb00 [/FONT] 
 [FONT=Courier New, monospace][SIZE=2]    Region 4: I/O ports at ca00 [/FONT] 
 [FONT=Courier New, monospace][SIZE=2]    Region 5: I/O ports at c900 [/FONT] 
 [FONT=Courier New, monospace][SIZE=2]    Kernel modules: parport_pc [/SIZE][/FONT] 
 
``` It seems obvious to me that Ubuntu recognizes that the card exists, which suggests that a) it didn't know how to set it up automatically during install, and b) that I should be able to get it to work through some incantation or other. There are many, many posts about using a parallel port in Linux/Ubuntu on the web, but none of the techniques seem to work for me (and the vintage and applicability of some of these postings isn't at all clear). Based on the most literate of the web postings I found (on this forum by the way), dated in January 2009 (by “Alex”), here's a recap of my most recent attempt to get the port working:
 

 I issued the following commands in sequence:
 

 ```

[FONT=Courier New, monospace][SIZE=2]sudo rmmod lp[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]sudo rmmod parport_pc[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]sudo /sbin/insmod /lib/modules/3.2.0-30-generic/kernel/drivers/parport/parport_pc.ko io=0xce00 irq=none[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]sudo /sbin/insmod /lib/modules/3.2.0-30-generic/kernel/drivers/char/lp.ko
[/SIZE][/FONT]

```
 After this, when attempting to add a generic printer (all I need), I can select “parallel:/dev/lp0” as the device URI (after a surprisingly long wait for the list to be populated – is that a clue?), but the “Print Test Page” button is greyed out, and nothing whatever happens when I attempt to print to it.
 

 Dropping down to the command line, the commands [echo “Hello” > /dev/lp0] and [echo Hello > /dev/parport0], even when prefixed with [sudo] both give “permission denied” messages.
 

 I checked permission levels on /dev/parport0 and /dev/lp0, and both have permissions set to “crw-rw----”, which seems to me in my current ignorant state to suggest that “permission denied” may be a red herring, since these are owned by lp. But my last exposure to Unix was back in the mid-1980s, so I'm prepared to be yelled at.
 

 Next I attempted to use the same sequence of commands above, but with the IRQ set to 3, as shown in the lspci output above. I had originally used the “irq=none” based on the referenced posting.
 

 Still the same results all around. I also attempted the sequence using different io addresses given in the lspci output; again, I started with the one for Region 3 as suggested in the referenced posting.
 

 I should mention, of course, that the parallel port works just fine under Windows, so I don't believe that's an issue.
 

 Does anyone have any insights to share?

---

### Post by howefield on 2012-09-21
Thread closed, duplicate here : [http://ubuntuforums.org/showthread.php?p=12248612#post12248612](http://ubuntuforums.org/showthread.php?p=12248612#post12248612)

---

