---
title: "Ubuntu goes from smooth to laggy after some minutes."
date: 2018-06-11
forum: New to Ubuntu
---

### Post by ilumizionist on 2018-06-11
I have installed Ubuntu 18.04 on a new Intel NUC7PJYH. I has an [COLOR=#464646][FONT=inherit]1.5 GHz Intel Pentium J5005 Quad-Core, Intel Graphics 605 and 8GB of Ram.

When I turn it on everything is smooth and nice but after a while, dragging the windows around it starts to lag and opening apps takes a while. Same when browsing using Vivaldi, Firefox or Chrome. When scrolling or opening new tabs it goes slow. If I try to play a 1080p video on YouTube the system starts lagging like crazy. If I try to have 2 videos playing it pretty much freezes.

This problem is not limited to Ubuntu, I also tried Solus Budgie(it also lags but as much as Ubuntu), Linux Mint and KDE Neon pretty much the same thing. The only place where it does not lag is when using Windows 10. In Windows with multiple windows/videos opened it runs rather smooth. I don't want to use Windows on this machine so please help :D.

The machine is rather new, could it be a driver issue? When I go in Ubuntu in system info it shows the system and all the components. If I check the driver tab, it doesn't find any additional drivers. Also Wi-fi isn't working properly, it works but I top out at 500KB, I have to use an USB Wi-fi dongle.

Do you guys have any suggestions? Thanks, I really like Ubuntu![/FONT][/COLOR]

---

### Post by mrdc76 on 2018-06-12
This might be too obvious, but have you checked if you have any ongoing processes that steal cpu-time? (Not counting the ones you are intentionally running.)

---

### Post by PaulW2U on 2018-06-12
> **mrdc76 said:**
> but have you checked if you have any ongoing processes that steal cpu-time?
That would be something that I would also check if I had the same issue.

@ilumizionist, if, in a terminal, you run top or if you have it installed htop do you see any processes that are taking much much more than their fair share of CPU time?

---

### Post by ilumizionist on 2018-06-12
Hey thanks for the replies! There doesn't seem to be anything that hangs the CPU. When using htop and going from fullscreen on a youtube video, I see the CPU is at 133%? :D In this case the computer is really struggling with everything else.
[https://imgur.com/a/3ZrtwVL](https://imgur.com/a/3ZrtwVL)
[IMG]https://imgur.com/a/3ZrtwVL[/IMG]

In normal usage with no video running in the background it's rather...normal(check second picture), it only lags from time to time
[https://imgur.com/NNjD2lZ](https://imgur.com/NNjD2lZ)

Edit: I didn't insert the images here directly because they are 1440p and they look too big :D

---

### Post by mrdc76 on 2018-06-12
It's at 133% because your cpu has multiple cores. If this confuses you, go to System Monitor preferences, select the "Processes" tab and enable "Divide CPU usage by CPU count".

---

### Post by mc4man on 2018-06-12
Maybe take a glance thru here, at least regarding wifi
[https://communities.intel.com/community/tech/nuc/content?filterID=contentstatus%5Bpublished%5D~category%5B02-nuc7cjyh-nuc7pjyh-nuc7cjysal%5D](https://communities.intel.com/community/tech/nuc/content?filterID=contentstatus%5Bpublished%5D~category%5B02-nuc7cjyh-nuc7pjyh-nuc7cjysal%5D)
(- ex. wifi apparently supported in 4.16 kernel? [https://communities.intel.com/thread/124666](https://communities.intel.com/thread/124666)

If you go to Settings > Details what does it report for Graphics? 
(- or install inxi & go 
inxi -Gn

---

### Post by ilumizionist on 2018-06-13
Thanks, I will go ahead and update the Kernel, found some good tutorial online.

Here is what inxi says:
[IMG]https://i.imgur.com/2HJsQtp.png[/IMG]

---

