---
title: "how do i run .run"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by ac1240 on 2008-05-09
i have downloaded the ati drivers from there site
and the file is a .run how can i execute that file ?

---

### Post by Joeb454 on 2008-05-09
If it is on your Desktop then open up a terminal from Applications > Accessories > Terminal and run the following ```
cd ~/Desktop
./<filename>.run
```

Where <filename> is whatever ATi have called their driver

---

### Post by szymon_g on 2008-05-09
first :

chmod +x file.run

than

sudo sh ./file.run or sudo ./file.run

of course, to install graphic drivers, you have to have Xorg turned off (but you prabably know that)

---

### Post by brigux on 2008-05-09
You might have to 
```
chmod +x <filename>.run
``` first

---

### Post by bumanie on 2008-05-09
Personally, I would try the ubuntu hardware drivers first (if you haven't already), they tend to work well in most circumstances.

---

### Post by ac1240 on 2008-05-09
> **bumanie said:**
> Personally, I would try the ubuntu hardware drivers first (if you haven't already), they tend to work well in most circumstances.

tried that and its very low fps

> **szymon_g said:**
> first :

chmod +x file.run

than

sudo sh ./file.run or sudo ./file.run

of course, to install graphic drivers, you have to have Xorg turned off (but you prabably know that)

i dont know how pls write it down

---

### Post by szymon_g on 2008-05-09
you have to logout and (in gdm) log into terminal (or konsole- i dont know, i use kubuntu)
just in case, if gdm/xorg would be still on, you should write

sudo killall -9 gdm
sudo killall -9 Xorg

than, if you have this file on your destkop, run

cd Destkop
chmod +x file.run
sudo sh ./file.run

btw, did you tried program called Envy :?
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

? its really nice, it work usually well

(but i have a Nvidia card, so i dont know exactly how good does it work on ati cards)

---

### Post by Joeb454 on 2008-05-09
Envy does work well, but remember you usually need to run Envy again after each Kernel update

---

### Post by ac1240 on 2008-05-09
> **szymon_g said:**
> you have to logout and (in gdm) log into terminal (or konsole- i dont know, i use kubuntu)
just in case, if gdm/xorg would be still on, you should write

sudo killall -9 gdm
sudo killall -9 Xorg

than, if you have this file on your destkop, run

cd Destkop
chmod +x file.run
sudo sh ./file.run

btw, did you tried program called Envy :?
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

? its really nice, it work usually well

(but i have a Nvidia card, so i dont know exactly how good does it work on ati cards)

what do you mean "you have to logout and (in gdm"
how can i log out and start the terminal if i am out ?

---

### Post by Saint Angeles on 2008-05-09
my method has worked for many people i know as well as myself (on gutsy and hardy):

[http://ubuntuforums.org/showpost.php?p=4749740&postcount=12](http://ubuntuforums.org/showpost.php?p=4749740&postcount=12)

---

### Post by bumanie on 2008-05-09
To stop xserver and get into console mode is ctrl-alt-F1 together, to restart xserver ctrl-alt-F7. To stop gdm > sudo /etc/init.d/gdm stop to restart gdm > sudo /etc/init.d/gdm start I knew this part, but did not know the code for installing an ati card. I hope the two posts together help.

---

### Post by 10Digits on 2008-05-09
Kill x server then press Ctrl+Alt+ F1
Log in as root then cd to the dir. where the file is and type

sh <filename>.run 
 it should run fine 
sorry about the command to kill the x server you can check out the forums for that..


If u have intrnet then add or remove programs can be used to install drivers for ati engine.... I suppose.

---

### Post by dreadlord_chris on 2008-05-09
> **Joeb454 said:**
> Envy does work well, but remember you usually need to run Envy again after each Kernel update

Not since Allbert incorporated DKMS into Envy - it's *automagically* taken care of for you now:
[FAQ #F]("http://albertomilone.com/envyngfaq.html#F")
> 
F) What happens if the kernel is upgraded (e.g. via system updates)?

You won't have to do anything at all. DKMS will automatically install the module for your new kernel. NOTE: make sure that the kernel headers (linux-headers) for that kernel are also installed.


---

