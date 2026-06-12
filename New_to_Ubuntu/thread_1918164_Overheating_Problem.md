---
title: "Overheating Problem"
date: 2012-01-31
forum: New to Ubuntu
---

### Post by tkabir11 on 2012-01-31
I have a HP Pavilion G60 Laptop- with Intel Dual Core 1.66GHz CPU, 1GB RAM and integrated Intel graphics. Currently I'm running Ubuntu 11.10; Kernel 3.0.0-15-generic. 
The problem: Laptop is overheating at all times- even when doing nothing. CPU usage is normal; but laptop cooling fan is running fast at all times. Although- there is absolutely no lag/slowness when I use Ubuntu- everything runs/moves/drags/drops/transfers smoothly. 
I've had this problem even when I was on Vista- but the system was really slow as well- which was the reason I had to ditch Windows and move to Ubuntu. So is there anything I can do to prevent my laptop fan running so wildly and overheating so much and so often for reasons I cannot figure out?? 
Here's a shot of my System Monitor at the moment, if that helps:

**_[http://s18.postimage.org/65aheih49/System_Monitor_006.png](http://s18.postimage.org/65aheih49/System_Monitor_006.png)_**

---

### Post by rgreener25 on 2012-01-31
If it happened with windows aswell that is a hardware issue you would get a better answer asking on a hp forum

---

### Post by S2UIRR3L on 2012-01-31
#1 - Did your laptop do this when it was brand new, or did it gradually happen as you were using Vista?
#2 - Have you in any way tried altering the temperature and CPU fan speeds in your BIOS?
#3 - Have you cleaned out the air ways (like with a can of compressed air)?
#4 - Have you ever separated the heat sink from the processor chip?
#5 - If you're computer is really old, you might need to "grease" it up with some new heat exchange grease between the CPU processor and heat sink that sits on top of it.

I did that for a friend's Toshiba laptop. He was running XP on it and over time, it would start over heating really bad and shut off without warning (as if you pulled the plug on it). We took it apart, cleaned out the air ways, wiped off the heat sink and applied some new heat exchange grease and double checked the BIOS settings. He was going to give it to his daughter if we fixed it, or buy her a new one if we couldn't. So we decided to try and repair it before anything. After all that, the computer lasted her for about a year before she spilled soda in it. Needless to say, she saved up for a newer one in that time, so they just recycled it.

MORAL OF THE STORY

If you're good with your hands, try looking at all the above, as well as the great advice that rgreener25 suggested (contacting HP for more in depth advice, if it is indeed a hardware issue). Best wishes with the laptop!

-Leo

---

### Post by tkabir11 on 2012-02-01
> **S2UIRR3L said:**
> #1 - Did your laptop do this when it was brand new, or did it gradually happen as you were using Vista?
#2 - Have you in any way tried altering the temperature and CPU fan speeds in your BIOS?
#3 - Have you cleaned out the air ways (like with a can of compressed air)?
#4 - Have you ever separated the heat sink from the processor chip?
#5 - If you're computer is really old, you might need to "grease" it up with some new heat exchange grease between the CPU processor and heat sink that sits on top of it.

I did that for a friend's Toshiba laptop. He was running XP on it and over time, it would start over heating really bad and shut off without warning (as if you pulled the plug on it). We took it apart, cleaned out the air ways, wiped off the heat sink and applied some new heat exchange grease and double checked the BIOS settings. He was going to give it to his daughter if we fixed it, or buy her a new one if we couldn't. So we decided to try and repair it before anything. After all that, the computer lasted her for about a year before she spilled soda in it. Needless to say, she saved up for a newer one in that time, so they just recycled it.

MORAL OF THE STORY

If you're good with your hands, try looking at all the above, as well as the great advice that rgreener25 suggested (contacting HP for more in depth advice, if it is indeed a hardware issue). Best wishes with the laptop!

-Leo

Thanks for the great advice. I must say that the overheating never occurred when brand new- it came about gradually- after about a year or so. I've been using this laptop for over 2 years now. I have been ignoring this issue for a long time now- mainly blaming it on Vista using up so much RAM and hence thinking that's the reason for overheating and slowness. But since I still have the overheating problem with Ubuntu- I can say for sure now that it's mainly got to do with my laptop's cooling fan being clogged up with dust and would also need to grease up between the cpu and heat sink as you've suggested. I've never done any sort of internal cleaning up/greasing; I did see a video tutorial on how to take apart my laptop for these purposes- but it looks like i don't have the guts to do that- it does seem a lot of work- and above all risky. Do you think cleaning out the airways with compressed air from outside the air-vents would be enough to remove the dust?...without needing to disassemble the laptop?

---

### Post by Mark Phelps on 2012-02-01
> **tkabir11 said:**
> Do you think cleaning out the airways with compressed air from outside the air-vents would be enough to remove the dust?...without needing to disassemble the laptop?

Only way to know is to try it --but yes, this generally helps a lot.

Wouldn't mess with the CPU.  You generally have to completely disassemble the laptop to do that, and there's no guarantee that after you're done, it will actually run any cooler.

---

### Post by S2UIRR3L on 2012-02-03
As Mark Phelps says (and I failed miserably to mention)...
Taking apart the laptop and breaking the seal between the CPU and the heat sink is the LAST resort and should only be done by someone who know exactly what they're doing.

As for the compressed air in the vents and the cooling fan...
You'll want to blow the air in reverse first, then blow it out in the proper directions. Usually the intake is on the bottom (the exhaust out the side). Blow air first into the side and let all the dust fall out of the bottom... Then, blow the fans(s) out second so the dust flies out the sides.

Just try to keep the can strait up. You don't want any of the liquid coming out of the straw. And when blowing the vents/fans out, it's not a bad idea to stand the laptop up on it's side (like an open book) and keeping your hand on it to make sure it won't blow over (some cans of air have a LOT of pressure lol).

I wish you the best and hope everything works!

---

### Post by tkabir11 on 2012-02-03
Thanks for all the advice guys. I'll try with the compressed air can and see if I can reduce the overheating.

---

### Post by nipunshakya on 2012-02-03
Hi. I would like to ask you how your battery is working? Sometimes, batteries are also a great promoter of heat in laptops...

Regards,WinuxUser

---

### Post by tkabir11 on 2012-02-03
> **WinuxUser said:**
> Hi. I would like to ask you how your battery is working? Sometimes, batteries are also a great promoter of heat in laptops...

Regards,WinuxUser

Ahaa- good question. I do have an issue with the battery too; I didn't bring it up here cos I thought the two issues weren't related. 
For the past few months I've had this issue where after I run my laptop on battery power for a while then plug the AC chord back in again- the battery wouldn't start charging up right away, most of the times it charges up only when the laptop is turned off or during standby. And also- power management gives me a notification saying that my battery has only forty-something percent capacity; so it needs replacing- contact your manufacturer and so on.

---

### Post by nipunshakya on 2012-02-03
mate..seriously, its time to throw your battery and buy a new one.. be advised, do as i said and you wont regret....automatically your laptop will perform at normal temperature...
Im sayin u so coz i have had the same issue regarding battery...and same problem of heating...changing the battery did it all fine....

---

### Post by d4m1r on 2012-02-03
I know those laptops and I'm sorry to tell you they are very cheap and underpowered, I can't imagine running Vista or Windows 7 on it...Although I would recommend atleast 2GB of ram for the newer versions of Ubuntu, it shouldn't be overheating trying to run it...

Google "HP modelhere overheating" and I'm sure you'll get a bunch of relevant information.

---

### Post by nipunshakya on 2012-02-03
^^ mate, it surely is his battery problem

---

### Post by |{urse on 2012-02-03
I find that a lot of battery issues occur due to overheating issues.

And if you do end up needing to disassemble the laptop download a disassembly manual first, most every laptop has one or there is a complete pictoral teardown already online somewhere.

 Get a white sheet of paper to set screws on as you remove them and draw circles around the screws in  manner which will help you remember where they each came from.

If you do reseat the cpu or heatsink (or both) remember that one fleck of dust or bubble caught in the middle of your thermal compound or pad can cause a whole new set of overheating issues.

In other words, only do this as a last resort to resolve an overheating issue. 

If there are screws left over, you did it wrong.

---

### Post by S2UIRR3L on 2012-02-04
What ever you try (and this is just my personal opinion)... Try the easiest/cheapest first.

If all you did was open it your self and tinker with some easy/cheap stuff first and this works and the laptop is repaired, you didn't spend anything.

If everything you've tried failed and you need to spend some money and have someone else repair it, it's not like you've spent a bunch of money lol.

Again... I wish you the best!

---

