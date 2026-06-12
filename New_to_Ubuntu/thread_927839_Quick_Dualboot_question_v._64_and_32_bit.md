---
title: "Quick Dualboot question v. 64 and 32 bit"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by ranthal on 2008-09-23
Is it possible to setup a 64-bit Vista (business) and 32-bit Ubuntu (8.04) dualboot assuming hardware will support 64-bit?  Has anyone ever done this?

Background, not necessary to read:
Just built my first PC and have 32-bit 8.04 successfully installed and running stabley, still need to download some drivers but it's good.  I want to try moving over to 64-bit platforms an want to start with Vista since it is better supported by hardware and keep the stable 8.04 install.

Thanks

---

### Post by mikewhatever on 2008-09-23
Don't see why not. The two OSs are not interdependent, so there shouldn't be any problems.

---

### Post by ranthal on 2008-09-23
> **mikewhatever said:**
> Don't see why not. The two OSs are not interdependent, so there shouldn't be any problems.

Cool, just wasn't sure if it mattered to GRUB or maybe how the BIOS was configured so I'll give it a shot and update this thread as it goes.

---

### Post by howefield on 2008-09-23
I had that dual boot setup, only the other way round, 32 bit Vista with 64 Ubuntu, worked without any issues.

---

### Post by Joeb454 on 2008-09-23
> **howefield said:**
> I had that dual boot setup, only the other way round, 32 bit Vista with 64 Ubuntu, worked without any issues.

I had that but with XP (32 bit) thrown in there too. It works great

---

### Post by hyper_ch on 2008-09-23
why would you run 64bit windows and 32bit linux? I mean there's not much available for 64bit windows why just about everything works out of the box on 64bit linux.

---

### Post by rsambuca on 2008-09-23
> **hyper_ch said:**
> why would you run 64bit windows and 32bit linux? I mean there's not much available for 64bit windows why just about everything works out of the box on 64bit linux.

Is there a reason that you feel a need to criticize the OP rather than help and answer his/her questions?  You do this in numerous threads and posts.

---

### Post by Paqman on 2008-09-23
> **ranthal said:**
> I want to try moving over to 64-bit platforms an want to start with Vista since it is better supported by hardware and keep the stable 8.04 install.


Actually, i'd say Ubuntu has _much_ better 64-bit support. Adapting drivers for 64-bit Linux is (i'm told) much simpler than for Windows, so we've had good hardware support for ages. There used to be some issues with 3rd-party software like Flash, but that's been sorted.

Seriously, give 64-bit Ubuntu a go, I think you'll be pleasantly surprised.

---

### Post by hyper_ch on 2008-09-23
paqman: flash, java etc. works all fine on 64bit meanwhile. the only problem I encountered on Ibex (not on Hardy) is Skype but I posted a solution to it already.

---

### Post by Paqman on 2008-09-23
> **hyper_ch said:**
> paqman: flash, java etc. works all fine on 64bit meanwhile.

I know. Some folks persist in saying otherwise on this forum, but I suspect they're folks who haven't dabbled their toes in the 64-bit end of the pool for a couple of years.

---

### Post by hyper_ch on 2008-09-23
I actually ment to point this out to the TO and not to you Paqman ;)

---

### Post by howefield on 2008-09-23
> **hyper_ch said:**
> why would you run 64bit windows and 32bit linux? I mean there's not much available for 64bit windows why just about everything works out of the box on 64bit linux.

> **rsambuca said:**
> Is there a reason that you feel a need to criticize the OP rather than help and answer his/her questions?  You do this in numerous threads and posts.


You surely would have to be pretty thin skinned to see that as criticism, after all he did point out why he thought that, which may have helped the OP.

---

### Post by rsambuca on 2008-09-23
> **howefield said:**
> You surely would have to be pretty thin skinned to see that as criticism, after all he did point out why he thought that, which may have helped the OP.

It has nothing to do with the thickness of my skin.  It is just that this poster, although he helps more than most, will occassionally keep asking these rhetorical questions to posters without really helping them, to the point that it becomes harrassment.  Clearly that is not the case in this thread.

I over-reacted and apologize.  In any event, I shouldn't have posted the way I did either, as it was inappropriate.

---

### Post by ranthal on 2008-09-23
Hey guys been pretty busy all day so just thought I'd update after reading through all the posts.

So my end idea was 64-bit both Vista and Ubuntu so slowly upgrade as I feel my way around the new build.

Based on the feedback in this thread I think now I will probably do 32-bit Vista and 64-bit Ubuntu w/ the 32-bit libraries installed (had that setup on our lab server this summer and it was pretty sweet) so it should cover all my bases in terms of support.

What's a good iso image dvd burner program for Ubuntu?  I was checking out Nero Linux 3, any other suggestions?  (all Windows platforms I download come as iso images)

Trolling or whatever you want to call it, whatever as long as there's some decent input.

Thanks!

---

### Post by rsambuca on 2008-09-23
If you just need to burn an iso image from Ubuntu, you can just right click the iso file and burn it directly from the nautilus menu.

---

### Post by hyper_ch on 2008-09-23
k3b... it's a lot like nero - but Open Source :)

---

### Post by Joeb454 on 2008-09-23
What's wrong with brasero?

If you need a Windows .iso burning app, I use imgburn :)

---

