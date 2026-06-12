---
title: "Kernel Panic"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by Da King on 2008-04-23
i have two OS's on my pc (XP & Ubuntu Gusty)..my pc suddenly went off yesterday (whiles on windows) after displaying a message just like when u get infected by a sasser virus that is the timing of 60secs untill it goes off. the big suprise is i have never connected my pc to an internet before and i have kaspersky antivirus on with manual update which is updated regularly and there was no flash drive inserted. well my pc restarted and windows codnt boot again cos it says it missing a file (fastfat) so it cant boot..so i went to the linux to boot up so i put in the missing file and i get an error
  > 121071] kernel panic-not syncing: Attempted to kill init!

i put in the ubuntu cd and i get the same message..now i take my hard disk and yet i get the same message, i try the ubntu 5.10 and same message..NOW WAT SHOD I DO.

---

### Post by Tatty on 2008-04-23
That doesnt sound very good.  Kernel panics are caused when the kernel receieves certain instructions that it cant process, usually because of data corruption somewhere along the line.

Since neither of your installed OS's are working and also no live CDs will boot, its possible that you may have some damaged hardware somewhere.  If this is the case then your ram is the most likely suspect - do you have any spare ram somewhere that you can try putting in your comp?

---

### Post by Da King on 2008-04-23
> **Tatty said:**
> That doesnt sound very good.  Kernel panics are caused when the kernel receieves certain instructions that it cant process, usually because of data corruption somewhere along the line.

Since neither of your installed OS's are working and also no live CDs will boot, its possible that you may have some damaged hardware somewhere.  If this is the case then your ram is the most likely suspect - do you have any spare ram somewhere that you can try putting in your comp?

I think u might be write, i remember i did a MEMTEST and i had errors showing up, i have 2 256mb memory so i guess i can easily take them out and see...another problem is gusty doesnt work on a 256mb ram and i dont have any spare ram at the mo..well i guess i wod try with the ver. 5.10..i will post u the results by moro when i come back to work..fanx a lot tho

---

### Post by Tatty on 2008-04-23
Good luck!  I hope its something simple/cheap to fix.

If you need more ideas of what to test have a browse through this page:

[http://www.thexlab.com/faqs/kernelpanics.html](http://www.thexlab.com/faqs/kernelpanics.html)

---

