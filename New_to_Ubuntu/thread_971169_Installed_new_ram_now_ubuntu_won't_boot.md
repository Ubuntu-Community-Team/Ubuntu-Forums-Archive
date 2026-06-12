---
title: "Installed new ram now ubuntu won't boot"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by djdarrin91 on 2008-11-04
I have a Dell Optiplex GX260. when i bought it 256MB of ram was installed so i took out the 256mb and installed 2 gigs(1 gigx2)and now i can't boot into ubuntu,it worked perfect with 256mb:( let me also add i did install a new LG dvd burner.computer says Bug: soft lockup-cpu#0 stuck for 11s! Hald Runner:6659. And i don't have a clue of what that means:? Is there anything i can do to fix this?

---

### Post by rustutzman on 2008-11-04
Disconnect the burner and try it. If it still won't boot plug the burner back in and put your 256 chips back in. Are you sure you got the right RAM?? Will it boot from the live cd??

Russ

---

### Post by Ocxic on 2008-11-04
try putting everything back to the way it was when it was working, that way you will know if it's something you added that is really causing the problem.

then install things one by one, it not uncommon to get bad ram even right out of the box, and make sure you ground yourself before working on anything, even a small shock from you can kill components. 

install the burner first, if everything is fine put in one of your RAM sticks, and see if it will boot, if not try the other one by itself, you may be surprised.

---

### Post by oilchangeguy on 2008-11-04
> **djdarrin91 said:**
> I have a Dell Optiplex GX260. when i bought it 256MB of ram was installed so i took out the 256mb and installed 2 gigs(1 gigx2)and now i can't boot into ubuntu,it worked perfect with 256mb:( let me also add i did install a new LG dvd burner.computer says Bug: soft lockup-cpu#0 stuck for 11s! Hald Runner:6659. And i don't have a clue of what that means:? Is there anything i can do to fix this?

are you sure you got the correct ram for your computer? ie. pc 2100, 2700, you get the idea.

---

### Post by Zzl1xndd on 2008-11-04
Just looking on the google and it looks like the GX260 maxes out at 1gig and can't handle sticks larger then 512MB

[http://www.virtualsystems.sk/sellout/Dell_Optiplex_GX260.pdf](http://www.virtualsystems.sk/sellout/Dell_Optiplex_GX260.pdf)

---

### Post by PierreDeKat on 2008-11-04
Is this new burner replacing a previous unit, or is it an additional unit? 

If it's replacing a previous unit, probably make sure the jumper on the back is set to the same setting as the unit you took out. If it's an additional unit, I'm guessing you will want to set one unit to "master" and one unit to "slave".

Otherwise, I've got a GX260 myself, and I'm running 2 gigs of RAM with no problems. So unless they're bad, or you didn't get them plugged in good, it almost has to be a glitch with the new burner.

---

### Post by oilchangeguy on 2008-11-04
> **tweakedenigma said:**
> Just looking on the Dell site and it looks like the GX260 maxes out at 1gig and can't handle sticks larger then 512MB

[http://www.virtualsystems.sk/sellout/Dell_Optiplex_GX260.pdf](http://www.virtualsystems.sk/sellout/Dell_Optiplex_GX260.pdf)

virtual systems is not the dell site. try this:
[http://support.dell.com/support/edocs/systems/opgx260/en/index.htm](http://support.dell.com/support/edocs/systems/opgx260/en/index.htm)
and it maxes out at 2gb!

---

### Post by djdarrin91 on 2008-11-04
Thanks to everyone for responding so quickly.I made sure to get the right ram and the burner i just installed today and its the only optical drive i have installed.the ram shows up in windows xp so i assume its installed correctly. I think im gonna try to disconnect to dvd burner first and check it again.i did buy the ram off of ebay so i wouldn't be too suprised if there was a problem with it but i can't gripe i only paid 36.00 for 2 gigs which was said to be new.once again thank you everyone for the help. i will post back asap.

---

### Post by djdarrin91 on 2008-11-04
Well everyone the ram was stalling ubuntu,i tried just 1 stick(gig)and still no go,i did try both sticks 1 at a time and nothing,installed the old 256 stick and it fired right up.the new ram is low density could that have anything to do with it?i really hope i can find a work around for this so i could use the new ram but im not too sure thats gonna happen:( I enjoy using ubuntu way more than windows but it looks like i may just have to use windows for now:-#:frown: if anyone has anymore ideas i would love to hear them.

---

### Post by djdarrin91 on 2008-11-05
Also the original ram is pc2100 and i bought pc3200,but i think that should be ok.The ram says its backwards compatable to pc2100.

---

### Post by oilchangeguy on 2008-11-05
> **djdarrin91 said:**
> Also the original ram is pc2100 and i bought pc3200,but i think that should be ok.

i'm suprised it works in windows. i don't think you can go higher than pc2700 in a machine that was designed for pc2100.

---

### Post by djdarrin91 on 2008-11-05
Did you use pc2100 ram in your machine?

---

### Post by Paqman on 2008-11-05
According to [the specs](http://support.dell.com/support/edocs/systems/opgx260/en/ug/specs.htm#1112456) you want PC-1600 or PC-2100 RAM.

---

### Post by djdarrin91 on 2008-11-06
but ubuntu does run on Virtual machine with the new ram installed,weird.but better than nothing.

---

