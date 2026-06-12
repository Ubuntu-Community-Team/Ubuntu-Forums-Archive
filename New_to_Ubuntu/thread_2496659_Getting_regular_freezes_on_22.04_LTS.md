---
title: "Getting regular freezes on 22.04 LTS"
date: 2024-04-07
forum: New to Ubuntu
---

### Post by mklnln on 2024-04-07
Hi all,


While  coding on my work machine, I'll regularly (1-2x per day) experience an  issue where programs no longer respond to input, i.e. I can't type or  move any windows, but the mouse can still move. Eventually, my external  monitors will go black and my laptop screen will start flickering. I  haven't waited more than two minutes for it to go away, as I'm on the  clock at work. I hard reset and can get more work done.


I've  been keeping an eye on RAM usage, I don't seem to be completely maxing  out, nor does my swap partition get full. They might get up to 13/16GB  and 4/16GB, respectively.


I do  have a fair few programs always open (VSCode, Obsidian, Firefox,  Syncthing, Chrome (as a developer sandbox), Thunderbird, PgAdmin,  CopyQ). I also have a Dell DisplayLink D3100 USB hub for my two external  screens (that's three screens total, in addition to my laptop screen).


Just now I tried to troubleshoot a bit of Syncthing upon a fresh boot, few other programs loaded, and it freezed again.
Here's  a link to some crash files, I'm not sure that they're exactly related  to this issue, however. I get these crashes sometimes if it says xyz  program has run out of memory (though it still seems like Swap isn't  full) [URL="https://drive.google.com/drive/folders/1rPjTJDFQg4E-XVTBW9AxSE8RK4k2BznY"]https://drive.google.com/drive/folders/1rPjTJDFQg4E-XVTBW9AxSE8RK4k2BznY

[/URL]

Any tips on where to go with this? It sucks to have made a push to use Linux at work and now it seems unstable cuz noob :<

---

### Post by TheFu on 2024-04-07
So, most iGPUs take up to 2GB of system RAM, so if you have 16GB and 14GB is used, then you are completely out of RAM.

Did you look at the system log files?  That's always where you need to start whenever something bad happens on your computer.  Check the logs.  You can google "linux log files" for how to do it.

Also, for every statement you make, you need to prove it using a command.  It is very common, especially for noobs, to misinterpret what they are seeing with what is actually true.  So, you don't need to actually make any statements - just show the proof of what you think may be the issue.

On the surface, I'd say you ARE 100% running out of RAM and should close FireFox, Thunderbird, Chrome while you are working.  But without seeing portions of the system logs (I won't be scanning YOUR log files, ever), I wouldn't rule out a hardware fault.

It would be a smart idea to pay attention to when your computer just starts feeling a little slower, then shutdown the huge memory hogs ASAP. Give the system 20-40 seconds to complete that, then continue working.  Chrome is known to be extremely RAM abusive, often allocating 2x the amount of RAM the system has. The only way I know to get that freed is by closing the program.  If you like, you could run Chrome under a RAM restricted environment to prevent RAM use over 4GB. That would probably be useful for other bloated programs too.  I use **firejail** to add a RAM constraint to the bloated programs.  There are some historical reason for why Linux memory management works the way it does.

Also "not full" isn't exactly useful from a swap description.  Use 
```
free -hm
``` to show it with facts. For example, 
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           30Gi        20Gi       1.4Gi       103Mi       8.5Gi       9.4Gi
Swap:         4.1Gi       1.0Gi       3.1Gi

```
In theory, there's 32G of RAM in the system.  20G is being used, so 10G should be free, but 8.5G is being used by network and disk buffers.  For a desktop system, I think the only viable size for swap is 4.1G. Anything less isn't enough. Anything more is a waste.  Swap is there to provide feedback when a system is running out of RAM. It is up to the user to "feel" that slow down and take appropriate steps to reduce RAM use.  This is different from MS-Windows.  It is a historical thing.  Linux/Unix will allow you to shot yourself in the head, if you like.  You've seen that.

---

### Post by mklnln on 2024-04-07
Thank you! I've heard a similar thing about my machine just being overtaxed, but it didn't quite make sense to me since I'm able to do the *exact* same thing on ******* without the negative consequences. It sounds like I need to be better about memory management. As you said, I'll be careful and pay attention to high swap values, which sounds like it acts as the canary in the coal mine, RAM wise. 

I poked around in /var/log and looked at recent boots and journalctl entries. As I'm a bit of a noob, so nothing really jumped out at me. The hardware theory is still plausible, but this computer was bought only a couple months ago. It seems like the RAM theory is a good one to start working with. I'm going to use Firefox Developer Edition and see if I get better RAM use out of that, and I'll get wary when things jump up past 12ish. I'm going to look more in to Linux memory management to figure out exactly what I need to know to not keep running into this issue.

---

### Post by tea for one on 2024-04-08
> **mklnln said:**
>  The hardware theory is still plausible, but this computer was bought only a couple months ago.
Generally, recent hardware requires a later kernel.
Perhaps, give Ubuntu 23.10 a spin in a live session.
Also, Ubuntu 24.04 will be released soon - 25 April 2024.

---

### Post by gezzer2 on 2024-04-08
could you please check what power setting your system is using.
in a terminal please enter ..

cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor

this will show the setting that the system is using ie.

power saving
balanced
performance

---

### Post by TheFu on 2024-04-08
No matter how much a program running in Linux may appear to be the same as under some other OS, THEY ARE NOT THE SAME.  There are very different philosophies in the way that each OS was created.  Always remember that.

Linux doesn't validate that RAM is actually available when memory is returned for use.  That was a performance consideration, since validating that RAM exists added over 80% time to the malloc() call.  It wasn't always this way, but when RAM sized were easily affordable a 8GB, nobody thought that Mozilla and Google could waste 50GB of RAM so easily, but they do.  Around 2022, Canonical decided to add an overhead process, OMM, that watched RAM used by processes and kill the largest offenders without warning.  In theory, it should kill Chrome BEFORE it uses all the remaining RAM+swap, but that hasn't been my experience.  

Of course, there are always GPU driver issues, especially with nVidia GPUs. Those run in the kernel for performance and sometimes bad bugs happen. They are closed/proprietary, so only nVidia really knows how bad their driver code is. The rest of us have to look at results to make any guesses.

One troubleshooting technique on Linux is to boot into a Try Ubuntu mode off an install ISO flash drive and see if you can recreate the problem.  If you have lots of custom tools installed, that can be harder, since everything runs in RAM from read-only media, so it really only makes sense to do this when issues are with normal snaps or normal repos installed programs.  If you cannot recreate the issue running that way, it is likely a configuration problem.  
The next step is to create a new user account, login with that and see if you can recreate the problem.  If not, then that points at the settings in the other account, no system-wide settings.
See how we can cut out huge parts of the OS being involved to troubleshoot and how very little effort it all takes to try?


BTW, 
```
$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
cat: '/sys/devices/system/cpu/cpu*/cpufreq/scaling_governor': No such file or directory
```

---

### Post by gezzer2 on 2024-04-08
@TheFu

on my system i get after using that code 16 lines for the 16 threads of ..

schedutil

which i changed from powersaver by having to do a grub entry of ..

[COLOR=#0C0D0E][FONT=-apple-system]GRUB_CMDLINE_LINUX_DEFAULT="amd_pstate=[/FONT][/COLOR]guided[COLOR=#0C0D0E][FONT=-apple-system]"

as none of the power settings within settings would change the CPU frequency it was stuck on powersaver.
which in turn affected my GPU and how the whole system was running.

i believe these settings can affect intel CPU's as well ..
 [/FONT][/COLOR]

---

### Post by maglin2 on 2024-04-09
Probably off-topic wrt this thread, but I see the same behaviour (22.04, gnome settings doesn't actually change power mode).
I think it may be addressed in Noble [https://bugs.launchpad.net/ubuntu/+source/power-profiles-daemon/+bug/2046853](https://bugs.launchpad.net/ubuntu/+source/power-profiles-daemon/+bug/2046853)
I'm happy with how my machine runs stuck in powersave, so I haven't fiddled.

---

