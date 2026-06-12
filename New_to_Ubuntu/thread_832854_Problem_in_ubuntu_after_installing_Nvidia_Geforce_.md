---
title: "Problem in ubuntu after installing Nvidia Geforce integration GPU drivers"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by denver78 on 2008-06-18
I am absolute beginner to ubuntu and linux. I am facing problem with my Nvidia Geforce integrated GPU. I had a fresh installation of Ubuntu 8.04 on my PC. It detects most of my hardware, even my HP printer, But it failed to detect my Graphic card. There is driver available for Nvidia in restricted driver module in ubuntu. But after installation my PC got hanged after reboot. Even I tried installing the drivers using the instructions from [http://albertomilone.com/](http://albertomilone.com/) 

i used the following steps:
1) sudo apt-get install envyng-gtk
2) sudo /etc/init.d/gdm stop 
3) sudo envyng -t 

but even this method didnt help in making my graphic card work.
Please help me in this issue.

---

### Post by aktiwers on 2008-06-18
Hi and welcome!

You could try install the drivers manually.. this often fixes isues.

I have made a small guide here:
[http://ubuntuforums.org/showthread.php?p=4105735&posted=1#post4105735](http://ubuntuforums.org/showthread.php?p=4105735&posted=1#post4105735)
Follow that and it will be installed manually.

Just remember that I wrote the guide some time ago, meaning that the 3. and 2. lasts steps contains and older driver file name.

Download the latest driver here and use that file name in those 2 commands instead:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

If you don't know which one to pick, tell me what card you have and I will let you know.

Good luck!

---

### Post by denver78 on 2008-06-21
Hi, Thanks for the provided information. I tried the mentioned step but still i am having the same problem.. I tried installing the following version of driver : 96.43.05 under group: Linux IA32. I have Nvidia Geforce 2 graphic card installed in my PC. My process is AMD athlon.. Please help in this..... I have tried to seach each and every post/blog/ forum but I couldn't find any answers to the problem i am facing....

---

### Post by Gannon8 on 2008-06-21
How did it "hang?" Does it get a blank screen after the reboot?

Also, what specific nvidia card do you have? (Like I have a Nvidia Geforce4 440 Go)

---

### Post by denver78 on 2008-06-21
yes it had blank screen after reboot. name and PCI ID is as follows:

02:00.0 VGA compatible controller [0300]: nVidia Corporation NVCrush11 [GeForce2 MX Integrated Graphics] [10de:01a0] (rev b1). 
Even if i had a terminal i need gdm for openoffice writer. With existing display limited to 800 x 600 the whole screen look big and quite cluttered with huge icons and buttons..

---

