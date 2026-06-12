---
title: "Video streaming is choppy! Best Flash player for Xubuntu 12.10?"
date: 2012-11-13
forum: New to Ubuntu
---

### Post by Mazraq on 2012-11-13
Hi there,

I'm running Xubuntu 12.10 in a Lenovo X100e laptop. My computer has full capacity RAM of 4GB DDR2 and a processor of 1.6 GHz. I am having issues of video streaming online like on Youtube, even when the video is fully buffered, the transition is a bit choppy. I checked my perfetchable memory , as a post on this forum suggested and it is allocated!
[HTML]reg03: base=0x0c0000000 ( 3072MB), size=  256MB, count=1: write-combining[/HTML]I wonder if my flash player is not the ideal one for Xubuntu 12.10, how would I know? Or if there is a transition accelerator I should install?

Thank you very much in advance and I look forward to hearing from you!

Moe

---

### Post by mastablasta on 2012-11-13
what is the GPU (graphics card)? does it have good linux support? it could be that CPU is taking all the load from video graphics acceleration making it choppy. and also flash is not good on some graphics cards.

---

### Post by Mazraq on 2012-11-13
How can I know the GPU card that I have and whether or not it has good linux support! I'm sorry, I am really a beginner in this :( Also, any better solution to flash?

---

### Post by audiomick on 2012-11-13
> **Mazraq said:**
> How can I know the GPU card that I have

Open a terminal and do the command

```
sudo lshw -c video
```

You will be asked for your password. Don't be disturbed that you don't see what you are typing. Just type your login password and hit enter.


Just for info, if you do lshw without the -c option and class after it, you get a full list of your machine's hardware.

---

### Post by Mazraq on 2012-11-13
Thanks a lot Michael, I really appreciate it! Now here is the result of running this command...Any help in understanding why my video streaming transition is choppy and what I could do about it? Your advice is highly appreciated! You guys are awesome!

[HTML]mazraq@mazraq-ThinkPad-X100e:~$ sudo lshw -c video
[sudo] password for mazraq: 
  *-display               
       description: VGA compatible controller
       product: RS780M/RS780MN [Mobility Radeon HD 3200 Graphics]
       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:18 memory:c0000000-cfffffff ioport:9000(size=256) memory:d0200000-d020ffff memory:d0100000-d01fffff
[/HTML]

---

### Post by mikewhatever on 2012-11-13
"Best Flash player for Xubuntu" sounds like a grotesque oximoron. All flash palayer for Linux are pretty bad, but since you've asked, IMHO, the best among the bad is the Adobe Flash player.

---

### Post by audiomick on 2012-11-13
I can't help too much other than to say that I have gained the impression lately that Radeon graphics can be an annoyance.

I searched the forum for 

Mobility Radeon HD 3200 Graphics

and turned up this thread. Have a look at it. I think there is some stuff in there that might help you along a bit. 


[http://ubuntuforums.org/showthread.php?t=2073193&highlight=Mobility+Radeon+HD+3200+Graphics]("http://ubuntuforums.org/showthread.php?t=2073193&highlight=Mobility+Radeon+HD+3200+Graphics")

---

