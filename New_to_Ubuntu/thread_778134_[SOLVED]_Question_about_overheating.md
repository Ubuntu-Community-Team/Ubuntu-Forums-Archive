---
title: "[SOLVED] Question about overheating"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by njd4k on 2008-05-01
I've been playing with Hardy 8.04 on my laptop using Wubi and I like it, but I've noticed my computer runs noticeably hotter when it's running Linux than Win XP. 

I haven't found anybody else here complaining of this. Ubuntu has otherwise been performing better than I had expected, but I'm worried it's slowly simmering my computer. Is that even possible? Has anybody else experienced this? I'm a computing dilettante and not very sophisticated about hardware. I'm running 32-bit Hardy on an Intel Core 2 Duo in Wubi. (64-bit was mildly buggy.)

---

### Post by Anduu on 2008-05-01
A little more info would be helpful.

What kind of temperatures are you getting?Are you getting random lockups as the temps go up?

---

### Post by Madman6510 on 2008-05-01
Why do you think it's overheating? Are you getting crashes, does it seem hotter than normal, making noise, etc?

---

### Post by njd4k on 2008-05-01
I haven't had any lockups. I can't figure out how to get a temperature in Linux. I just noticed that the laptop seemed a lot hotter than normal when I'm running Ubuntu. It's hotter right now (in Ubuntu), and has been any other time I've bothered to check. Otherwise no problems. 

But it seems on these message boards other people are locking up. I may try 7.10/Gutsy Gibbon and see if that has the same problem.

---

### Post by spacefreak86 on 2008-05-01
What are the general temperature and battery life ranges for Ubuntu vs Windows vs. Mac?

---

### Post by wheels. on 2008-05-02
What kind of a laptop do you have, I am having overheating issues temps over 60 just sitting around, peaking close to 80, I am not using wubi though, does your fan ever seem to really kick in? Mine always just seems to spin at the same speed.

---

### Post by drsox1899 on 2008-05-02
Here's how to get sensors on your Ubuntu installtion : [http://www.techthrob.com/tech/linuxsensors.php](http://www.techthrob.com/tech/linuxsensors.php)

Works very well.  Remember to reboot/logout to enable the addition of the Hardware Sensors Monitor applet to the AddToPanel options.

---

### Post by TimKraemer on 2008-05-02
I had the same problem:

In my case, the source seemed to be, that the ram got incredibly hot, because it was constantly reorganized by the kernel and unused data was swapped out to the swap partition on my harddrive. 

If you feel that you have the same problem, you might want to do a google search on "swappiness".

My solution was to change the "swappiness" to 0. You can try it on-the-fly by "sudo sysctl vm.swappiness=0". This means that your kernel will only swap out data from your ram, if more free ram is needed. My ram (and my CPU next to it) stays much colder now. So far I haven't noticed any decrease in performance.

Good luck!

---

### Post by njd4k on 2008-05-02
Thank you all for your help. I'll see what the temperature sensors have to say and report back Monday.

---

### Post by bilal.17 on 2008-05-02
I have the same problem, and im gonna try out the solution that TimKraemer posted

---

### Post by wheels. on 2008-05-02
> **TimKraemer said:**
> I had the same problem:

In my case, the source seemed to be, that the ram got incredibly hot, because it was constantly reorganized by the kernel and unused data was swapped out to the swap partition on my harddrive. 

If you feel that you have the same problem, you might want to do a google search on "swappiness".

My solution was to change the "swappiness" to 0. You can try it on-the-fly by "sudo sysctl vm.swappiness=0". This means that your kernel will only swap out data from your ram, if more free ram is needed. My ram (and my CPU next to it) stays much colder now. So far I haven't noticed any decrease in performance.

Good luck!

What are your average temps now, after setting the "swappines"?
Mine are sitting at about 52 Celsius after trying your fix, much better than the high 50s to 70s that I had yesterday, so do I have to run that command every time I log in or is there a way to make it permanent?

Thanks for the solution!!

---

### Post by TimKraemer on 2008-05-03
You can add the line "vm.swappiness=0" to the end of the file /etc/sysctl.conf to make the change permanent.

I was able to reduce the idle temperature of my cpu from a bit under 70C to roughly 55C. But thats of course still much too hot. 

The heat issues with ubuntu seem to be caused by several independent kernel "features". Anticipatory swapping is **only one** of them. Swapping ( [http://lwn.net/Articles/83588/](http://lwn.net/Articles/83588/) ) would definitely give you an increase in performance on a desktop client, but on a Laptop this gain in performance comes with severe overheating issues. 

I assume there might be other similar kernel-features, which would give you a small gain in performance, but which cause overheating on Laptops.

Even after I  killed the Xserver and all auxiliary processes/devices, with barely 1-2% CPU usage, 1% RAM usage and a dozend tasks still running, the temperature of my CPU would not go below 50C

---

### Post by njd4k on 2008-05-05
I've been getting temps in the low 50s consistently, and finally did manage to push it to the 70s C and lockup the computer. Apparently OpenOffice really heats things up. Adjusting swappiness did not seem to improve performace.

I like Ubuntu's user interface, but this definitely isn't acceptable on my computer. Oh well -- The nice thing about Wubi is how easy it is to try this out without a lot of work. I guess I'll just stick with XP a few more years.

---

### Post by njd4k on 2008-05-05
Thanks for all your help

---

### Post by game_plan on 2008-05-05
You can view and change how the system handles power and temperature using acpi command.

I've also found that open office and some flash videos heat up the system for a while, but the cool off.

I've found windows Vista ran around 62 celcius and Ubuntu runs 51 so Vista is definitely a hog on the system.

---

### Post by mustang on 2008-05-05
```
sudo apt-get install powertop
```

See what reductions, if any, that yields.

---

### Post by njd4k on 2008-05-05
> **game_plan said:**
> You can view and change how the system handles power and temperature using acpi command.

I've also found that open office and some flash videos heat up the system for a while, but the cool off.

I've found windows Vista ran around 62 celcius and Ubuntu runs 51 so Vista is definitely a hog on the system.

I almost said that Ubuntu's performance reminded me of Vista (which I also uninstalled, depsite having a "capable" machine!), but I thought the community might take it as an affront. :)

I'll try acpi and mustang's powertop before I uninstall then.

---

### Post by njd4k on 2008-05-05
Even with all the tweaks suggested here combined I'm still only a few deg. Celsius cooler. :(

---

### Post by njd4k on 2008-05-05
Hmm, it turns out the Core 2 Duo is designed to run hotter than I'd realized. It's only a few degrees cooler in Windows XP, by design.

Well, maybe I can keep using ubuntu with the tweaks after all. Thank you all for your help.

---

### Post by rekster on 2008-05-05
This is a very interesting post, I also found my laptop getting extremely hot.  When I was running the previous Ubuntu my laptop actually died, thank god it was under warranty and I got the mainboard replaced.

I don't know if this was pure coincidence or not but now I'm getting worried it will happen again..

Note though, it only got that hot when running a graphics intensive 3d game.  However did not get as hot running WinXP with the same game.  I'd rather not use Windows though, hopefully I can find a way to make sure the temperature does not get so high again.  I noticed when the laptop started running too hot the graphics started to glitch out and the game was stuttering, only after it was running for a while.  I'll try some of the suggestions listed in the previous posts, but this does have me worried now...

edit: Tried the suggestions, then loaded the game.  After about 4 minutes the cpu was at 77 degrees...   uh oh we got a problem!

I will boot into Windows, load the same thing and check temperatures and see what the difference is.  I'll keep you posted.

---

