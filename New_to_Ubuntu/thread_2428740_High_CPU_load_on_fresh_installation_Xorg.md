---
title: "High CPU load on fresh installation Xorg"
date: 2019-10-08
forum: New to Ubuntu
---

### Post by alstormprime on 2019-10-08
Good day community!

** Updated situation **

[COLOR=#000000]I've noticed that system works perfect when it is shut down with "Power Off" option.[/COLOR]
[COLOR=#000000]After "full" shutdown I don't have high CPU load issue and CPU frequency at idle are as next:[/COLOR]

[COLOR=#000000]alstorm@dolfin:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_cur_freq[/COLOR]
[COLOR=#000000]800018[/COLOR]
[COLOR=#000000]799999[/COLOR]
[COLOR=#000000]800012[/COLOR]
[COLOR=#000000]800002[/COLOR]

[COLOR=#000000]The high CPU load issue comes back after either a "Reboot" or "Suspend" (eg closing lid of the laptop without Shut Down)[/COLOR]
[COLOR=#000000]top doesn't blame any particular process for CPU load, but CPU frequencies stays maxed out.[/COLOR]

[COLOR=#000000]alstorm@dolfin:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_cur_freq[/COLOR]
[COLOR=#000000]3827087[/COLOR]
[COLOR=#000000]3700219[/COLOR]
[COLOR=#000000]3847067[/COLOR]
[COLOR=#000000]3700253[/COLOR]

[COLOR=#000000]Farther the issue stays present until "proper" Shut Down. And also require to wait some time before powering system back.[/COLOR]
[COLOR=#000000]In case if Shut Down is followed with too soon Power On - high CPU load issue is still present.[/COLOR]

** Original post ** 

Would like to ask for assistance in troubleshooting of high CPU usage on fresh Ubuntu installation (18.04.3)

Things I've noticed 
- the issue is not present when I boot from the same USB I used to install Ubuntu.
- when booting from HDD performance drops dramatically - scrolling web pages and printing in search bars become unusable.
- the hardware seems to be capable at handling such tasks smoothly (was okay under Win 10)
- HP Pavilion Laptop 13-an0031wm - Intel i3-8145U, 8GB RAM, 128GB SSD
- top gives most of CPU usage to Xorg (almost constant 90% ~ 105%) when System monitor or Firefox is running.

On the screen shot situation is depicted while installing updates - 3 cores have moderate load and one constantly full load.
The same core has near full load at idle when Firefox or System monitor is open...
[ATTACH=CONFIG]284164[/ATTACH]


So far I've gone through possible problems from this list  [https://wiki.ubuntu.com/X/Troubleshooting/HighCPU](https://wiki.ubuntu.com/X/Troubleshooting/HighCPU) with no positives  results.
1. killall vino-server -> vino-server: no process found
2. $ glxinfo | grep render -> direct rendering: Yes
3. /var/log/Xorg.0.log  -> has no records
4. ...figure out what X is actually doing during these high load  situations -> unfortunately, don't know how to figure this thing  out...

I've gone through several other attempts to follow steps I could find online in topics with similar issue - but had no luck.

Will be thankful for any suggestions on how to troubleshoot / pinpoint / figure out what can be the reason causing my issues!


$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Device 3ea0

---

### Post by oldrocker99 on 2019-10-08
Here's something about your problem, which apparently is not unique.

[https://wiki.ubuntu.com/X/Troubleshooting/HighCPU](https://wiki.ubuntu.com/X/Troubleshooting/HighCPU)

---

### Post by cruzer001 on 2019-10-08
At the login screen check to see your running either xorg or xwayland.

I would also check for BIOS updates.

---

### Post by alstorm on 2019-10-10
> **oldrocker99 said:**
> Here's something about your problem, which apparently is not unique.

[https://wiki.ubuntu.com/X/Troubleshooting/HighCPU](https://wiki.ubuntu.com/X/Troubleshooting/HighCPU)

Had no luck with following through steps listed in the link - details are in the first post.
Also, after spending more time studding the issue I feel as my first description might not that accurate.
Please see below my new findings.

> **cruzer001 said:**
> At the login screen check to see your running either xorg or xwayland.

I would also check for BIOS updates.

I've tried both xorg and xwayland, also tried Debian with mate and KDE - symptoms are the same.
After my recent findings (please see below) BIOS update seems to be one of the possibility.
HP offers BIOS update for my laptop. It's available only in the win executable format. 
I will try to recover into Win10 and use this update. Thought it will take for me several days.


After spending more time trying different things I would like to update description of my issue and system behaviour.

I've noticed that system works perfect when it is shut down with "Power Off" option.
After "full" shutdown I don't have high CPU load issue and CPU frequency at idle are as next:

alstorm@dolfin:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_cur_freq
800018
799999
800012
800002

The high CPU load issue comes back after either a "Reboot" or "Suspend" (eg closing lid of the laptop without Shut Down)
top doesn't blame any particular process for CPU load, but CPU frequencies stays maxed out.

alstorm@dolfin:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_cur_freq
3827087
3700219
3847067
3700253

Farther the issue stays present until "proper" Shut Down. And also require to wait some time before powering system back.
In case if Shut Down is followed with too soon Power On - high CPU load issue is still present.

---

