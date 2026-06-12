---
title: "[SOLVED] Stuttering ubuntu with some internet trafic."
date: 2008-07-03
forum: New to Ubuntu
---

### Post by Frenske on 2008-07-03
Recently I have upgraded to Hardy Heron and quiet like it. However, when there is fair amount of downloading (for example, surfing this forum and downloading synaptic packages) the computer stutters and CPU usage goes up all the way. This is quiet annoying since I quiet often listen to music on the computer while surfing the internet but a choppy Buena Vista Social Club turns into some kind of 1990s hardcore techno.
First I thought it was the new firefox, but after trying opera and experience the problem during an upgrade, it is clear that any connection to the web causes problems.
Is there a way to avoid the stuttering and capping the effect internet traffic has on the computer resources.


Spec: Dell 2.6GHz 1GB P4 with wireless broadband.

---

### Post by sayakb on 2008-07-03
While the usage goes up to 100%, post the output of the following command here:
```
top
```

Of if you like it colorful, post output of:
```
htop
```

---

### Post by Frenske on 2008-07-03
No idea how to post things like that. No help in the help either.

Well this should do:

[img]http://frenske.zenfolio.com/img/v2/p398881028-4.jpg[/img]

---

### Post by Frenske on 2008-07-03
Well that is not really at the moment the internet is at 100%. :confused:
However, when I selected in htop the memory usage a lot of applications/commands have multiple PID. Firefox has 8 entries. Furthermore it shows that 400MB of 1000MB is used. Which strikes me as way too much for just running ubuntu, firefox and a terminal.

---

### Post by sayakb on 2008-07-03
Firefox uses up more memory as more tabs you open. At a terminal:
```
killall firefox
```
And then start firefox again. The screenshot doesn't seem to help much. Try disabling compiz and see if this persists: Goto System->Preferences->Appearance. Click on **Visual Effects** tab and click None.

---

### Post by Frenske on 2008-07-03
I have tried that before and it did not help. I did killall firefox. Restarted firefox no tabs.
When I look into htop, there are 7 firefox PID all using 4.9% memory and there are various other applications with multiple PIDs. Is this normal?

---

### Post by whitethorn on 2008-07-03
> **Frenske said:**
> Recently I have upgraded to Hardy Heron and quiet like it. However, when there is fair amount of downloading (for example, surfing this forum and downloading synaptic packages) the computer stutters and CPU usage goes up all the way. This is quiet annoying since I quiet often listen to music on the computer while surfing the internet but a choppy Buena Vista Social Club turns into some kind of 1990s hardcore techno.
First I thought it was the new firefox, but after trying opera and experience the problem during an upgrade, it is clear that any connection to the web causes problems.
Is there a way to avoid the stuttering and capping the effect internet traffic has on the computer resources.


Spec: Dell 2.6GHz 1GB P4 with wireless broadband.

Hi I had the same problem, just copy this into a terminal

sudo /etc/init.d/alsa-utils reset

it worked for me.

---

### Post by Frenske on 2008-07-04
To whiteborn. Thanks for the try, but it did not do much!

Can anybody tell if it is normal to have multiple PID for the same application/commond? When I killed one PID of Firefox they all disappeared.

---

### Post by nowshining on 2008-07-04
P4's have an issue with going up to 100% on just about every little thing :D

- u can also try going into  ur bios and disabling HT - hyperthreading if need be and if it's enabled and ur P4 has it, and try again.

or 

close out all apps, logout and back-in.

if all probs presist, u  can try compiling a newer non-patched from ubuntu kernel from kernel.org, the latest that worked for on GG was 2.6.24.7. :)

it's quite easy to do so, if probs persist with a newer non-ubuntu-patched kernel, then it may be a problem with the ubuntu-kernel that is patched by ubuntu.

Again tho - P4's goes to a high CPU % at just about every little thing. :P However compared to windows - it's still useable a lot of the times - i'd say about 75% of the time and the 25% it gets frozen to where the mouse won't move and sometimes a ctrl|+alt+backspace is needed. :)

---

### Post by Frenske on 2008-07-05
No HT on my computer. As a matter of fact, my machine is dual boot. I did some tests with XP. Surfing the internet, while playing songs on iTunes AND running 2D finite-difference time-domain models using Matlab (quiet heavy forward modelling calculations). Guess what: no stuttering at all, iTunes keeps playing the songs smooth and no choppy mouse movements.

I believe that the internet is faster when using Firefox 2.
I keep XP solely for Matlab and the odd games, but I would like to use Ubuntu as my default OS. But it is driving me nuts. Is Ubuntu 8.10 so much more demanding than XP or Ubuntu 7.10.

---

### Post by nowshining on 2008-07-05
did you try running Matlab and the odd games on WINE? winehq.org.

as for the more demanding part - yes I believe so, so i've heard/read. :)

---

### Post by Frenske on 2008-07-22
Apparently it had something to do with the drivers. Installed RT73 drivers from grease monkey and I achieve 10% higher download speed than in Windows (same hardware).
Ridiculous that something like that affects your computing experience so much and I am still bazzled on the fact that the old driver was working sometimes. You would think software would work fine or would not work at alll but not a little bit.

Woohoo!

---

