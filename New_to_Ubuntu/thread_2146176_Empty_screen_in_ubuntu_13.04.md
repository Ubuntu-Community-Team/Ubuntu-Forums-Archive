---
title: "Empty screen in ubuntu 13.04"
date: 2013-05-17
forum: New to Ubuntu
---

### Post by nsf7 on 2013-05-17
New guy here. Not just in the forum but using ubuntu as well, so everything is new to me. Here goes. Reading a rc forum I found a post about ubuntu, so i decided to search for the os and see how it looked like. I got pretty surprised with the newly released ubuntu 13.04, in every aspect. I used Windows for long time, until I moved to the MAC OS some years ago. I still use Windows when I have to, but hate the thing. I have at home an old pc (about 10 years old) running xp, and its as slow as is can be, so I decided to instal in that machine the latest ubuntu, along side Windows. 
The install went fine, but I can't get ubuntu to work. I get to the start screen where I have to insert the password, but that's it. As soon as I do the login I get a completly empty screen, with just an orange background. No icons,nothing, just the empty backgroung.
I suspect that the problem is in the outdated pc, but I was hoping some one could shed some light.

PC specs
grafic card - Asus Radeon A9200SE 
Processor - AMD Athlon XP2700+ 2.2ghz
RAM - 1gb
Motherboard - Asus A7V8X-X

Thanks

---

### Post by rburkartjo on 2013-05-17
nsf7 your graphic card might not support the default desktop- unity. you can try this thought as soon you get to the blank screen use the short key ctrl +alt + t (the letter). this should open a terminal and then type sidset unity in the terminal then hit the enter key and hopefully unity will load up. i also have a radium driver and have to do it to get it to load. good luck

---

### Post by nsf7 on 2013-05-17
Thanks for your help. I too suspect that the problem may be in the old hardware. Anyway, did as you said but all the same. Pressing the keys you mentioned makes half of the screen go grey, while the other half remains as I said, in the orange background. But cant type anything.

---

### Post by grahammechanical on 2013-05-17
If the live session works then an install should work. Two things are important, 1) The amount of memory on the video adapter. If it is shared memory then that will reduce the available RAM; 2) The video driver.

When you installed Ubuntu did tick to install third party software? If you did that Ubuntu will also install a proprietary video driver. And I think that it is the proprietary video driver that is causing this problem. What can you do?

a) Re-install and this time not tick third party software. In this way Ubuntu will use the opensource video driver called Nouveau. I use it without problems. If you hardware is not able to run Unity 3D then in 13.04 we get an open source video driver called llvmpipe. It is supposed to give us the Unity 3D experience on lower specification hardware. Now go to System Settings and load Software & Updates and open the Additional Drivers tab. There you should see a selection of video drivers to experiment with. Experiment.

b) At the Grub menu select Advanced Options for Ubuntu. It is a sub-menu. Now select Recovery mode and press F10 to boot into recovery mode. At the recovery mode screen select resume. That might get you to a working desktop. Ubuntu should be using llvmpipe. Now go to System Settings and load Software & Updates and open the Additional Drivers tab. There you should see a selection of video drivers to experiment with. Experiment.

c) At the orange background right click the background. If a menu appears select Change Desktop Background. That will load System Settings and from there you will be able to get to the Additional Drivers tab in Software & Updates where you can mess with video drivers.

Regards.

---

### Post by nsf7 on 2013-05-18
Thank's guys for the help. Did everything as you said grahammechanical. Using metod A got the same results, so I restarted the pc under recovery mode, but no changes. So tried metod C and was able to get to system settings, but cant open software and update. I have no problems opening the other tabs, althoug the computer is running extremely slow. Takes a few seconds to open any tab, except program and update , that just doesnt open.
One thing, did as you said and didnt tick to install third party software. Going to system settings, under details tab on the grafics I have this: VESA: V280.

Thanks once more

---

### Post by mörgæs on 2013-05-18
The easiest approach is just to install Lubuntu 13.04 in stead of Ubuntu.
Nouveau drivers mentioned above are irrelevant, as they are only for Nvidia cards and you have ATI.

---

### Post by nsf7 on 2013-05-18
Thanks morgaes. As I mentioned above this was my first incursion in open OS. Ubuntu was the first one I downloaded and tried to install.
After this problem and some search I came across with Fedora was thinking in giving it a try, but after some dighing I dont think it will run the pc as well.
Wat are de diferences between the OS you mentioned?

---

### Post by mörgæs on 2013-05-18
Lubuntu is the lightest member of the Buntu family. As your graphics card is from around 2003 it's a better choice than the quite demanding Ubuntu.

---

