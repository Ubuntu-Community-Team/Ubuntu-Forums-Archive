---
title: "Heat problem. ubuntu 11.10"
date: 2011-10-13
forum: New to Ubuntu
---

### Post by FimmFingur on 2011-10-13
Hi guys, i just installed ubuntu 11.10 and the fan in my computer is louder then usual and the warmth coming from it seems strange. any idea what it could be ?

i got
 Intel Core i3-2310M 2.1GHz  
if it has anything to do with it.

thank you

---

### Post by FimmFingur on 2011-10-13
my CPU is at 63°c and all I'm doing is browse the web.

---

### Post by sammiev on 2011-10-13
Shut off your computer for 1 min and try it again. I had one do the same now and then.

---

### Post by Benjamin1987 on 2011-10-13
If you have another graphical card in your laptop it might use that one instead of the igp of the processor. If it uses the other gpu (card) it is also possible that the laptop fan is running faster. I have for instance an asus with the same proc as you have (i3-2310m) but also a Geforce gt520m. If it uses the geforce it gets hotter as well.

---

### Post by FimmFingur on 2011-10-14
Thanks, I just turned it off for the night and it seems to be better.

All i got is 
              Intel HD Graphics 3000 Dynamic Video Memory Technology.

---

### Post by FimmFingur on 2011-10-14
i seem to be wrong, i started a flash game and the fan turned really loud and it got very hot again.

This didn't happen in 11.04.

Would you guys reccomend going back to 11.04 for a while or is this OK for my computer ?

---

### Post by sadaruwan12 on 2011-10-14
The heat factor actually the users have to monitor that have to get and idea of that so better keep on monitoring your CPU temp.

Well I'm using a same type of a proc along with 11.10 I don't think it has gotten any hotter.

---

### Post by FimmFingur on 2011-10-14
It's at 75°c while running the flash game

---

### Post by Sicnarf on 2011-10-14
11.04 used to do that to my laptop as well even if I was just using the Intel Graphics Video Card. My fan was loud. I've just installed 11.10 so I haven't really noticed if it is also using up unusual CPU power to make my laptop hot. Perhaps I'll give an update on this thread after awhile.

---

### Post by Johnb0y on 2011-10-14
try flashing/re-setting default on the BIOS, had the same issue with a dell optiplex. flashed and all was good! 

did also have a custom build that required a complete upgrade of the BIOS, turned out to even better than before.

hope that helps.

---

### Post by varunendra on 2011-10-14
I think there can be a bunch of possibilities, and more than one of them may exist in a given setup.

Firstly, if you use Adobe's flash plugin, it has a long history of resource over-usage on Linux, although I'm not sure of its current status. Secondly, I've seen some experts saying that Linux kernel (in fact, the CPU driver-modules in it) is not yet able to handle Sandy-Bridge processors properly. Again, I'm not sure what all they mean by this. Another possibility is that it may be some background application that is keeping the CPU on toes (Unity? Compiz?...??). To verify this, you may use top command to see which process is using the CPU abnormally.

As for holding back to 11.04, there is nothing wrong with the idea if it suits you. Newer releases are most often buggy and are more inclined towards testing rather than offering a stable overall performance. In fact, for those who are not so enthusiastic about trying out the latest, and rather like stability in their system, it is always recommended to use the latest LTS release (which currently is 10.04).

---

### Post by Sicnarf on 2011-10-14
I think it might also have something to do with these:

[http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html](http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html)

[http://www.phoronix.com/scan.php?page=news_item&px=OTg5Mg](http://www.phoronix.com/scan.php?page=news_item&px=OTg5Mg)

---

### Post by Dark Shinobi on 2011-10-24
I believe I read that the Linux 3.0 kernel (which is in 11.10) consumes much more power than the old kernel. More power = more electricity which = hotter. I have also noticed that unity takes up more resources so that could be another reason. You can go here [http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html](http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html) to do a simple edit to the GRUB load options that may help. Good luck

[I]Edit

[/I]Ok gave the fix a try and my cpu temp is down to 44C so the fix definately works.

---

