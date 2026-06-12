---
title: "what to do when ubuntu freezes or slows to a crawl?"
date: 2011-11-16
forum: New to Ubuntu
---

### Post by 118118 on 2011-11-16
often happens when playing music while surfing - facebook etc..

thanks for any assistance :)


oh i'm running a netbook :KS

---

### Post by ubudog on 2011-11-16
Hi there, does your browser freeze up?  After closing the browser, does the system restore to normal?

---

### Post by 118118 on 2011-11-17
hi,

yes the browser freezes but the pointer still moves about. i think. i can provide more details after it next happens. i assumed i was just overloading the hardware..?

---

### Post by prookie on 2011-11-17
Hi 118x2,

This looks like a shortage of memory to me.

I had a similar problem. My computer freeze when I started Ubuntu Software Center, when I had several tabs opened in Firefox, ... I had 512MB of memory.
After, I upgraded computer with 1GB of RAM to have 1.5GB total, and now everything is working fine. Ubuntu 11.10 with Unity is very thirsty for memory.

Can you provide me some details about your PC:
- processor type and speed,
- RAM memory installed,
- what Ubuntu version are you using.

pRookie

---

### Post by ubudog on 2011-11-17
+1 on providing specs... if you could post the output of:
```
free -m
``` 
that would be great.

---

### Post by 118118 on 2011-11-18
hi there,

yes i find software centre can be especially problematic. part of the reason i am using ubuntu though is that it seemed when i got this netbook [aspire 1, 1gb of ram, N450 (1.66 GHz. 512KB cache)] to run windows 7 quite a bit slower..?

```
free -m
             total       used       free     shared    buffers     cached
Mem:           991        870        120          0         21        520
-/+ buffers/cache:        329        662
Swap:            0          0          0

```:)


edit oh yes 11.10 unity. happy to downgrade to 2d or whatever that is??

---

### Post by realitykid on 2011-11-18
> **118118 said:**
> hi there,

yes i find software centre can be especially problematic. part of the reason i am using ubuntu though is that it seemed when i got this netbook [aspire 1, 1gb of ram, N450 (1.66 GHz. 512KB cache)] to run windows 7 quite a bit slower..?

```
free -m
             total       used       free     shared    buffers     cached
Mem:           991        870        120          0         21        520
-/+ buffers/cache:        329        662
Swap:            0          0          0

```:)


edit oh yes 11.10 unity. happy to downgrade to 2d or whatever that is??

My recommendation is to use Unity 2D and see if the problem persists there. Like everyone said, Unity 3D is hungry. While using it in 11.10, I'm already using about 1GB of 4GB with only a few firefox tabs open and rhythmbox playing music. So try 2D and see if that solves the issue.

---

### Post by prookie on 2011-11-18
You can choose Unity 2D from the menu positioned near right from the box where you type username and password.

Personally, I'm using Xfce from Xubuntu. And I'm much happier with this because my PC does not spill resources on looks. Applications run faster that way.

You can install Xubuntu in Unity from terminal:
apt-get install xubuntu-desktop

---

### Post by mike555 on 2011-11-18
I think you would like xubuntu better, but a clean install would be better..(instead of inside ubuntu ) I suggest trying a live xubuntu cd first and if you like it, then you can install it

---

### Post by prookie on 2011-11-18
> **mike555 said:**
> I think you would like xubuntu better, but a clean install would be better..(instead of inside ubuntu ) I suggest trying a live xubuntu cd first and if you like it, then you can install it

Mike, please can you tell me more what is an advantage of clean Xubuntu install?

My wish is to use Xcfe (as a light desktop manager) together with all advanced applications which Ubuntu offer (for example LibreOffice, LibreCAD, ). That's why I prefer Ubuntu install with later installation of xubuntu-desktop package.

I think that there is no difference between clean install and additional install of Xubuntu because they use the same kernel and common programs as layer to shells.
Am I right?

---

### Post by mike555 on 2011-11-19
Installing Xubuntu into ubuntu adds a bunch of xfce programs to your computer, many people have had trouble with that because programs tend to fight for control ........
 better to do a clean install and then install libreoffice etc. avoiding gnome and kde stuff....... if you use synaptic package manager it will tell you what it is installing so you can choose.

---

### Post by lolpenguin on 2011-11-20
If you have a old computer with lower hardware specs, Xfce, LXDE, Gnome Classic or Unity 2D are recommended. Unity (3D) and Gnome Shell are too power hungry for netbooks and old laptops (and really old desktops).

---

### Post by prookie on 2011-11-20
> **mike555 said:**
> Installing Xubuntu into ubuntu adds a bunch of xfce programs to your computer, many people have had trouble with that because programs tend to fight for control ........
 better to do a clean install and then install libreoffice etc. avoiding gnome and kde stuff....... if you use synaptic package manager it will tell you what it is installing so you can choose.

Thank you for comment Mike.

For now, I can say that my dual distribution installation with Ubuntu and Xubuntu is working fine on 10.04 LTS.
On the other hand, the installation on 11.10 is a bit unstable. But I suspect that crashes I've experienced have nothing with that. 11.10 is not well tested release, and new kernel integration 3.x.x (together with new Unity desktop) is causing a lot of faults.

I hardly wait next release. And then Xubuntu will be the only installation for me.

---

### Post by bigred1600 on 2011-11-20
Try adding gnome in the software centre.
Reboot and select Gnome classic (no effects) at logon.
Running 2 ageing laptops here happily on 11.10 this way.

---

### Post by prookie on 2011-11-21
> **bigred1600 said:**
> Try adding gnome in the software centre.
Reboot and select Gnome classic (no effects) at logon.
Running 2 ageing laptops here happily on 11.10 this way.

Thanks for the tip. I'll try to install it.
I have an option to use Gnome on 10.04 LTS and I like it. It would be much better than Unity if I would be able to install it on 11.10.

---

### Post by majedaly on 2011-11-21
In such events, I go to system > administration> system monitor, arrange processes by CPU usage, and kill the process which consumes most of the processing power (usually firefox because of the adobe plugin)!

If it is a complete freeze, i usually enable ctRl+Alt+BkspC to restart x.
Alternatively, I would ssh to the machine from another one, and request a reboot.

---

### Post by prookie on 2011-11-21
> **majedaly said:**
> If it is a complete freeze, i usually enable ctRl+Alt+BkspC to restart x.

My desktop managers (Unity, Xfce) on 11.10 are not freezed. They are crashed with "black screeon of death" showing some errors. After that I can only restart my computer on power button.

I've described an error 2 days ago on this forum:
[http://ubuntuforums.org/showthread.php?t=1883170](http://ubuntuforums.org/showthread.php?t=1883170)

I guess that problems of this kind I have to report to development team because nobody answers here.

---

### Post by 118118 on 2011-12-27
i am now using xubuntu - and aside from not crashing anymore, it definitely seems like an improvement.


tried lubuntu the other day but it didn't run my wlan thing "out of the box" or whatever. thanks :) !!

---

