---
title: "Nvidia drivers, 12.10"
date: 2012-10-26
forum: New to Ubuntu
---

### Post by Pendaws on 2012-10-26
I downloaded 64bit Ubuntu 12.10 and installed. I then tried to install a driver for my Nvidia GTX 285 but each time I installed it I lost the side bar with the links and also the top bar. The resolution has changed to 1280 x 720 and says I have a laptop. :(

I have done 3 clean installs and this time I still have the side and top bars but the resolution is too large. 

Can anyone please tell me what I am doing that is so wrong? there is obviously something I am either doing wrong or something I am not doing right.
Any help would be appreciated. I have tried using google to find answers but my level of understanding some of the commands (read most) is VERY basic.

---

### Post by danielbauwens on 2012-10-26
If you go to System Settings > Displays you can change your screen resolution.
Hope it helped.

Daniel

---

### Post by thatguruguy on 2012-10-26
> **Pendaws said:**
> I downloaded 64bit Ubuntu 12.10 and installed. I then tried to install a driver for my Nvidia GTX 285 but each time I installed it I lost the side bar with the links and also the top bar. The resolution has changed to 1280 x 720 and says I have a laptop. :(

I have done 3 clean installs and this time I still have the side and top bars but the resolution is too large. 

Can anyone please tell me what I am doing that is so wrong? there is obviously something I am either doing wrong or something I am not doing right.
Any help would be appreciated. I have tried using google to find answers but my level of understanding some of the commands (read most) is VERY basic.

You may want to read [this page]("http://askubuntu.com/questions/202677/nvidia-driver-doesnt-work-in-12-10"), and follow the instructions given.

---

### Post by Pendaws on 2012-10-27
Thank you to both guys. I did what it said on that link you listed Guru and I did exactly what it said but I can't tell if the drivers are installed properly. When I go into settings and choose details I get:-
Graphics: Driver: Unknown
Experience: Standard

I did go into Software Sources and it tells me that the Driver being used currently is the 304.51 Nvidia one. Am I looking at this wrong or is there another setting I have to change?
I apologise for being such a noob.:confused:

George

---

### Post by kaldor on 2012-10-28
> **Pendaws said:**
> Thank you to both guys. I did what it said on that link you listed Guru and I did exactly what it said but I can't tell if the drivers are installed properly. When I go into settings and choose details I get:-
Graphics: Driver: Unknown
Experience: Standard

That's a known issue. It says that for me as well (I use the latest stable NVIDIA drivers). 

Sounds like your driver is working, though!

---

### Post by mc4man on 2012-10-28
System Settings > Details needs the 'mesa-utils' package to be installed to show any info in Graphics

---

### Post by alphavictorwhiskey on 2012-10-28
> **mc4man said:**
> System Settings > Details needs the 'mesa-utils' package to be installed to show any info in Graphics
 
Since I'm new, can you clarify what to do when someone says 'x' package needed? Is it simply 'sudo apt-get install mesa-utils'? I've seen this a few times and never know exactly how to get whatever it is I need. Thanks!

---

### Post by Pendaws on 2012-10-28
I added a programme called Synaptic Package Manager I found in Ubuntu Software Centre and using the Synaptic programme I was able to download the Mesa Utils and install. Now all the info for the Driver of the Graphics is showing all the info.

Thank you to everyone for your help. Hopefully I will get better as I go along and be able to help others as well. :)

---

