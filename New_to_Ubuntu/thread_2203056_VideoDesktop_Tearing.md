---
title: "Video/Desktop Tearing"
date: 2014-02-01
forum: New to Ubuntu
---

### Post by LukasLeon on 2014-02-01
Hello, i installed Ubuntu Studio 13.10 yesterday and i am experiencing a problem with tearing in HD videos and by moving windows or scrolling down a page. I was trying to fix this yesterday by installing a .run geforce driver ( I have Nvidia Geforce 450GTS video card ) and end up with reinstalling system because i was unable to boot ( black screen ). So i decided to write here because i dont want to screw things up again... I did install nvidia-current drivers, by using this commands: sudo apt-add-repository ppa:ubuntu-x-swat/x-updates, sudo apt-get update, sudo apt-get install nvidia-current, i am now able to open nvidia-settings ( before i was having an error ) and it seems to identificate my video card, but the tearing is still here. Then i followed this thread: [http://ubuntuforums.org/showthread.php?t=1645908](http://ubuntuforums.org/showthread.php?t=1645908), i have installed compiz and compiz system manager from synaptic, but the option to enable vsync and disabling automatic refresh rate detection seems to be missing ( picture below ). My xorg.config file is blank. Ive also tried to install additional drivers from ubuntu soft centre, and it says "this driver is activated but not currently in use" ( again picture below ). Also there are 3 other options to install those xorg drivers, should i install them? i am kinda scared of getting the black screen again.. I hope i provided enough information, thanks.
[IMG]http://oi62.tinypic.com/142e7o0.jpg[/IMG]

---

### Post by PotatoHead007 on 2014-02-01
You might want to go to the official nVidia website and download the driver for your graphic card.
Before you do this, make sure that your system is fully up to date(i.e sudo apt-get update, sudo apt-get upgrade).

Website for drivers: [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Then, press Ctrl+Alt+F1, login and type the following:

sudo /etc/init.d/lightdm stop
 chmod +x <Nvidia file>.run
 sudo ./<Nvidia file>.run 
When that is done, execute reboot.

Note that if you install the driver like this, you will not get any updates automatically, and must always do it manually.
Before you do this though, backup your files, because there is never a guaranty that it will work(although it did for me).

A website that tells of different ways: [http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html)

Hope it helped [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]

---

### Post by LukasLeon on 2014-02-01
> **PotatoHead007 said:**
> You might want to go to the official nVidia website and download the driver for your graphic card.
Before you do this, make sure that your system is fully up to date(i.e sudo apt-get update, sudo apt-get upgrade).

Website for drivers: [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Then, press Ctrl+Alt+F1, login and type the following:

sudo /etc/init.d/lightdm stop
 chmod +x <Nvidia file>.run
 sudo ./<Nvidia file>.run 
When that is done, execute reboot.

Note that if you install the driver like this, you will not get any updates automatically, and must always do it manually.
Before you do this though, backup your files, because there is never a guaranty that it will work(although it did for me).

A website that tells of different ways: [http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html)

Hope it helped :smile:


Hey, thanks for your information :). I am a bit scared about installing the drivers from nvidia site, because yesterday i was unable to boot after doing it ( i did mention this in my original post also ). But thanks to the site you have provided, with those different ways, i tried to update my drivers thrue the ubuntu soft. centre: additional drivers, to the newest 331. And now i got almost no tearing at all! It has really improved, and now it is almost perfect. So thanks for your tip ;) I am glad it is better now. If i decide to install those from nvidia site, to maybe fix my problem totally, can you tell me how to remove them in recovery if it goes wrong again?

---

### Post by LukasLeon on 2014-02-01
Any ideas anyone? the tearing is still pretty annoying, especially in videos.. the funny thing is, few days ago i had Xubuntu installed thrue wubi, and there i just installed drivers from additional drivers and had no tearing, i did here exactly the same, but experience this problem...

---

### Post by PotatoHead007 on 2014-02-02
> **LukasLeon said:**
>  If i decide to install those from nvidia site, to maybe fix my problem totally, can you tell me how to remove them in recovery if it goes wrong again?

This should work: [http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely](http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely) (Note the comment "thanks, this was effective on ubuntu 13.10"
I ran into that problem once, and doing what this guide does fixed it. Sorry to hear that the tearing is still there, no idea how to fix it if that doesn't :(.

---

### Post by LukasLeon on 2014-02-02
> **PotatoHead007 said:**
> This should work: [http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely](http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely) (Note the comment "thanks, this was effective on ubuntu 13.10"
I ran into that problem once, and doing what this guide does fixed it. Sorry to hear that the tearing is still there, no idea how to fix it if that doesn't :(.

Well i already took the risk and tried to install 331 drivers which are the newest one, but tearing consists.. I really dont know what i am missing.. i was also trying to boot without Nvidia drivers, using just nounveau, same tearing as with Nvidia.. Tried nvidia 304, 319 and 331, same in all of them. Tried to modify my xorg.conf file in many different ways which i found on forums thrue google, nothing helped.. actually there are lot of topics about this problem, but very little answers and solutions, seems like a common nvidia problem, guess i have to get use to it O.o

---

### Post by PotatoHead007 on 2014-02-02
Wow ok... sorry i could not help fix it completely.

---

### Post by MartyBuntu on 2014-02-02
> **LukasLeon said:**
> Ive also tried to install additional drivers from ubuntu soft centre, and it says "this driver is activated but not currently in use" ( again picture below ).


It's a long-time bug...in Additional Drivers showing the driver not activated, but it actually is.

---

### Post by LukasLeon on 2014-02-02
> **MartyBuntu said:**
> It's a long-time bug...in Additional Drivers showing the driver not activated, but it actually is.

Ah well.. so atleast i know my drivers are working x)

---

### Post by LukasLeon on 2014-02-02
Woohoo! I managed to fix the tearing by using Compton as my compositor ! So if anyone else experience this problem, just follow this [http://ubuntuforums.org/showthread.php?t=2144468](http://ubuntuforums.org/showthread.php?t=2144468) :)

---

