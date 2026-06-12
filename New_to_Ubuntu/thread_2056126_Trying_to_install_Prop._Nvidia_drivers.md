---
title: "Trying to install Prop. Nvidia drivers"
date: 2012-09-10
forum: New to Ubuntu
---

### Post by Zach1928 on 2012-09-10
This is my first time using Ubuntu 12.04 and needless to say, I am quite lost. My laptop uses Optimus in windows, but In ubuntu I am assuming it opts for my GT 540m. My questions is how do I install proprietary drivers and is it necessary for them. Everything seems to be working, but in the system details it says "unkown" for my graphics. Should I go to the nvidia website and download the drivers from there?

Thanks in advance

---

### Post by newb85 on 2012-09-10
The brief answer is No.

Ubuntu would probably have notified you if it thought you should install Nvidia drivers, but if you want to check, grab a terminal and enter 
```
$ sudo jockey-gtk
```
and let it search for available drivers.

It might be possible to pull drivers from Nvidia's website, but unless you feel something's missing, it's probably not worth it.  Messing with graphic drivers can be an easy way to bork your system.

Out of curiosity, did I understand correctly that you have two graphics cards?  What makes you think Ubuntu is using the Nvidia card?

---

### Post by pqwoerituytrueiwoq on 2012-09-10
this will get you the latest stable driver, but i dont think optimis is supported so it will probally end badly
odds are you will have to revert it
```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates;sudo apt-get update;sudo apt-get install nvidia-current;sudo reboot
```to go back to the open source driver
```
sudo apt-get purge nvidia-current nvidia-settings;sudo reboot
```

---

### Post by Zach1928 on 2012-09-10
@newb85 My xps15 is one of the systems with optimus so i've got the intel graphics on the CPU, along with the GT 540m and I'm assuming linux like other OS' opts for the better of the 2 cards.

@PQW thanks and you're right about optimus i think, though i read something saying that Nvidia is currently working on optimus drivers so I'm keeping my hopes up. At any rate, will the open source drivers function as well as the Nvidia drivers? Everything seems to be working as of now

---

### Post by Epodx64 on 2012-09-11
> **Zach1928 said:**
> @newb85 My xps15 is one of the systems with optimus so i've got the intel graphics on the CPU, along with the GT 540m and I'm assuming linux like other OS' opts for the better of the 2 cards.

@PQW thanks and you're right about optimus i think, though i read something saying that Nvidia is currently working on optimus drivers so I'm keeping my hopes up. At any rate, will the open source drivers function as well as the Nvidia drivers? Everything seems to be working as of now

The open source nvidia drivers are system crippling Nouveau drivers are a big reason why I decided to sell a Nvidia chipset I had if there where any instance's of them running it'd just completely crippled the computer the x-swat/x-update drivers should work the 304.x driver was the only one that worked on my chipset if you wanna get brave and only do this if your hardwares not running well add this ppa **[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) **I warn you though if you install that ppa make sure you install ppa-purge first

---

### Post by GeForce 9500GT on 2012-09-11
When having a Nvidia graphic card and/or graphic controller with the Optimus technologie neither x-swat or xorg-edgers PPA will help. 
 
For the correct Nvidia driver supporting Optimus you must use the [Bumblebee drivers]("http://bumblebee-project.org/").

---

### Post by mips on 2012-09-11
> **GeForce 9500GT said:**
> When having a Nvidia graphic card and/or graphic controller with the Optimus technologie neither x-swat or xorg-edgers PPA will help. 
 
For the correct Nvidia driver supporting Optimus you must use the [Bumblebee drivers]("http://bumblebee-project.org/").

Bumblebee works with the newer x-swat stuff. It's actually recommend on the PPA page, [https://launchpad.net/~bumblebee/+archive/stable](https://launchpad.net/~bumblebee/+archive/stable)

---

### Post by GeForce 9500GT on 2012-09-11
> **mips said:**
> Bumblebee works with the newer x-swat stuff. It's actually recommend on the PPA page, [https://launchpad.net/~bumblebee/+archive/stable](https://launchpad.net/~bumblebee/+archive/stable)
 
really?? Must have missed that part then.... :-k

---

### Post by mips on 2012-09-11
> **GeForce 9500GT said:**
> really?? Must have missed that part then.... :-k

From the link I posted above,
> You may also want to use newer drivers (particularly if having recent hardware), then run this before installing Bumblebee:
sudo apt-get purge nvidia-current
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

After installation, reboot to let changes apply.

To see if it works, run during around 30s: glxspheres
Then, run it with optirun, and compare: optirun glxspheres

I also heard someone mention this on IRC the other day.

---

### Post by Zach1928 on 2012-09-11
I used "sudo add-apt-repository ppa:bumblebee/stable" 
 did I do it correctly? or should I purge that and enter "
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates;sudo apt-get update;sudo apt-get install nvidia-current;sudo reboot"


Sorry for all the lame questions guys

---

### Post by newb85 on 2012-09-11
> **GeForce 9500GT said:**
> When having a Nvidia graphic card and/or graphic controller with the Optimus technologie neither x-swat or xorg-edgers PPA will help. 
 
For the correct Nvidia driver supporting Optimus you must use the [Bumblebee drivers]("http://bumblebee-project.org/").

@Zach1928,
Sounds like GeForce9500GT agrees with your decision.

---

### Post by mips on 2012-09-12
> **Zach1928 said:**
> I used "sudo add-apt-repository ppa:bumblebee/stable" 
 did I do it correctly? or should I purge that and enter "
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates;sudo apt-get update;sudo apt-get install nvidia-current;sudo reboot"


Sorry for all the lame questions guys

You need to enable the xswat & bumble ppas first then install the nvidia drivers, then rebooot and then install bumblebee.

You will have to undo whatever you have done so far.

---

### Post by GeForce 9500GT on 2012-09-12
> **mips said:**
> From the link I posted above,
 
 
I also heard someone mention this on IRC the other day.
 
Which cards are (in general) supported by the Bumblebee driver?

---

### Post by GeForce 9500GT on 2012-09-12
> **mips said:**
> You need to enable the xswat & bumble ppas first then install the nvidia drivers, then rebooot and then install bumblebee.
 
You will have to undo whatever you have done so far.
 
 
```
sudo add-apt-repository ppa:bumblebee/stable
```
```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
```
```
sudo apt-get update && sudo apt-get upgrade
```
```
sudo reboot
```
 
This will work too. With the command sudo apt-get upgrade your system will be upgraded, this means also that the packages nvidia-current will be upgraded. Keep in mind that you must follow every instruction given in the terminal as well!

---

