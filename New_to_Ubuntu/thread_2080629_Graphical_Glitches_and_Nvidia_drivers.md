---
title: "Graphical Glitches and Nvidia drivers"
date: 2012-11-04
forum: New to Ubuntu
---

### Post by escott28 on 2012-11-04
I'm quite frustrated at the moment...

I'm giving Ubuntu (12.10 x64 this time) another try after a year or two. When I installed, I got random graphical glitches on the text. Thinking this was an issue with Nouveau, I installed the Nvidia drivers from the Software Sources application (Additional drivers tab). this didn't seem to fix anything, so I went to the nvidia config program (I can't remember the name, as I can't see it now). It told me to run some command (again, I can't remember) as root. I then restarted and now, I get a crappy resolution and I can't see any of the unity GUI when I log in. I can right click on the desktop, but I can't bring up any programs or the terminal when I press ctrl+alt+t.

I'm sick and tired of re-installing the whole OS every time I mess up. Can someone help me out? 

Thanks

---

### Post by escott28 on 2012-11-04
Well, I re-installed the OS again as I couldn't do anything. Still have the glitches of course, and picked the first Nvidia drivers option in software sources (proprietary, tested). I can't access the Nvidia xserver settings application. 

Here's a pic of the glitches I get. i can't believe no one else has encountered these, or at least, I haven't found any other instances of them on the internet yet. 
[IMG]http://i.imgur.com/6MRj0.png[/IMG]

---

### Post by Bashing-om on 2012-11-04
Hi ! escott28;

 I am willing to help in this graphics issue. But, be aware that I have never experienced any problems with Nvidia drivers. Presently running Nvidia on a desk top box and two laptops. Additional Drivers loaded the needed drivers and all work with out any problems.
I have done a lot of research lately on Nvidia graphic driver issues in other threads(not all are solved at this time) and am sorely lacking comprehension in some areas.
with that said ...here is my suggestion to attempt resolution, If this attempt is not successful I am willing to go on after we see the card that is installed and what drivers are loaded[ cli commands will be forth coming] :

 A bug may be caused by the drivers NOT pulling in the kernel headers
  Because they are missing, the driver can't compile and therefore, can't be loaded. Just install the headers manually and the system will happily compile the driver.
So the problem may be solved by installing the kernel headers and then reinstalling the driver:
```
sudo apt-get update
``````
sudo apt-get upgrade
``````
sudo apt-get install linux-headers-3.5.0-17-generic
```substitute the correct header file from terminal command:
```
uname -r
``````
sudo apt-get remove nvidia-current 
``````
sudo apt-get install nvidia-current nvidia-settings
```at this point We want to see if there is an /etc/X11/xorg.conf file ???

reboot and lets see where we stand..ok ??
[INDENT]just try'n to help <== BDQ


[/INDENT]

---

### Post by tamccullough on 2012-11-07
I am getting the exact same error with the very same build of ubuntu.

Ubuntu 12.10 64-bit and nvidia drivers....

Either the nvidia team has messed up or canononical has.  Either way,  I have found some "fixes" which solve the problem but mess up the system in other ways.

This works - [http://techhamlet.com/2012/10/install-nvidia-drivers-in-ubuntu-12-10/](http://techhamlet.com/2012/10/install-nvidia-drivers-in-ubuntu-12-10/)

I tried it on one of my two systems running the Ubuntu 12.10 64 bit, and it has fixed the issue. Except it has broken the auto hide function of the unity launcher.  It won't reveal itself when going to the left hand side of the screen.

At this point I will either return to 12.04 or wait for the fix whenever it comes.

---

### Post by tamccullough on 2012-11-07
Hm...
Taking a look into synaptic, it is clearly Canonical's fault.
The latest nvidia driver is not available, even with the experimental version.

Hopefully the fix it soon.

---

### Post by alphacrucis2 on 2012-11-07
The "experimental" driver works ok for me. The so called stable nvidia drivers are junk.

---

