---
title: "Shutdown"
date: 2012-08-26
forum: New to Ubuntu
---

### Post by Penfold1971 on 2012-08-26
I have my Ubuntu (12.04) machine running headless, and have acquired several Terminal commands that enable me to do what I want via ssh from both my Intel iMac and G4 PowerBook. The Ubu machine is dedicated to running Folding@home - and only that.

I used the command
```
sudo shutdown -h now
```
yesterday.

What, if any, advantage would there be in using the command
```
sudo shutdown -P now
```
?

---

### Post by androssofer on 2012-08-26
> **Penfold1971 said:**
> I have my Ubuntu (12.04) machine running headless, and have acquired several Terminal commands that enable me to do what I want via ssh from both my Intel iMac and G4 PowerBook. The Ubu machine is dedicated to running Folding@home - and only that.

I used the command
```
sudo shutdown -h now
```
yesterday.

What, if any, advantage would there be in using the command
```
sudo shutdown -P now
```
?

-H requests the system be Halted after it is brought down..

-P requests the system be powered down after it is brought down.

-h does either Halt or Power off. The choice is left to the system. 

So it would appear that with -h you let the system choose which is best. -P you are forcing it to Power off..


note: I have no idea what the difference between Power off and Halt. Perhaps someone else can help with that. I always use -h and trust the system to choose right..

---

### Post by cryptotheslow on 2012-08-26
On one of my systems using the -h option results in all processes being terminated and disks unmounted etc. just as you would see on any other shutdown. Only thing is it doesn't power off,  just stops and unloads everything ending up at a completely unresponsive black screen. Then have to use the power button to actually power down.

That is a "halt" I suppose.

---

### Post by Paqman on 2012-08-26
> **cryptotheslow said:**
> On one of my systems using the -h option results in all processes being terminated and disks unmounted etc. just as you would see on any other shutdown. Only thing is it doesn't power off,  just stops and unloads everything ending up at a completely unresponsive black screen. Then have to use the power button to actually power down.

That is a "halt" I suppose.

noacpi?

---

### Post by cryptotheslow on 2012-08-26
Quite possibly - I've not bothered troubleshooting it as it's a server that is generally on the whole time.

It's running on a little Intel Atom board (D425KT), maybe that's what makes the difference. :confused:

---

### Post by Penfold1971 on 2012-08-26
> **androssofer said:**
> -H requests the system be Halted after it is brought down..

-P requests the system be powered down after it is brought down.

-h does either Halt or Power off. The choice is left to the system. 

So it would appear that with -h you let the system choose which is best. -P you are forcing it to Power off..


note: I have no idea what the difference between Power off and Halt. Perhaps someone else can help with that. I always use -h and trust the system to choose right..

Thanks. I found that list earlier. Perhaps I should have been a little less vague :smile:

I'm interested in this notion that the system 'chooses'. In my case the system 'chose' to put the whole thing to bed - when I went to check, the machine was indeed 'shut down' as I would describe it in layman's terms. The power light on the case was off.

I clearly have no need, it seems to use the -P alternative. But why? What makes my system 'chose' as it does?

This is pure curiosity, nothing more.

---

### Post by hypnot0ad on 2012-08-26
> **Penfold1971 said:**
> Thanks. I found that list earlier. Perhaps I should have been a little less vague :smile:

I'm interested in this notion that the system 'chooses'. In my case the system 'chose' to put the whole thing to bed - when I went to check, the machine was indeed 'shut down' as I would describe it in layman's terms. The power light on the case was off.

I clearly have no need, it seems to use the -P alternative. But why? What makes my system 'chose' as it does?

This is pure curiosity, nothing more.

I always shutdown like this and yes it brings everything to a halt.
Everything is off.

I'm sure when the system 'chooses' its possibly doing checks on the system, deciding what kind of shutdown it does.

---

### Post by Penfold1971 on 2012-08-26
OK. Thanks everybody. Curiosity satisfied.

---

