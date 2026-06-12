---
title: "new build -- xp/kubuntu hardware question"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by badperson on 2008-09-19
Hi,

I have a new build (love it) with xp and kubuntu. 
It's an amd dual quad core machine. 

I have two HD's, they are both detected in bios, but neither xp or kubuntu sees the second one. 

The other problem is that I can't seem to get any audio. I have a creative audigy sound blaster card that xp detects, but when I play a cd and try plugging headphones into the various jacks on the back, I don't get any sound. Same thing in kubuntu. 

any ideas?
thanks, 
bp

---

### Post by aeiah on 2008-09-19
well these are two different problems. what is your 2nd hard drive like? is it formatted? is it enabled in bios? when you say 'it isnt seen in kubuntu' do you mean it isnt mounted or do you mean if isnt even visible in /dev/ ?

---

### Post by badperson on 2008-09-19
Hi,

the two drives are identical. The second is not formatted...I thought I'd be able to do that with the OS installed. 

I do not believe it's visible in /dev but I'll need to check; I'm used to gnome and just getting used to finding my way around kde. 
thanks
bp

---

### Post by waspbr on 2008-09-19
well, what I would do would be to download gparted in synaptic, and run it to check if it is there.

alternatively you could check by inputting the following into terminal

```
sudo fdisk -l
```

if everything fails, then I reckon it may be a jumper problem, just double check it the master/slave jumpers are set correctly

---

### Post by rustutzman on 2008-09-19
For XP go into Disk Management and see if the drive is listed there. If it is you can format it there and then XP will list it in Windows Explorer. 

Russ

---

### Post by badperson on 2008-09-19
great, thanks for the replies!
bp

---

