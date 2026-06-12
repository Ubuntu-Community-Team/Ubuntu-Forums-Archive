---
title: "Flickering issue in Ubuntu 16.04"
date: 2017-01-13
forum: New to Ubuntu
---

### Post by lefterios on 2017-01-13
I have recently installed Ubuntu but I'm getting flickering issue in browsers(Firefox and Chrome) and in applications and games(Minecraft). I guess that's nvidia drivers related. So I installed the proprietary nvidia drivers rebooted and nothing happened. I also tried to manually install nvidia drivers through nvidia's website but the problem insists. Any idea?

---

### Post by mjjenkins on 2017-01-13
Ive had this same problem. I did a clean install after wiping Windows 7 on a Compaq Presario CQ50. There appear to be three different drivers associated with this model. Two are Nvidia and one is the open source version. Out of those three, the two proprietary ones are the only ones that work whatsoever, but one causes the flickering problem, unbearable by the way (not some minor issue), and the other fixes the graphical problems but causes the system to freeze and wont let any programs run. Ive tried many suggestions from various forums, but none have really helped. Its like for every thing that gets resolved, a new problem takes it's place. Im relatively new to this kind of thing and am just learning as I go along, but it has been my understanding that most common laptops have intel integrated gpu chips..... thats not to say that nvidia doesnt make software for integrated chips. idk. Im just trying to be thorough and consider all possibilities. I appreciate any help from you all, and I want to say that this looks like a great community of people and Im very excited about learning this awesome OS.

---

### Post by mjjenkins on 2017-01-13
I believe it is the open source driver that causes the flickering specifically, but I may be remembering it wrong.....

---

### Post by lefterios on 2017-01-13
The open source driver has the flickering bug definitely. I don't know about 2 proprietary from nvidia what do you mean? I had installed the nvidia driver through system setting > software update > proprietary drivers and it didn't work. I also downloaded from nvidia.com and by using apt-get install nvidia-current and nothing worked either. Is that what you mean when you're talking about two different nvidia drivers?

---

### Post by mjjenkins on 2017-01-13
My system isnt stable enough at this point to open and run things other than from the terminal........ but yes, as I understand it, two of those drivers are the real (proprietary) software from nvidia.... where open source ones are basically copies made especially for this OS. The open source one causes the flickering and one nvidia brand driver causes the login loop while the other nvidia brand driver fixes graphical glitching but makes the system lag and freeze to the point of it being basically inoperable. At that point all I can do is ctrl + alt + f3 to open a terminal on boot.

---

### Post by lefterios on 2017-01-15
So no one suggests something?

---

