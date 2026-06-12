---
title: "Computer Turns on When Plugged In"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by Lazy-buntu on 2008-09-13
One of my family's computers has an oddity that has popped up recently.

The computer is plugged into a power strip, and when we turn the power strip on...the computer turns on without us pressing the power button.

They said they recently installed XP's service pack 3 update, but I doubt that has anything to do with the problem.

Any ideas?

---

### Post by iAtari on 2008-09-13
Hmm... 

No ideas, but my old Dell Dimension 4600 always does that.

---

### Post by Jack M. on 2008-09-13
There's a BIOS setting in many of Dell's computers that could be causing that. Press F2 during boot, then look for the "Auto power on" option (or something to that effect) and turn it off.

---

### Post by Lazy-buntu on 2008-09-13
It's an HP, but I checked the BIOS earlier. I don't think I saw a setting like that.

---

### Post by cariboo on 2008-09-13
Look in the power saving section of the bios, look for power-on.

Jim

---

### Post by Lazy-buntu on 2008-09-13
Maybe I didn't check the BIOS carefully enough. It looks most of the ideas are leading to that.

Thanks for the input =)

---

### Post by Jack M. on 2008-09-13
Since this has only started occuring recently, the only things that I can think of would either be that some sort of jumper on the motherboard got inadvertently switched somehow, or that Service Pack 3 is turning off the computer in an odd way...? Neither of those options seem very likely, though. Do you know the specific HP model? That might help to diagnose the problem.

---

### Post by Pogeymanz on 2008-09-13
I vote CMOS battery. You can buy another one for $3 US. I've seen some weird computer activity because of those things.

---

### Post by R_T_H on 2008-09-14
Just speculation, but I've seen such an occurrence on my Dell when I plug the ethernet cable in. I think it might be that plugging it in changes the case's potential and triggers the on switch.

---

### Post by Mornedhel on 2008-09-14
> **R_T_H said:**
> Just speculation, but I've seen such an occurrence on my Dell when I plug the ethernet cable in. I think it might be that plugging it in changes the case's potential and triggers the on switch.

You sure your Dell doesn't just have Wake-on-LAN ?

---

### Post by lisati on 2008-09-14
> **Lazy-buntu said:**
> It's an HP, but I checked the BIOS earlier. I don't think I saw a setting like that.

My Compaq machine (made by HP) has such a setting in BIOS, I think it's disguised as a "restart after a power failure"-type option.

---

### Post by Lazy-buntu on 2008-09-14
> **lisati said:**
> My Compaq machine (made by HP) has such a setting in BIOS, I think it's disguised as a "restart after a power failure"-type option.

I set that option to "stay off" before my first post, so I'm still not sure what to think.

---

### Post by Lazy-buntu on 2008-09-15
I just noticed that the setting I saved "stay off" after AC power failure, isn't staying saved.

I went back in to the BIOS, changed it again to "Stay Off" and saved/exited.

I power the computer back on and the setting reverted.

Bad CMOS battery? The clock isn't losing any time though.

---

### Post by Nicane on 2009-08-17
I know this is serious gravedigging here... BUT, I actually had this problem with someones motherboard/have seen this problem before. One is the CMOS battery, and by exchanging it, the problem was solved. But this is ONLY if it's the BIOS settings being wrong and causing it to boot up that way. If that is not the problem, it is a blown capacitor on the motherboard. I had, sadly, tried fixing a friends computer with this problem, and I knew it wasn't the CMOS battery. So I swapped motherboards and used all of her hardware (CPU, RAM, GFX, etc) and as I plugged it in, I saw a poor little capacitor pop and fry before my eyes. Then, amazingly, THAT motherboard had the same problem. I was pissed off, but I know what had happened to her motherboard. I'm looking at a faulty CPU, the PSU is fine, since I used a different one and it still died. So look at those to options, and be careful with the CPU I have. I am simply using common sense with figuring out what the problem is. Try the battery first. Of course, you might have already solved the problem in the past year or so. I apologize for this. But I thought my opinion might be worth a shot.

---

