---
title: "Noise and fan heat. Drivers ?"
date: 2016-09-22
forum: New to Ubuntu
---

### Post by dragoncurt on 2016-09-22
Hi guys. I am pretty new to Ubuntu but I want to try it out. I have a laptop which is the Dell e6420. WIth the two GPU's IGPU and the Nvidia one. The thing is my laptop is very hot and I can also hear the fan on, when this in on windows 8.1 it does not make this much heat or noise when it is even running netflix in 1080p. 

Could I have an issue with the drivers ? If so is there any way I can fix it.



Thanks 

Curtis

---

### Post by mastablasta on 2016-09-23
are the nVidia drivers installed? is nVidia optimus (bumblebee project) installed ?

---

### Post by dragoncurt on 2016-09-27
I don't thin the nVidia driver are installed but I do have nVidia optimus in bios. What is bumblebee project. Thanks

---

### Post by mastablasta on 2016-09-28
bumblebee project is enabling switching between nVidia and intel GPU. you install nVidia drivers and then you can switch (manually). but i think nVidia is working toward getting optimus, at least partially supported, in linux.

Optimus is fully supported in Windows and it swtiches automatically. so when you do Office work it owuld use intel GPU and power dsavings, but when you start a game it owuld switch to nVidia GPU and draw extra power (means heat=the need for fans).

---

### Post by dragoncurt on 2016-09-30
Hi, I wanted to reply to you about talking about the bumblebee project. I think I have now got it to install and work. :) but does this do the same as windows would,Use the Igpu in not much needed states and then use Nvidia one when it needs to use the extra graphics power. Thanks for telling me about it.

---

