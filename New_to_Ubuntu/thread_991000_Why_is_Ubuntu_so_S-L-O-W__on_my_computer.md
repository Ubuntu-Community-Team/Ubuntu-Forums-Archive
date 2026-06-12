---
title: "Why is Ubuntu so S-L-O-W  on my computer???"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by scylla2 on 2008-11-23
I recently installed Ubuntu 8.10 64-bit on my laptop. The machine runs an AMD 64 bit processor at 1.8GHz and has 512MB of RAM. It still has Windows XP on it, and I made a 20GB partition in which to install and dual-boot Ubuntu.

It's still pretty much a fresh Ubuntu install, and I've only made a few customizations to the desktop, etc. I really like the look and feel of this OS and I'm glad I'm taking advantage of the computer's 64-bit capabilities. I'd use this OS exclusively if it didn't run SO DAMN SLOW.

Windows is WAY faster. I find in Ubuntu I'm constantly waiting for the screen to refresh, for pages to load, and for applications to open and close. I spend a HUGE amount of time watching the mouse cursor spin and the screen "dims" at least a couple of times every 5 minutes, often without any reason at all.

All I ever really do is run Firefox and listen to music, but this seems to much for the system. Opening Firefox takes forever, and if I afterwards open the music software it's often over a minute before I can continue browsing web pages. Meanwhile I'm watching the cursor spin, the screen dim over and over, and hearing the music skip like crazy as it starts up.

I was really hoping, among other things, to get an increase in speed by installing Linux on this PC. I'm now very ready to un-install it and just go back to the much faster Windows.

What gives here? The PC seems to run fine and doesn't ever lock up or crash, but I can't handle tapping my fingers waiting for it to figure out what to do when I know in Windows the same actions would take mere seconds. Is there anything I've done wrong here? Isn't Linux supposed to run MUCH faster than Windows? I'm very disillusioned with this at the moment. This is my first experience with Linux.

PS - As I've typed this the screen has "dimmed" three times and made me wait. I'm not even running any apps other than Firefox at the moment.

---

### Post by Michael.Godawski on 2008-11-23
What do you expect as an answer?

There are many of us who enjoy the benefits of linux. I am sorry that your installation has gone awry, because your Ubuntu is not THE ubuntu.

---

### Post by zesu on 2008-11-23
:KS
firefox 3.0.x is more faster than 2.0.x any way

---

### Post by Toet on 2008-11-23
There must be something wrong at your setup. Ubuntu is way faster than Windows. The only thing when Ubuntu gets a bit slow is when there is a lot of harddisk activity. 

Is your swapfile being used a lot?

---

### Post by scylla2 on 2008-11-23
I'm not sure about the swapfile. How would I tell for sure? I can say that the HD light is on a lot, and is usually on solid while the computer slows.

---

### Post by drs305 on 2008-11-23
If you post the results of "free" we can take a look at the memory and swap file usage.

---

### Post by Michael.Godawski on 2008-11-23
Let's check what could be eating up the resources.
If you can open the terminal and run

```
top
```

and post the output here.

---

### Post by Funnnny on 2008-11-23
Ubuntu wayyyy faster.
Maybe you want to reinstall Ubuntu and see.

---

### Post by crjackson on 2008-11-23
> **scylla2 said:**
> I recently installed Ubuntu 8.10 64-bit on my laptop. The machine runs an AMD 64 bit processor at 1.8GHz and has 512MB of RAM. It still has Windows XP on it, and I made a 20GB partition in which to install and dual-boot Ubuntu.

It's still pretty much a fresh Ubuntu install, and I've only made a few customizations to the desktop, etc. I really like the look and feel of this OS and I'm glad I'm taking advantage of the computer's 64-bit capabilities. I'd use this OS exclusively if it didn't run SO DAMN SLOW.

Windows is WAY faster. I find in Ubuntu I'm constantly waiting for the screen to refresh, for pages to load, and for applications to open and close. I spend a HUGE amount of time watching the mouse cursor spin and the screen "dims" at least a couple of times every 5 minutes, often without any reason at all.

All I ever really do is run Firefox and listen to music, but this seems to much for the system. Opening Firefox takes forever, and if I afterwards open the music software it's often over a minute before I can continue browsing web pages. Meanwhile I'm watching the cursor spin, the screen dim over and over, and hearing the music skip like crazy as it starts up.

I was really hoping, among other things, to get an increase in speed by installing Linux on this PC. I'm now very ready to un-install it and just go back to the much faster Windows.

What gives here? The PC seems to run fine and doesn't ever lock up or crash, but I can't handle tapping my fingers waiting for it to figure out what to do when I know in Windows the same actions would take mere seconds. Is there anything I've done wrong here? Isn't Linux supposed to run MUCH faster than Windows? I'm very disillusioned with this at the moment. This is my first experience with Linux.

PS - As I've typed this the screen has "dimmed" three times and made me wait. I'm not even running any apps other than Firefox at the moment.

It's likely your complaint is related to your video card. My laptop doesn't exactly love 8.10 either. That's because I have an ATI 9600 Mobility Radeon. Support for this card is minimal in 8.10.

It runs very fast however on 8.04 which has only been out for 7 months and is supported for 3 years on desktop and 5 on server.

If I were you I would install the 32-bit version of 8.04, get all updates, enable all repositories and install the restricted drier from the driver manager. After that there are many tweaks I usually do to kick it up a notch.

8.04 leaves xp in the dust in my Athlon 64 laptop with an ATI video card.

Remember that xp is a very old OS designed to run on older hardware. Compare Ubuntu to Vista not XP. That said, Ubuntu can still run just as fast (or faster for me) on my laptop.

---

### Post by Paqman on 2008-11-23
What graphics card do you have? Have you enabled any drivers that the system is requesting in System > Admin > Hardware Drivers?

---

### Post by ajgreeny on 2008-11-23
In a terminal type ```
free -m
``` and you will see how much of your swap is being used, as well as how much of your ram.  The output will look a bit like this:-

                  total       used       free     shared    buffers     cached
Mem:          1011        849        161          0         51        448
-/+ buffers/cache:        349        662
Swap:         1192          0       1192

Ignore for the moment the top line, which shows how much ram contains data, not how much of that data is being used by the system.  In my case you will see that 849 MB is used, out of the 1011 available, but remember that linux works on the principle that unused ram is wasted ram, and it doesn't free it until it is needed for something else.  The more important figures are the *+/- buffers/cache* line which shows how much ram is currently in real use, ie 349 MB.  The final line is the swap partition usage, zero in my case.

It does sound as if something is not running quite right on your system, however.  Try turning off the tracker using System->Preferences->Search and Indexing to see if that helps for the time being.  It can be pretty resource hungry on a newly installed system whilst it indexes files.

---

### Post by scylla2 on 2008-11-23
> **Michael.Godawski said:**
> Let's check what could be eating up the resources.
If you can open the terminal and run

```
top
```

and post the output here.

Okay, thanks, here you go:

I'd hate to have to re-install. The 64-bit disk image doesn't even work right and has to be installed on a USB stick first. I erased the USB stick ages ago.

(The screen dimmed twice while I typed the above paragraph!!)

Thanks for all the help.


top - 12:20:10 up 1 day,  3:00,  3 users,  load average: 0.96, 1.10, 1.11
Tasks: 151 total,   2 running, 149 sleeping,   0 stopped,   0 zombie
Cpu(s): 14.9%us,  5.9%sy,  0.0%ni, 78.9%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:    508120k total,   502008k used,     6112k free,     2392k buffers
Swap:  1012052k total,   515020k used,   497032k free,    48464k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
13225 kathy     20   0  128m  21m 3956 S  8.3  4.4 201:41.88 npviewer.bin       
 5129 root      20   0  387m  64m 4932 R  6.6 13.0  55:40.05 Xorg               
 6570 kathy     20   0  153m 3396 2736 S  6.0  0.7  42:32.10 pulseaudio         
 6632 drew      20   0  295m  30m  13m S  2.0  6.2   0:01.68 gnome-terminal     
 5525 drew      20   0  219m 4800 2792 S  1.0  0.9   3:07.61 compiz.real        
25660 drew      20   0  676m 141m  15m S  1.0 28.5 202:09.35 firefox            
 4586 root      15  -5     0    0    0 S  0.7  0.0   0:13.28 kondemand/0        
 6661 drew      20   0 19100 1352  992 R  0.7  0.3   0:00.30 top                
 5576 drew      20   0  242m 4064 3024 S  0.3  0.8   1:09.20 mixer_applet2      
    1 root      20   0  5240  360  296 S  0.0  0.1   0:01.00 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.16 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:01.06 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   44 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0

---

### Post by MrWES on 2008-11-23
Did you set it up with a swap file?

---

### Post by scylla2 on 2008-11-23
Yeah this laptop also has a ATI 9600 Mobility Radeon. Do you think that's the problem?

If I were to re-install (ugh), shouldn't I go with 64-bit 8.04?

Thanks,





> **crjackson said:**
> It's likely your complaint is related to your video card. My laptop doesn't exactly love 8.10 either. That's because I have an ATI 9600 Mobility Radeon. Support for this card is minimal in 8.10.

It runs very fast however on 8.04 which has only been out for 7 months and is supported for 3 years on desktop and 5 on server.

If I were you I would install the 32-bit version of 8.04, get all updates, enable all repositories and install the restricted drier from the driver manager. After that there are many tweaks I usually do to kick it up a notch.

8.04 leaves xp in the dust in my Athlon 64 laptop with an ATI video card.

Remember that xp is a very old OS designed to run on older hardware. Compare Ubuntu to Vista not XP. That said, Ubuntu can still run just as fast (or faster for me) on my laptop.

---

### Post by scylla2 on 2008-11-23
Won't I have difficulty getting the Broadcom wireless card to work right with 8.04?

---

### Post by Toet on 2008-11-23
> Mem:    508120k total,   502008k used,     6112k free,     2392k buffers
Swap:  1012052k total,   515020k used,   497032k free,    48464k cached

Your swap is used quite a lot, imho this is the source of the slowness, dimming your applications and slowing Ubuntu.

Edit: Is your videocard using shared memory, and if so, how much is it using?

---

### Post by scylla2 on 2008-11-23
> **Toet said:**
> Your swap is used quite a lot, imho this is the source of the slowness, dimming your applications and slowing Ubuntu.


Thanks... so how should I go about addressing this problem??

I have no idea how much memory the vid card is using. How would I find this out?

---

### Post by Toet on 2008-11-23
> **scylla2 said:**
> Thanks... so how should I go about addressing this problem??

I have no idea how much memory the vid card is using. How would I find this out?

It would not make a lot of difference anyway I'm think now. I'm still looking for a clue how to stop your harddrive from going wild. Not sure how you could stop using the swap for so much.

Maybe someone else. From the top command it is not clear how much ram is being used by applications I think, only applications + cache.

Could you post the results of "free -m" as asked earlier in the thread?

---

### Post by scylla2 on 2008-11-23
Here are the results from free -m
.

             total       used       free     shared    buffers     cached
Mem:           496        490          5          0          0         40
-/+ buffers/cache:        449         46
Swap:          988        510        477


Getting the terminal window up took a good two minutes. The screen dimmed about 4 times and the HD light was on steady. Switching between users takes AT LEAST 5 minutes of looking at a black screen.

This time I counted. While typing the above (or trying to) the screen dimmed EIGHT TIMES. HD light was on steady.

This install is obviously not working. The PC is all but useless the way it is now.

Thanks, BTW, for all the help so far. I'm open to any suggestions.

I've downloaded the ISO image for Ubuntu 8.04 64-bit (downloaded on a separate PC running WIndows). Should I burn and install this instead?? Will I have troubles with it recognizing my Broadcom wireless card in this laptop? Thanks again.

---

### Post by Sealbhach on 2008-11-23
Are you using the new 64-bit flash? I notice you have npviewer.bin in your top, which is a flash related issue.

[http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)

Also, close down any sessions you don't need at startup, like tracker.



.

---

### Post by Toet on 2008-11-23
> **scylla2 said:**
> Here are the results from free -m
.

             total       used       free     shared    buffers     cached
Mem:           496        490          5          0          0         40
-/+ buffers/cache:        449         46
Swap:          988        510        477


Getting the terminal window up took a good two minutes. The screen dimmed about 4 times and the HD light was on steady. Switching between users takes AT LEAST 5 minutes of looking at a black screen.

This time I counted. While typing the above (or trying to) the screen dimmed EIGHT TIMES. HD light was on steady.

This install is obviously not working. The PC is all but useless the way it is now.

Thanks, BTW, for all the help so far. I'm open to any suggestions.

I've downloaded the ISO image for Ubuntu 8.04 64-bit (downloaded on a separate PC running WIndows). Should I burn and install this instead?? Will I have troubles with it recognizing my Broadcom wireless card in this laptop? Thanks again.

That 46 means you have 46Mb free memory, I think. That is not a lot, and is causing the slowness. Harddisk activity in Ubuntu gets priority, as the kernel is not configured for desktop by default. Configuring a desktop kernel is quite advanced stuff, and would not help your situation enough.

If you could limit your swap activity, aka free memory, you'd be fine for performance.

As for the ATI and Broadcom driver with 8.04.1 or 8.10, I do not have any knowlegde. So I'll guess somebody else is going to answer that.

---

### Post by Toet on 2008-11-23
You could try the 8.04.1 Live CD (without installing) btw, and look how memory usage is, and see if your Broadcom gets recognized.

---

