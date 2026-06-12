---
title: "help with builtin camera"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by mess110 on 2008-07-07
hello.

I just bought sony vaio vgn-fz31z laptop and installed ubuntu on it. (version 8.04) and I wanted to know how I can enable my built in camera or how can I make skype detect it.

(someone on this forum had the same problem but he only got one reply saying he should type lsusb in terminal)
when I run lsusb in terminal I get this output:

Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 05ca:183b Ricoh Co., Ltd 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

googled a bit on ricoh co and found out they make cameras. so I assume that is the camera. Now I also assume ubuntu detects the camera. now how do I use it?

thx in advance

---

### Post by k3lt01 on 2008-07-07
Have you installed Camorama? I used it in once in Feisty and then my cam worked perfectly. I haven't had to do anything with Hardy though it just worked out of the box.

---

### Post by mess110 on 2008-07-07
yes I installed camorama and when I run it it says:
"could not connect video device (/dev/video0). Please check connection"

---

### Post by k3lt01 on 2008-07-07
The same thing happened to me with Camorama at first, I rebooted my laptop and it was fine after that.

Take a look at [this Ubuntu Help page]("https://help.ubuntu.com/community/Webcam") and follow it step by step, let us know how you go.

---

### Post by mess110 on 2008-07-07
something ain't working. I tried installing easycam but I can't detect repositories. (i know I installed them properly.) i tried a bunch of other stuff but no results. rebooting also didn't work.

do you have by any chance another tutorial I can fallow. google didn't help much2day..

---

### Post by k3lt01 on 2008-07-07
No sorry I don't have another tute that I know off. Try Psychocats it's pretty good with Ubuntu related stuff. If I think of anything else I'll let you know.

Just recheck your repos lists and make sure they are all available.

---

### Post by mess110 on 2008-07-08
Sony Viao VGN-FZ31Z Motion Eye Camera

as I said before the output for my lsusb is:

Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 05ca:183b Ricoh Co., Ltd 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000



ok after a lot of hardwork I managed to get the camera working on my laptop.

so in case someone will ever be in this situation I will explain what happened and what I did with the risk of ppl laughing at me..

first I installed skype video from the skype website but there is only a 32bit version. (I installed 64 bit)
this is the link that tells you how to install skype on 64 (and some more info on skype)
[https://help.ubuntu.com/community/Skype#AMD64](https://help.ubuntu.com/community/Skype#AMD64)

after that I wanted to install easycam, wanted to add repositories but again easycam2 only worked on 32. I manually downloaded all files and double clicked the package and it worked. 

here is the location where I found out where to download files from. Just download from the link that the repository won't work.

[https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam)

I does not work with camorama but it works with skype. (and thats all you need cuz you can install skype on almost all platforms)

hope I helped someone out there cuz I have been really frustrated with this.

cheers

---

### Post by Sealbhach on 2008-07-08
Thanks, I never got mine working, I'll try it when I get home.

If it works, I'll give you a gold star (official thank-you).


.

---

### Post by k3lt01 on 2008-07-08
> **mess110 said:**
> ok after a lot of hardwork I managed to get the camera working on my laptop.

so in case someone will ever be in this situation I will explain what happened and what I did with the risk of ppl laughing at me..Congrats and well done. Don't worry about people laughing at you, YOU got it working so you know more about that particular aspect than others and you have just shared your process with others which is what Ubuntu Community is about.

Again, well done.

---

