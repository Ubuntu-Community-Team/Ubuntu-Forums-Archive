---
title: "graphics problem"
date: 2012-10-16
forum: New to Ubuntu
---

### Post by Roger1957 on 2012-10-16
I am A first time user of Ubuntu. Just installed 12.04 lts. How do i install Nvidia drivers?:rolleyes: in the displays area, its showing laptop and i can't get it to detect that its not a laptop.

---

### Post by NikTh on 2012-10-16
Hi  and welcome to Ubuntu World. 

You have to know that Ubuntu(Linux) comes with the driver for Nvida cards pre-installed. Named: nouveau. 

If  you have a real problem with your graphics (eg: video tearing , glitch , desktop environment ..etc) you can install additional drivers from Nvidia. 
Ubuntu's open source driver (nouveau) is not a general driver only for first boot. Its developed by Ubuntu's developers  and suited to a lot of Nvidia cards without a problem. 

When you want to install additional (restricted) driver of Nvidia , then you must open the additional drivers program. You can call it from Dash by writing **additional** or via terminal with this command ```
jockey-gtk
```. Always install the [Recommended] one. 

The [Ubuntu community wiki]("https://help.ubuntu.com/community/") its an inexhaustible source of informations. Here you can find more info : [Binary Driver Nvidia/How to]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia").

Thanks

---

### Post by thatguruguy on 2012-10-16
Wait. Please describe your hardware. What exact kind of graphics card do you have?

Also, some displays identify themselves as laptop displays. That can be safely ignored, and shouldn't cause any problems. I'd be more curious about whether your graphics drivers are properly installed.

---

### Post by rishioid on 2012-10-16
Welcome to open world of Ubuntu bro, I agree with NikTh, your graphics drivers are set while installation, in my case I used to get a popup of Restricted drivers available, but I had a bad experience with My Ubuntu 12.4 64bit on AMD with nvida drivers.

---

### Post by Roger1957 on 2012-10-16
Thank you for the info.

---

