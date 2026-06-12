---
title: "Graphics issue installing on HP G60 100EM (Nvidia Geforce 8200M)"
date: 2018-10-15
forum: New to Ubuntu
---

### Post by xandyfive on 2018-10-15
Hi all,

I am trying to install Ubuntu on my machine (at the moment as a dual boot along with Windows Vista) and am having an issue getting the graphics driver to work.  I am experiencing a severe flickering of the screen and have been trying the various drivers (nvidia-304/nvidia-340) as indicated in the additional drivers but non of these seem to improve things.  I have tried various different installs of Ubuntu  including 16.04.5 and 18.04.1 of Ubuntu along with Lubuntu, Zorin and Pop-os but all seem to display similar symptoms with regard the screen flicker issues.  When I boot into Windows, I get no issues so assume the screen is OK.

Any help in trying to fix this would be most appreciated.

Many Thanks.

---

### Post by mastablasta on 2018-10-16
do you have 2 graphics chips? if so which one is used during flickering?

does it work without proprietary drivers? if so, then drivers are the issue which means you should ask on nvidia forums for support.

---

### Post by xandyfive on 2018-10-16
Thanks for your reply[**[COLOR=#DD4814][B]**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=964486") mastablasta.  I don't think I have more than one graphics chip - just Nvidia GeForce 8200M G is showing in windows device manager.  

I have just tried installing Xubuntu and that seems to be working fine (including using the Nvidia-340 driver).  I think now that possibly it may be something else causing the issue rather than directly related to the graphics chip/driver.  Maybe something in my laptop specs. is not sufficient to handle Ubuntu.  Still, happy that I have found a version that seems to work OK with Xubuntu.

Thanks again.

---

### Post by Autodave on 2018-10-16
Ubuntu is a rather heavy desktop: uses a lot of memory.  But, Lubuntu uses even less than Xubuntu, so it really doesn't make any sense that Xubuntu is running OK.  However, if it ain't broke.......  :-)

---

### Post by monkeybrain20122 on 2018-10-17
> **Autodave said:**
> Ubuntu is a rather heavy desktop: uses a lot of memory.  But, Lubuntu uses even less than Xubuntu, so it really doesn't make any sense that Xubuntu is running OK.  However, if it ain't broke.......  :-)
No *buntu would be "heavy" comparing to Vista.:p

---

### Post by mastablasta on 2018-10-18
> **xandyfive said:**
> 

I have just tried installing Xubuntu and that seems to be working fine (including using the Nvidia-340 driver).  I think now that possibly it may be something else causing the issue rather than directly related to the graphics chip/driver.  Maybe something in my laptop specs. is not sufficient to handle Ubuntu.  Still, happy that I have found a version that seems to work OK with Xubuntu.


main difference is that Xubuntu doesn't use GPU acceleration to draw desktop and do various special effects. use what works best for you. aside from the user interface there is not much difference between the two. furthermore the XFCE used in Xubuntu is very easy to customize. so you can quickly make it to look as you would like it to look. it can be more plain or you can add effects. move panels and icons around, there are themes available, change the "start" button...

---

### Post by xandyfive on 2018-10-24
Hello again,

It seems I spoke too soon with regard Xubuntu working OK!!  I now seem to be experiencing random crashes (either screen just goes blank and system becomes unresponsive, or it just reboots itself).  Is there any form of crash report that I can view which may indicate what is causing this problem?

Many Thanks.

---

### Post by him610 on 2018-10-24
I just checked the system specifications of your HP G60 100EM. It seems to be 10+ years old. Either Xubuntu or Lubuntu is a good choice. I have two laptops about the same age - both having come with Win Vista; however, mine both have intel CPUs where you have an AMD CPU. Have you considered that your the random crashing may be the result of the CPU overheating?  Sometimes, over the years foreign material - lint, hair, dust, gets sucked into the air passages of any laptop that tend to block the airflow that normally cools the CPU and GPU chips. A thorough vacuuming of the air vents may help.

---

### Post by xandyfive on 2018-10-25
Thanks for your repl[**[COLOR=#000000][/COLOR]**]("https://ubuntuforums.org/member.php?u=248298")y him610.  I have just run a temperature check app (whilst running Windows) and the temperatures of the cpu are: current 83 deg. C (max 93 deg. C) and for the gpu  current 90 deg C (max 110 deg C).  Not sure if these values are high or not but may be worth cleaning out the vents anyway.  Windows does not crash at all but maybe Xubuntu causes my machine to run at higher temps or has a lower tolerance before crashing.

Regards.

---

### Post by mastablasta on 2018-10-26
> **xandyfive said:**
> Thanks for your reply him610.  I have just run a temperature check app (whilst running Windows) and the temperatures of the cpu are: current 83 deg. C (max 93 deg. C) and for the gpu  current 90 deg C (max 110 deg C).  Not sure if these values are high or not but may be worth cleaning out the vents anyway. 

those temps are too high. you PC is overheating. or is running on borderline. time for some good cleaning.

> 
 Windows does not crash at all but maybe Xubuntu causes my machine to run at higher temps or has a lower tolerance before crashing.

quite possible. a non optimal driver may cause GPU to work more than it should so it creates extra heat. furthermore it could be that GPU driver is using CPU for graphic acceleration, adding additional strain to an already hot CPU. it then pushes it over the limit which causes the shutdown (safety feature, otherwise you would have the potential to create fire on your desk).

---

### Post by xandyfive on 2018-10-27
Hi,

Many Thanks to everyone who has replied to this.  I vacuumed out the cooling fan and vents on my laptop and it has resulted in it running a lot cooler now so thanks for that advice.  However, this did still not resolve the issue.  

But, I came across this thread : [https://ubuntuforums.org/showthread.php?t=2396263](https://ubuntuforums.org/showthread.php?t=2396263) and it seems to have done the trick.  It would appear that my graphics card needs to have the Nvidia 304 driver installed with a specific patch to make it work.  As I am new to linux, it took a few attempt to get it right but eventually it installed and everything now seems to be fine.  Can now mark this thread as solved.

Thanks Again

---

