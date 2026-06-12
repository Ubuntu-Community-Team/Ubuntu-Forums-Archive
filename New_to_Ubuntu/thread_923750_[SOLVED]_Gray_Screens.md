---
title: "[SOLVED] Gray Screens"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by mczonie on 2008-09-18
I'm noticing that my screen is going gray a lot. Since this is a brand new, clean reinstall, the only problem I can think of is that something is hogging lots of memory, but I can't imagine what. Any suggestions as to what I can do? TIA.

---

### Post by kk0sse54 on 2008-09-18
Can you please elaborate on exactly what's happening, as for checking your memory usage install and use Conky or go to System > Adminstration > System Monitor in order to check how much memory each program is using.

---

### Post by mczonie on 2008-09-18
> **C!oud said:**
> Can you please elaborate on exactly what's happening, as for checking your memory usage install and use Conky or go to System > Adminstration > System Monitor in order to check how much memory each program is using.

I just did that, but I'm totally computer illiterate and I have no idea what I'm seeing means. 


I also noticed that whenever I go to a webpage with lots of flash videos, my browser crashes.

---

### Post by Crafty Kisses on 2008-09-18
Just go into Terminal and type this:
```
top
```
Post the results here.

---

### Post by kk0sse54 on 2008-09-18
> **mczonie said:**
> I just did that, but I'm totally computer illiterate and I have no idea what I'm seeing means. 


I also noticed that whenever I go to a webpage with lots of flash videos, my browser crashes.

Both top and system monitor basically show you how much memory and cpu is taken up by a particular application

---

### Post by mczonie on 2008-09-18
> **Codename said:**
> Just go into Terminal and type this:
```
top
```
Post the results here.
```


top - 16:48:12 up 2 days, 21:32,  2 users,  load average: 1.83, 1.68, 1.57
Tasks: 107 total,   4 running, 103 sleeping,   0 stopped,   0 zombie
Cpu(s): 95.0%us,  5.0%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    384508k total,   375624k used,     8884k free,      780k buffers
Swap:  1116476k total,   430332k used,   686144k free,    39100k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
20712 mike      20   0  378m 4176 3912 R 52.6  1.1   1496:43 opera              
16774 mike      20   0  314m 150m  25m R 41.3 40.2  69:34.67 firefox            
 5111 root      20   0  276m  38m 4616 S  5.3 10.3 155:59.76 Xorg               
27901 mike      20   0 65832  19m  10m R  0.7  5.1   0:01.58 gnome-terminal     
 5705 mike      20   0 22732 4800 2568 S  0.3  1.2  10:41.04 compiz.real        
    1 root      20   0  2844  332  284 S  0.0  0.1   0:01.42 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.10 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:02.44 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   41 root      15  -5     0    0    0 S  0.0  0.0   0:01.30 kblockd/0          
   44 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   45 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  111 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
  147 root      15  -5     0    0    0 S  0.0  0.0   0:10.48 kswapd0 
```

---

### Post by Crafty Kisses on 2008-09-18
For some odd reason, 95% of your computers resources are being used:
```
Cpu(s): 95.0%us,  5.0%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
```

---

### Post by mczonie on 2008-09-18
> **Codename said:**
> For some odd reason, 95% of your computers resources are being used

Any idea what it could be?

---

### Post by Nitefang on 2008-09-18
> **Codename said:**
> For some odd reason, 95% of your computers resources are being used:
```
Cpu(s): 95.0%us,  5.0%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
```

Mine isn't using 95% but it is using about 50% for EACH of my 4 CPU's and a lot more memory than I expected. Is this normal for Ubuntu, I thought it was supposed to use less. is there something you need to set correctly.

  I also get gray screens an awful lot, mostly on web pages with videos on them, Firefox also crashes often.

  I reduced the visual affects to none and it did help but not much. I have a pretty fast graphics card and never had similar problems with Vista(not saying its better just saying its not the computer).

---

### Post by mczonie on 2008-09-18
> For some odd reason, 95% of your computers resources are being used

I've done several reinstalls on this CPU. Do you think it's possible that all the installs are there on my hard disk and taking up memory?

---

### Post by RequinB4 on 2008-09-18
Just a quick clarification diagnostic -

run:
```

killall opera
killall firefox

```

Then again run ```
top
```

---

### Post by mczonie on 2008-09-18
> **RequinB4 said:**
> Just a quick clarification diagnostic -

run:
```

killall opera
killall firefox

```

Then again run ```
top
```

OK, this is what I got after running that:

```
top - 19:35:59 up 3 days, 20 min,  2 users,  load average: 0.94, 1.56, 1.62
Tasks: 106 total,   2 running, 104 sleeping,   0 stopped,   0 zombie
Cpu(s):  6.3%us,  1.3%sy,  0.0%ni, 92.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    384508k total,   288048k used,    96460k free,     5100k buffers
Swap:  1116476k total,   414340k used,   702136k free,    75748k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5111 root      20   0  271m  33m 4064 S  4.7  8.9 164:32.23 Xorg               
30103 mike      20   0  2308 1104  852 R  0.7  0.3   0:00.06 top                
 5631 mike      20   0 15332 3208 2612 S  0.3  0.8   1:28.74 gnome-screensav    
 5634 mike      20   0 39452  11m 6732 S  0.3  3.1   1:26.32 gnome-panel        
 5705 mike      20   0 22732 4820 2588 S  0.3  1.3  11:05.40 compiz.real        
 5722 mike      20   0 25192 3176 2536 S  0.3  0.8   2:51.54 nm-applet          
    1 root      20   0  2844  336  284 S  0.0  0.1   0:01.42 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.16 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.12 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:02.58 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper         
```

---

### Post by RequinB4 on 2008-09-19
> **mczonie said:**
> OK, this is what I got after running that:

```
top - 19:35:59 up 3 days, 20 min,  2 users,  load average: 0.94, 1.56, 1.62
Tasks: 106 total,   2 running, 104 sleeping,   0 stopped,   0 zombie
Cpu(s):  6.3%us,  1.3%sy,  0.0%ni, 92.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    384508k total,   288048k used,    96460k free,     5100k buffers
Swap:  1116476k total,   414340k used,   702136k free,    75748k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5111 root      20   0  271m  33m 4064 S  4.7  8.9 164:32.23 Xorg               
30103 mike      20   0  2308 1104  852 R  0.7  0.3   0:00.06 top                
 5631 mike      20   0 15332 3208 2612 S  0.3  0.8   1:28.74 gnome-screensav    
 5634 mike      20   0 39452  11m 6732 S  0.3  3.1   1:26.32 gnome-panel        
 5705 mike      20   0 22732 4820 2588 S  0.3  1.3  11:05.40 compiz.real        
 5722 mike      20   0 25192 3176 2536 S  0.3  0.8   2:51.54 nm-applet          
    1 root      20   0  2844  336  284 S  0.0  0.1   0:01.42 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.16 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.12 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:02.58 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper         
```

Keep in mind this is all operating under the assumption that it's a RAM/processer problem (which it may not be, but I seem to be the only one still here):

So unless you have opera and firefox running all the time and it always uses that much of your cpu%, i'm doubting its lack of cycles in your processor.

As for RAM, run ```
top
``` again and then press ```
>
```

aka shift + .

and post the output

---

### Post by mczonie on 2008-09-19
> **RequinB4 said:**
> Keep in mind this is all operating under the assumption that it's a RAM/processer problem (which it may not be, but I seem to be the only one still here):

So unless you have opera and firefox running all the time and it always uses that much of your cpu%, i'm doubting its lack of cycles in your processor.

As for RAM, run ```
top
``` again and then press ```
>
```

aka shift + .

and post the output

OK, here it is:

```

top - 20:04:31 up  4:44,  2 users,  load average: 0.67, 0.51, 0.40
Tasks: 101 total,   4 running,  97 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.0%us,  1.0%sy,  0.0%ni, 95.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    384508k total,   378772k used,     5736k free,      960k buffers
Swap:  1116476k total,    81072k used,  1035404k free,    49536k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5864 mike      20   0  252m 100m  24m R  5.7 26.7  53:28.03 firefox            
 5114 root      20   0  255m  28m 6024 S  1.7  7.5   8:34.92 Xorg               
 5976 mike      20   0 75260  20m  10m R  0.7  5.4   0:01.02 gnome-terminal     
 5703 mike      20   0 58284  19m 9940 S  0.0  5.2   0:01.10 nautilus           
 5702 mike      20   0 35912  17m  11m S  0.3  4.6   1:04.81 gnome-panel        
 5776 mike      20   0 25956  12m 8768 S  0.0  3.5   0:00.62 update-notifier    
 5675 mike      20   0 48032  12m 8104 S  0.0  3.4   0:52.52 gnome-settings-    
 5845 mike      20   0 44748  12m 9224 S  0.0  3.4   0:00.40 mixer_applet2      
 5848 mike      20   0 26088  11m 8276 S  0.0  3.2   0:00.28 fast-user-switc    
 5790 mike      20   0 25192  10m 7676 R  0.0  2.9   0:11.68 nm-applet          
 5792 mike      20   0 24256 9.9m 6412 S  0.0  2.6   0:25.02 python             
 5781 mike      20   0 62336 9632 8160 S  0.0  2.5   0:00.15 evolution-alarm    
 5805 mike      20   0 23312 9376 7156 S  0.0  2.4   0:00.22 trashapplet        
 5766 mike      20   0 21644 9360 5352 S  0.3  2.4   0:56.27 compiz.real        
 5853 mike      20   0 18164 9192 6544 S  0.0  2.4   0:40.70 gtk-window-deco    
 5802 mike      20   0 38936 8772 7532 S  0.0  2.3   0:00.11 evolution-excha    
 5786 mike      39  19 30736 8532 2036 S  0.0  2.2   0:00.08 trackerd 
```

---

### Post by RequinB4 on 2008-09-20
ok your memory is fine... the only thing left i can think of is to make sure you have the newest vid card driver.  what is the output of ```
lspci
```

Also, go to system - admin - hardware drivers and check anything appropriate.

---

### Post by mczonie on 2008-09-20
> **RequinB4 said:**
> ok your memory is fine... the only thing left i can think of is to make sure you have the newest vid card driver.  what is the output of ```
lspci
```

```

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:06.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem (rev 02)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
```
> Also, go to system - admin - hardware drivers and check anything appropriate. 

It says "no proprietary drivers are in use on this system" but have no idea what that means. Like I said before, I'm totally computer illiterate.

---

### Post by RequinB4 on 2008-09-20
You should have the updated drivers for that card... I honestly can't tell you for certain what is wrong now, and compiling a new driver won't help and is very error prone.  Can you tell us when and where etc this grey area happens, what options you have, etc?

That's all i know how to do.  Hopefully it was just opera and firefox messing things up.

---

### Post by mczonie on 2008-09-20
> **RequinB4 said:**
> Can you tell us when and where etc this grey area happens

It usually happens when I open lots of tabs or load a page with lots of video content. Sometimes my browser crashes alltogether. 

The problem here is obviously that something is hogging all my memory, but I can't imagine what.

---

### Post by quinnten83 on 2008-09-20
Flash is a memory hog in firefox, so if you are watching a lot of video content, your system will be slowed down considerably.
you can try installing the newest flash 9 beta (or release candidate), which I hear works better than the current one. You're going to have to google the install instructions though.

---

### Post by nowshining on 2008-09-20
hmmm killall opera &
killall firefox 

firefox seems to work fine, the problem may lie with opera...:/ try re-opening opera and going to a flash site, etc... flash does take up a lot of cpu...

---

### Post by mczonie on 2008-09-20
> **nowshining said:**
> try re-opening opera and going to a flash site, etc... flash does take up a lot of cpu

Opera won't even work most of the time with flash or any videos. I have to use Firefox for that.

---

### Post by Qinjuehang on 2008-09-20
You might want to try turning off compiz by pressing Alt-F2 and entering ```
metacity --replace
```
And see if you still have any grey screen problems.

---

### Post by mczonie on 2008-09-20
> **Qinjuehang said:**
> You might want to try turning off compiz by pressing Alt-F2 and entering ```
metacity --replace
```
And see if you still have any grey screen problems.

What's compiz and what does it do?

---

### Post by hellion0 on 2008-09-20
> **mczonie said:**
> What's compiz and what does it do?It's a compositing program. Basically, it gives you wobbly windows, the desktop cube and at its most basic, shadows beneath the windows and transparency. It's all the "extra" visual effects.

---

