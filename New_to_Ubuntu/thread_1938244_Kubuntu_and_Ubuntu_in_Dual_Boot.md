---
title: "Kubuntu and Ubuntu in Dual Boot"
date: 2012-03-09
forum: New to Ubuntu
---

### Post by freshminted on 2012-03-09
After certain 'problems' with Kubuntu 11.10, I decided to see if they appeared in Ubuntu 11'10 which I set up as dual boot. Ubuntu did not have the conflicts and now I want to remove Kubuntu and use the space for the Ubuntu partition. 
A. How do I identify which partition holds Kubuntu ? (Loaded first would seem to be SDA 1)
B. If I merely remove Kubuntu, will it adversely effect the booting of Ubuntu?
C. Suggestions I simply overwrite the whole disc are unacceptable as I shall lose key links within Thunderbird which I cannot recreate.
D. Any suggestions should bear in mind that I am looking for simple, preferably not too technical advice.

Help would be gratefully received and acknowledged.:P

---

### Post by androssofer on 2012-03-09
> **freshminted said:**
> After certain 'problems' with Kubuntu 11.10, I decided to see if they appeared in Ubuntu 11'10 which I set up as dual boot. Ubuntu did not have the conflicts and now I want to remove Kubuntu and use the space for the Ubuntu partition. 
A. How do I identify which partition holds Kubuntu ? (Loaded first would seem to be SDA 1)
B. If I merely remove Kubuntu, will it adversely effect the booting of Ubuntu?
C. Suggestions I simply overwrite the whole disc are unacceptable as I shall lose key links within Thunderbird which I cannot recreate.
D. Any suggestions should bear in mind that I am looking for simple, preferably not too technical advice.

Help would be gratefully received and acknowledged.:P

not sure about how to know for definite which partition is which. But i would back up your /home directory (should backup your thunderbird stuff) then fire up the live cd/usb and open gparted. Then simply delete the kubuntu partition and and then resize the ubuntu one to fill the gap. 

on the gparted it gives you a bar representing your hard drive. the kubuntu partition will probably be the 1 on the left. then the ubuntu parititon, then swap space on the far right. (as a guess, your experience may vary :-p )

i've done this before when deleting windows and it worked fine. grub remembers which partition to boot ubuntu from and its name wont change when your resize. Then run a grub refresh when you boot into ubuntu and it will clean away the kubuntu option for you. :-)

**note: ** the resize could mess up and lose all your data. has never happened to me, but you never know.

---

### Post by oldos2er on 2012-03-09
If you run the bootinfo script ([http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)) and copy and paste the results here, we can help you determine what exactly needs to be done.

---

