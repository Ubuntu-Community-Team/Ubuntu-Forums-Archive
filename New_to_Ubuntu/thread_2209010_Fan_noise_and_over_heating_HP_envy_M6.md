---
title: "Fan noise and over heating HP envy M6"
date: 2014-03-03
forum: New to Ubuntu
---

### Post by Rjoyns on 2014-03-03
Hi everyone, 

I'm pretty new to unix but I'm running Ubuntu 12.04 LTS and my fan is constantly loud and my laptop is hot in the left portion next to the touchpad even when I've got nothing running. 

Laptop details:

HP envy m6 
AMD A8-5550M
Radeon HD 8550G Radeon HD 7500M/7600M Series dual graphics
2 x 8Gb SODIMM DDR3 memory

I've read there can be a problem with the dual graphics and the fan, but I'm not sure if this may be the problem

Please help!!

Thank!

---

### Post by phidia on 2014-03-03
Doing a search on that model & overheating does show [related issues of overheating]("https://www.google.com/search?client=opera&q=HP+envy+m6&sourceid=opera&ie=UTF-8&oe=UTF-8#q=hp+envy+m6+overheating+fix") Ubuntu aside so perhaps it's not simply the OS? I'm inserting [this link]("http://askubuntu.com/questions/331093/ubuntu-compatible-laptops") too in case it might be helpful.

---

### Post by Rjoyns on 2014-03-04
Hi, Thanks for the reply.

 I am running it dual booted I never get this problem even while running a lot of processes and games on windows 8. So I thought that it was just a compatability issue with ubuntu

---

### Post by phidia on 2014-03-04
When you are in Ubuntu and hear the fans speed up you can open a terminal and type "top"
That should show what processes are using the cpu. Is laptop-mode-tools installed on your system?

---

### Post by Rjoyns on 2014-03-04
There are just a few processes at a few % when I checked with top. I checked for that programme but I don't think I have it. How can I install it? (Thanks for your patience!)

---

### Post by phidia on 2014-03-04
You can do a search in package manager or if you're comfortable in CLI (using a terminal) you can do "sudo apt-get install laptop-mode-tools".
For more reference you can look at the [guide here]("https://help.ubuntu.com/community/InstallingSoftware"). 
I hope that helps. As far as patience goes-we're all learning all the time-hopefully.

[This]("https://help.ubuntu.com/community/SensorInstallHowto") is a little older but might be useful. Offering that because it's unclear, to me anyway, exactly how much heat your laptop is developing.

---

### Post by Impavidus on 2014-03-05
Most likely it's the dual graphics. I read that the graphics card may not switch to idle whenever it should. I don't know how to solve it though. Have you checked for any available proprietary drivers?

Besides, what's in the left portion next to the touchpad? It's rather variable amongst machines. Also, because of thermal conductors build inside, the hotspots on the box may not correlate with hot components inside.

---

### Post by Rjoyns on 2014-03-05
Thanks! I'll give it a try, see whats happening and post back.

---

### Post by Rjoyns on 2014-03-05
Hi Impavidus,

from looking at the manual, I think its the heat sync for the graphics card thats below it. I will search more into the dual graphics issues then! 

Thanks!

---

### Post by rickard-joh on 2014-07-16
Hp envy m6 is terrible even with windows 8 my xgf has one and it constantly runs hot and overheats (and shutsdown)it's just not an OS problem. Some people underclock it to run cooler. However it could run maybe a bit more hot with ubuntu perhaps.

---

