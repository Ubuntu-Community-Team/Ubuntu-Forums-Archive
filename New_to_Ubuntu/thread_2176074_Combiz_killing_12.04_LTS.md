---
title: "Combiz killing 12.04 LTS"
date: 2013-09-22
forum: New to Ubuntu
---

### Post by Dean_Tiernan on 2013-09-22
I am very new to Ubuntu and Linux took the plunge a few months back and added a Linux partition to an XP machine. Everything has gone well until the last few days, when Combiz is apparently not happy and keeps threatening to reboot unless I press continue. If left to its own devices the computer will reboot. It goes from a rapid pulsing so much that I can't keep up and "locks up" the desktop. Any help would be appreciated. I am not familiar with all the tools, have no fear of command line (I'm an old dos hack). But need a little hand with this one. this is what I get [https://www.facebook.com/photo.php?fbid=10151670230097921&l=8b5473d221](https://www.facebook.com/photo.php?fbid=10151670230097921&l=8b5473d221)

---

### Post by Old_Grey_Wolf on 2013-09-22
I assume you mean Compiz. If not ignore this.

You may need to reset Compiz to its default settings and reboot. To reset Compiz:
Press alt+F2
Enter this command ```
unity --reset
```
Reboot

---

### Post by whitesmith on 2013-09-22
Just out of curiosity, do this in a terminal: ```
top
``` and post back the the upper 10 lines. My 12.04 system was driven into constant 25-30% CPU utilization by Compiz and I had to revert to Gnome to regain lost performance. It was pretty but I value speed more than appearance.

---

### Post by Dean_Tiernan on 2013-09-23
[https://www.facebook.com/photo.php?fbid=10151673633377921&l=de8962dc11](https://www.facebook.com/photo.php?fbid=10151673633377921&l=de8962dc11)  This is an intermittent error message. In addition to the others. Will try suggestions thank you.

---

### Post by Dean_Tiernan on 2013-10-18
This worked, Thank you very much. An update brought the problem back, but this fix worked, Thank you.

---

### Post by Jonathan Precise on 2013-10-18
Please mark this thread as solved by going to thread tools.

---

