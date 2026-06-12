---
title: "ATI Graphics help?"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by Empyreon on 2011-10-14
Hello ubuntu world, i am a complete noob so please be nice :). 
I am having truobles with my ATI graphics, it may be because i have two graphics cards? i dont know. i noticed the problems when playing wii games and using youtube how everything is slow as f***. my computer works fairly well on windows 7, in terms of speed. this is a HP Pavillion dv6-3064ca and i am using Natty 11.04.

$ lspci -nn | grep VGA
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc M880G [Mobility Radeon HD 4200] [1002:9712]
02:00.0 VGA compatible controller [0300]: ATI Technologies Inc Redwood [Radeon HD 5600 Series] [1002:68c1] (rev ff)

---

### Post by collisionystm on 2011-10-14
sudo apt-get install fglrx

---

### Post by razorxpress on 2011-10-14
If fglrx does not work, See [Ubuntu Natty Installation Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide"). Since you have ATI/ATI dual that might help. To disable one and run another as default you can see [this]("http://ubuntuforums.org/showthread.php?t=1859945"). In my case I have one intel and another ati. If you are lucky first one should work.

---

