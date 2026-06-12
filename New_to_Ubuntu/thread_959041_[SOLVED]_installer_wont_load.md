---
title: "[SOLVED] installer wont load?"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by DoubleMcLovin on 2008-10-26
I decided to put Ubuntu on some laptop I had laying around, theres nothing wrong with the laptop other then the fact that it has windows on it. So I decided, hey lets drop linux over it and maybe have a portable compy worth a crud. Well I drop in my install disk and it freezes after I hit the "Install Ubuntu" link, displaying about half of the background. I decided it must be cause of no support for this video card and get the alternative install disk, then I get a black screen after I click to install?

Laptop:
Toshiba Satellite M45 - S165  ATI graphics card (i understand theres a lot of issues with these?) Intel celeron M processor.

Maybe I could get some kind of install pack set up with the ati drivers?

---

### Post by eternalnewbee on 2008-10-26
Hi there. Very basic: Did you burn the cd at a very low speed?
Preferably speed 4.

---

### Post by DoubleMcLovin on 2008-10-26
No I didn't, wow can't believe I missed that on 2 tries lol. Im burning a new one at 4x now and we will see how this one goes.

---

### Post by DoubleMcLovin on 2008-10-26
burned at 4x speed, and when I booted same thing happened, but this time I noticed something that was happening all along, an error appeared for a brief second before the black screen:
 [4294672.157000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
I googled it and found that its solved by running as noacip mode, I did this and didnt get the error, but the same black screen came up =\

[COLOR="Red"]EDIT::

Solved![/COLOR] I played around with install parameters, and found that running noapic nolapic vga=771 solved my problem!

---

