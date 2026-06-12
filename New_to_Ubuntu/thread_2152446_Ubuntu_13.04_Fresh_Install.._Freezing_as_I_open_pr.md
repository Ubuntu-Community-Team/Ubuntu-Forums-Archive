---
title: "Ubuntu 13.04 Fresh Install.. Freezing as I open programs"
date: 2013-06-07
forum: New to Ubuntu
---

### Post by waterbubblez on 2013-06-07
Hi everyone, I apologize for the 'repost' this seems to be a common issue amongst a few. However, throughout the research I've done I have yet to find a solution. I hope this is the right place to ask this question. Basically as the title says I just installed Ubuntu 13.04 on a new hard drive I bought earlier today and now when I try to open any programs it usually opens them and freezes that program, the only thing I can seem to consistenly use is the terminal through the use of ctrl+alt+t command and ctrl+alt+f1. Althought, occasionally these freeze as well.

Computer Specs:
1TB HD 7200RPM running a fresh install of 13.04 as the only operating system on the hard drive
4GB DDR3 RAM
Radeon HD 6970 series Graphics Card I beleive it has either 1GB or 2GB DDR3 RAM, I can't remember exactly as I am currently at work. 
As for the Processor I also cannot remeber as of right now, I'll edit this when I get off with more up to date information.

I apologize if this is the wrong section to post this in, and if it is could somebody please direct me to the right part of the forums.

Thanks

---

### Post by 2F4U on 2013-06-08
Did you update the system to the latest available patches? Since this probably won't work through GUI tools, I would suggest to try updating through the terminal.

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Which graphics driver are you using for the ATI card? Since every application is freezing there must be something fundamentally wrong, maybe even a bad installation. Did you verify the checksum of the downloaded Ubuntu iso? Did you look into the system log files if it contains error messages?

---

### Post by waterbubblez on 2013-06-08
Current video driver is:
```

lspci -v

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Cayman XT [Radeon HD 6970] (prog-if 00 [VGA controller])
    Subsystem: Hightech Information System Ltd. Device 2306
    Flags: bus master, fast devsel, latency 0, IRQ 85
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f7b20000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at e000 [size=256]
    Expansion ROM at f7b00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci

along with

sudo lshw -C display | grep driver
       configuration: driver=fglrx_pci latency=0
       configuration: driver=i915 latency=0

```
I did not check the checksum before I installed it. I'll try to get to my friends to check on his computer still running windows.

```



sudo apt-get update 
sudo apt-get dist-upgrade


```
After running those commands everything seems to be working much smoother so far. As for now I feel like this issue is resolved. I'm going to play around with it for a bit and I'll post back, as for now Thank you much for the help.

---

### Post by waterbubblez on 2013-06-08
Well thanks a lot for the help the issues I was having seems to be solved!

---

