---
title: "problem after downloading chrome in firefox"
date: 2013-11-01
forum: New to Ubuntu
---

### Post by albaqui on 2013-11-01
Hi

I have problem after downloading chrome in firefox. I can't start computer rather blinks showing" Starting CUPS ....." Please help me.

---

### Post by Frogs Hair on 2013-11-01
HI [COLOR=#000000]albaqui: 

Cups in Linux usually refers to printing and I don't how this ties into a problem  with a Firefox download .  Can you provide anymore information ?   

 [/COLOR][http://en.wikipedia.org/wiki/CUPS](http://en.wikipedia.org/wiki/CUPS)

---

### Post by albaqui on 2013-11-01
hi

I firefox. I downloaded and started installing chrome. Finally asked me to restart. I did. Then it failed to open rather blinking showing
 
"battery state...
Starting CUPS .."

---

### Post by Frogs Hair on 2013-11-01
Chrome doesn't require restart when installed or at least never has when I have installed it . Were there Ubuntu updates installed as well.

---

### Post by albaqui on 2013-11-01
I see. It may be updates. In fact I downloaded chrome, then went to updates. then clicked chrome updates. you may be right. I want as it was. But Crome is preferable.

---

### Post by deadflowr on 2013-11-01
> **albaqui said:**
> I see. It may be updates. In fact I downloaded chrome, then went to updates. then clicked chrome updates. you may be right. I want as it was. But Crome is preferable.

Clicked on Chrome updates?
By default when running updates, all updates are set to install.
When you click on one it should unset them or uncheck them to not install.
Leaving the rest to install.

If you did this you it's possible that a newer kernel was installed(a restart usually happens when this occurs)
In which case, you might be able to get into a working system if you try an older kernel.

To do so, when you boot the Computer, at the section after the Computers BIOS screen is when the GRUB loads.
If Ubuntu is the only system then it would be hidden.
To access GRUB when the screen starts to switch from the BIOS screen(the first screen that shows right when you turn on the computer) hold/or tap the shift key until the message grub loading appears.(I think it's hold the shift, but can't remember exactly)
When GRUB loads it will list a few option, the top being Ubuntu, then there should be a section called previous versions.
Click on previous versions and hit enter.
Then selection the top entry. This is the last kernel version you used.
Hit enter and see what happens.

---

### Post by albaqui on 2013-11-01
Thanks. Now it shows,

Ubuntu,with Linux 3.2-39-generic -pae
Ubuntu,with Linux 3.2-39-generic -pae (Recovery mode)
Previous Linux version

Which one to hit?

---

### Post by albaqui on 2013-11-01
i hit previous linux version. But it did not resolve

---

### Post by deadflowr on 2013-11-01
> **albaqui said:**
> i hit previous linux version. But it did not resolve

What do you mean "did not resolve"?

When you clicked on previous versions did it open up more listings?
Or was the screen blank, or something similar.

Or did it give a listing, from which you then tried to select an entry, but it did the same thing like before?

---

### Post by albaqui on 2013-11-02
when i clicked previous linux version it started blinking showing 'cups.............

---

