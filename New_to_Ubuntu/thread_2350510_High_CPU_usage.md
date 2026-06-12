---
title: "High CPU usage"
date: 2017-01-25
forum: New to Ubuntu
---

### Post by martemarziano on 2017-01-25
Hi everyone, 
Something is consuming almost the whole of the processors capacity. I had only the system monitor opened but the processor ran almost 100%. I couldn't see from the system monitor what it is all about. Can anyone tell?

---

### Post by howefield on 2017-01-25
Can you run the top command from a terminal (instead of system monitor) ?

```
top
```

Should get an idea of what is eating the cpu from that.

---

### Post by martemarziano on 2017-01-25
Thanks for the quick reply!
I happened to post after I had restarted the computer and things seemed already to have calmed down but I have noticed that Xorg can take up a whole lot of cpu- time and capacity. Is that normal? I will be running the top command as you have suggested and keep an eye on what's going on behind the curtains. As an ex-Windows user and new to Linux, I understand that there is a whole new world to discover and learn about and I am grateful for all the help I can get. Thanks again!

---

### Post by howefield on 2017-01-25
Glad to hear the computer has settled down, if you need to use the "*top*" command you can look for the load averages and the cpu column. Htop is an alternative command but would be installed whereas top is pre-installed with a default Ubuntu installation.

Perhaps the computer was busy for a few minutes checking for updates.

If you post again on the subject, it would help to now the machine specifications.

---

### Post by martemarziano on 2017-01-25
I suspected too that it could have been the software updater causing the high cpu usage since shortly after the restart I got the message that the computer need to be restarted...
I will install the htop as well. I am happy to learn as much as I can about Linux. I am running Ubuntu- Mate on a quite low spec machine, but alright next time I would add more detailed machine specifications. 
Thanks again for your help!

---

### Post by oldrocker99 on 2017-01-25
I have a **very** low-end laptop, and as a big fan of Ubuntu MATE, I installed it on this crappy lappy. I found a large CPU load (I use it for DJing, and songs would break up with heavy CPU usage). I ended up installing LXDE and the footprint is far lower.

For what it's worth.

---

### Post by Impavidus on 2017-01-25
> **martemarziano said:**
> ... but I have noticed that Xorg can take up a whole lot of cpu- time and capacity.

That could mean there's a problem with your graphics driver. Have you let your system search for additional drivers?

---

### Post by martemarziano on 2017-01-25
Hi,
A search for additional drivers shows some "unknown device" is not working  and gives me the choice of not using the device or using processor microcode firmware for Intel CPUs from intel-microcode (propriaetary).
What shoul I do?

---

### Post by howefield on 2017-01-25
It is an update to the code already running inside your CPU, microcode updates are generally released to fix/improve issues with the original cpu firmware.

Your choice of whether to install or not, I certainly do.

---

### Post by martemarziano on 2017-01-25
Thanks, I'll do it right away!
By the way, here comes some spec you asked for before:
Laptop: Asus E402M
CPU: Intel BYT -M 2 cores, up to 2.58 GHz
Ram: 2 GB (got almost 2Gb as swap)
SSD 120 GB
OS: formerly Win. 10; Currently dualboot Mint 18.1 Cinnamon and Ubuntu 16.04 Mate

---

### Post by martemarziano on 2017-01-30
I have been keeping an eye on the CPU activities with htop, on and off for the past couple of days and things seem to be running quite smoothly. On moderate usage the average load is around 0.70 and rarely above 1.80 but

 I suppose all that is relative to how many applications are running at the same time. I haven't notice any one process making an excessive use of the cpu unless the software updater is running in the background or the like. 

Thanks everybody for your kind suggestions and advice.

---

### Post by DuckHook on 2017-01-31
If you consider this problem solved, *please mark thread **solved** using *Thread Tools* in the top toolbar for the benefit of others searching for solutions*.

---

### Post by ddascalescu+launchpad on 2018-01-15
> **martemarziano said:**
> Hi everyone, 
I had only the system monitor opened but the processor ran almost 100%. I couldn't see from the system monitor what it is all about.

System Monitor doesn't show the real CPU utilization of Xorg due to [this bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/1740247"). Please click "Does this bug affect you" on that page.

---

### Post by ddascalescu+launchpad on 2018-01-15
I also have this problem with xorg and compiz using 100% of the CPU, but that only happens randomly. I couldn't find a pattern and it's super annoying.

Here's a [screencast]("https://launchpadlibrarian.net/351151332/CPU%20utilization%20100%25%20yet%20System%20monitor%20doesn%27t%20show%20anything%20but%20htop%20does.gif"). My laptop is an ASUS with a hybrid graphics card.

I tried installing the Nvidia drivers but that was a horrible story never worked out after throwing my Ubuntu 16.04 into a boot loop, so I'm still using the Intel integrated graphics.

---

