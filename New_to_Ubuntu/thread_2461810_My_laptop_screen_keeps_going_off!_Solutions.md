---
title: "My laptop screen keeps going off! Solutions?"
date: 2021-05-07
forum: New to Ubuntu
---

### Post by oneala on 2021-05-07
PC system : Asus TUF GAMING (FX705DT-AU092T)
After a given period of time, my laptop screen just goes off. After pressing the power button, my system boots up and works normally, till it eventually goes off again.

I found someone experiencing something similar here :
[https://askubuntu.com/questions/823124/screen-randomly-turning-off](https://askubuntu.com/questions/823124/screen-randomly-turning-off)

But I would like to know more about what is happening above (I am not sure what the commands in the link is doing.) Any help will be really appreciated. Just trying to learn. 
Thank you.

---

### Post by TheFu on 2021-05-07
Battery saving mode?
Screen saver or power settings to put the system to suspend mode? Hibernate mode?

Depending on the release, check out the "Ubuntu Desktop Guide" power management settings.  There are desktop guides for some of the other DEs too.

To get better help, always specify the exact Ubuntu release you are running 
AND
the DE being used.

---

### Post by oneala on 2021-05-08
I am running on Ubuntu 20.04.2 LTS, DE is GNOME 3.36.8

I don't think it is battery saving mode, or hibernate mode, because the screen doesn't shut down 'cleanly' There is occasionally some static on the screen before it shuts down (somethimes with noise too). Nonetheless I will check out the desktop guide's power management settings, and get back.

---

### Post by rsteinmetz70112 on 2021-05-10
Are you running on battery or on line power when it shuts down.

---

### Post by oneala on 2021-05-10
It doesn't seem to make difference whether I am on battery or connected to line power, both times It goes off. I noticed a pattern that if I move my laptop abruptly (say moving it from one table to a coffee table) it goes off too. Could it be something related to hardware?

---

### Post by TheFu on 2021-05-10
> **oneala said:**
>   Could it be something related to hardware?

Yes.  Could be a lose electrical connection.  Try re-seating all of those and cleaning out all the dust from inside the case.

---

### Post by Autodave on 2021-05-10
Check the RAM chips: remove them, blow out any dust, reinstall.

---

### Post by rsteinmetz70112 on 2021-05-10
Make sure the battery is firmly in place, check the connections and clean the contacts.

---

### Post by Frogs Hair on 2021-05-10
Is the computer over heating prior to shutdown ?

---

### Post by oneala on 2021-05-11
yes, it tends to get really hot at times. This is just when I am doing basic stuff like surfing, and editing documents. Will try to cleaning and reseating, as suggested and will then update.

---

### Post by oneala on 2021-05-11
Update.. This seems to only be happening when I am on Ubuntu, when i boot into Windows, this does not happen. I am uncertain how to diagnose this..

---

### Post by oneala on 2021-05-11
Oh and I also cleared out dust, and checked connections.. No change

---

### Post by oneala on 2021-05-12
So I have dusted and cleaned up the contact points and even the fan, but still when I log-in to Ubuntu, my screen again shuts down. On the other habd when I boot into Windows, this doesn't happen (In all the time I was using Win, it only went off once for some update, as compared to 6+ times on Ubuntu).

---

### Post by Frogs Hair on 2021-05-12
If it is overheating I suspect there was some sort of problem with the Ubuntu installation. If you run the following command in the terminal it should display what process may be causing the problem. Post output here via copy&paste  ```
top
```

---

### Post by amanchesterman on 2021-05-13
I don't want to complicate matters but I had the same problem (without the overheating) on my laptop. I've tracked it down to DPMS, which apparently stands for 'display power management signalling' and is often built into hardware.

I run Xubuntu and there are settings to disable the screensaver, not blank the screen etc. -- but on my machine these are ignored and the screen goes blank after a few minutes, whether it's running on battery or mains power. But the XFCE power manager has an option to enable 'presentation mode', and when that is selected DPMS is disabled and the screen stays on.

I don't know if your DE has a similar option? It might be worth exploring anyway, besides tackling the overheating of course.

---

### Post by oneala on 2021-05-14
Thanks for sharing your experience @amanchesterman, but i have Ubuntu  20.04 which runs on Gnome and I am currently unable to find much about  DPMS, though I will keep trying. Also!! The same thing has also happened  just now on my system when I tried to boot it from Windows 10! it shut  off, and when I powered it back on I got the message :"Unexpected Kernal  mode trap".
So I am kind of concerned that it is something related to the hardware bit :/

---

### Post by oneala on 2021-05-14
@FrogsHair, below is the result of top:

```


top - 16:22:40 up 1 min,  1 user,  load average: 2.10, 1.01, 0.39
Tasks: 304 total,   1 running, 303 sleeping,   0 stopped,   0 zombie
%Cpu(s): 13.0 us,  1.2 sy,  0.0 ni, 85.2 id,  0.0 wa,  0.0 hi,  0.6 si,  0.0 st
MiB Mem :   7832.3 total,   4760.9 free,   1403.1 used,   1668.3 buff/cache
MiB Swap:   2048.0 total,   2048.0 free,      0.0 used.   6142.1 avail Mem 

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                                                                              
   2082 ro        20   0 1256876 225688  41988 S  77.1   2.8   0:08.72 snap-store                                                                                                                           
   1616 ro        20   0 1459892  93952  62748 S   4.7   1.2   0:04.45 Xorg                                                                                                                                 
   1807 ro        20   0 5294268 294220 121708 S   4.0   3.7   0:09.58 gnome-shell                                                                                                                          
   2752 ro        20   0 2200844 113004  77736 S   3.0   1.4   0:07.80 skypeforlinux                                                                                                                        
   2887 ro        20   0 6192916 159492 110180 S   2.7   2.0   0:10.02 skypeforlinux                                                                                                                        
top - 16:22:44 up 1 min,  1 user,  load average: 2.10, 1.01, 0.39
Tasks: 304 total,   2 running, 302 sleeping,   0 stopped,   0 zombie
%Cpu(s):  2.7 us,  1.1 sy,  0.0 ni, 96.0 id,  0.0 wa,  0.0 hi,  0.2 si,  0.0 st
MiB Mem :   7832.3 total,   4753.3 free,   1408.9 used,   1670.1 buff/cache
MiB Swap:   2048.0 total,   2048.0 free,      0.0 used.   6136.3 avail Mem 


```

---

### Post by MAFoElffen on 2022-02-26
I can confirm that the defualt seetings have DPMS on by default...
```

xset s off -dpms

```
That will disable DPMS and turn off screen blanking. If it is using an zorg.conf file, like the ones in /etc/X11/xorg.conf.d/, there are two sections (Monitor, Extensions) where you can disable or turn off DPMS.

---

### Post by bietduoc on 2022-03-05
You can check ram and cpu again, sometimes there are errors that cause overheating

---

