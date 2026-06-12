---
title: "login screen problem"
date: 2012-05-02
forum: New to Ubuntu
---

### Post by mj360 on 2012-05-02
i just updated to 12.04 but once it goes to the login screen the monitor says unsupported video signal but i can hear the ubuntu sound so i login without seeing the screen but once i login everythings fine it's just do this at the login screen i don't understand why it's doing this. everyone know why this happening ?

---

### Post by mj360 on 2012-05-03
> **mj360 said:**
> i just updated to 12.04 but once it goes to the login screen the monitor says unsupported video signal but i can hear the ubuntu sound so i login without seeing the screen but once i login everythings fine it's just do this at the login screen i don't understand why it's doing this. everyone know why this happening ?
i'm i the only one who having this problem ?

---

### Post by anejo on 2012-05-03
It would seem so mate... but lets see what we can do anyway to get you to see the greeter screen.
So when you power up your machine... 
you get a blank screen... 
nothing visual only an auditory clue that Ubuntu is actually doing something? 
Is that it?
(And then you login and then you see the desktop)

---

### Post by anejo on 2012-05-03
Also before you login...
If you were to press [B]Ctrl+Alt+F1 
[/B]does that take you to a login prompt that you can see?

---

### Post by mj360 on 2012-05-03
yes that's right.

---

### Post by mj360 on 2012-05-03
yes it show ubuntu login in all black when i do ctrl alt f1

---

### Post by NikTh on 2012-05-03
> **mj360 said:**
> yes it show ubuntu login in all black when i do ctrl alt f1
Hi  , 
try to login from there , then do ```
sudo apt-get -f install 
sudo dpkg --configure -a 
sudo apt-get update ; sudo apt-get dist-upgrade
``` 
When commands finish , reboot and see if works.
Thanks .

---

### Post by mj360 on 2012-05-03
it didn't work. but i forgot to say, it works when i hook the pc up through hdmi but it don't work with vga.

---

### Post by NikTh on 2012-05-03
> **mj360 said:**
> it didn't work. but i forgot to say, it works when i hook the pc up through hdmi but it don't work with vga.
Except for VGA(hardware) problem , 
maybe vga's graphics are to low to run with Ubuntu ? I don't really know ... i am not sure. 
What is your card ? 
Give the output of ```
lspci -nnk | grep -iA2 vga
```
Thanks

---

### Post by anejo on 2012-05-03
IF **NikTH**'s solutions are working for you great!
If not, again in that terminal--Ctrl+Alt+F1--what you should try is first get 'gdm' installed
```
sudo apt-get install gdm
```The above command assumes that you have access to the Internet of course.
If not, then do so after you have login successfully.
Remember we are trying to get a greeter-login screen visible for you...
Assuming then that you have gdm installed... at the prompt
```
sudo dpkg-reconfigure gdm
sudo reboot
```The first time you do this--because the lightdm is not showing--select gdm and then reboot.
The gdm version of a login screen should be presented... and you should be good to go!

---

### Post by mj360 on 2012-05-03
sorry i forgot to say it's a aspire acer desktop with a nvidia geforce 9200 with 4gb of ram

---

### Post by mj360 on 2012-05-03
i did the lspci -nnk | grep -iA2 vga and this what i got.


02:00.0 VGA compatible controller [0300]: NVIDIA Corporation C77 [GeForce 8200] [10de:084b] (rev a2)
	Subsystem: Acer Incorporated [ALI] Device [1025:0153]
	Kernel driver in use: nvidia

---

### Post by mj360 on 2012-05-03
i did the sudo apt-get install gdm and this what i got 

A display manager is a program that provides graphical login              &#9474;  
 &#9474; capabilities for the X Window System.                                     &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Only one display manager can manage a given X server, but multiple        &#9474;  
 &#9474; display manager packages are installed. Please select which display       &#9474;  
 &#9474; manager should run by default.                                            &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Multiple display managers can run simultaneously if they are configured   &#9474;  
 &#9474; to manage different servers; to achieve this, configure the display       &#9474;  
 &#9474; managers accordingly, edit each of their init scripts in /etc/init.d,     &#9474;  
 &#9474; and disable the check for a default display manager.

---

### Post by NikTh on 2012-05-04
Hi,
gdm its another X display manager. Ubuntu from 11.10 and after runs with LightDM display manager. I think its not necessary to install them both. 

I don't really see any problem with your card. As i mentioned before maybe VGA(input-export)  is responsible for that problem you have.
Try to use Hdmi instead.


Also i see that you have nvidia's proprietary driver installed. Do you want to test the free and open source nouveau driver ? 
If yes then open a terminal and ```
sudo apt-get remove nvidia-current nvidia-settings
``` and reboot your system.
Thanks

---

### Post by mj360 on 2012-05-04
how do i install this open source nouveau driver ?

---

### Post by NikTh on 2012-05-05
> **mj360 said:**
> how do i install this open source nouveau driver ?
Hi , 
open source driver is pre-installed in Ubuntu. If you remove Nvidia's driver then nouveau takes place automatically . 
Reboot for driver take place.
Thanks

---

### Post by mj360 on 2012-05-08
hey sorry it taking me so long to reply back. but i uninstall the nvidia drive and the login screen does show, so i guess it's a problem with the nvidia drivers ?

---

### Post by mj360 on 2012-05-11
after updating it everything works good now. so i guess it's was a bug

---

