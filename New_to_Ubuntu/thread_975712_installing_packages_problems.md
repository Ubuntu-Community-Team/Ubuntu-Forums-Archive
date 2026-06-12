---
title: "installing packages problems"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by geomcewan on 2008-11-08
I have been trying to install various programs and drivers with no success so far. I have tried extracting the package and then double clicking everything possible! I have also tried the command line "make" command amongst others but have failed to install anything. The programs I'm trying to install include GStreamer and PlayOnLinux as well as graphic drivers.
I didn't expect this to be as easy as windows but this seems really difficult.
I trust I am doing something really dumb - any help greatly appreciated.

---

### Post by alienexplorers on 2008-11-08
What graphic driver are you trying to load.  Have you tried using Hardware Drivers program?

---

### Post by Mark_in_Hollywood on 2008-11-08
For the future, please say with greater information what you want to do. We need to know the name of the apps/drivers at very minimum.

Having said that, you can from System/Administration, find both Hardware Drivers, Network, Printing. Is this enough? If I knew what you were installing I could have said more.

Are you online in Intrepid? or Gutsy? Online but not in Ubuntu? Are you online in a LiveCD session?

Let us know, we want to help all we can.

---

### Post by alwayshere on 2008-11-08
go to applications then add/remove find what you want mark it click apply and your done

---

### Post by fooman on 2008-11-08
best and easiest method of installing packages is with synaptic package manager.

go to system > administration > synaptic package manager

use the search button and see if what you need is available from the repos.   

playonlinux is available in a .deb file.  those are easy...just double-click on the file to install.  get it here:

[http://www.playonlinux.com/en/download-ubuntu.html](http://www.playonlinux.com/en/download-ubuntu.html)

for the graphics driver (what card is it?)...first place to look is system > administration > hardware drivers

it will show if it has a driver available for you...click on it then click the "enable" button and it should install.

---

### Post by geomcewan on 2008-11-08
The graphics driver is an NVIDIA Geforce 5 series which I got from the NVIDIA site. 
I can write here from a second computer running windows. I download everything here and put it on the other computer on which I want to use linux permanently.
I will follow your advice re the deb packages tomorrow morning and no doubt will be back in touch here. 
Pleased with such a quick response, thanks again.

---

### Post by alwayshere on 2008-11-08
put below in terminal

sudo su

then

lshw

post the result

---

### Post by oldos2er on 2008-11-08
> **geomcewan said:**
> The graphics driver is an NVIDIA Geforce 5 series which I got from the NVIDIA site. 
I can write here from a second computer running windows. I download everything here and put it on the other computer on which I want to use linux permanently.
I will follow your advice re the deb packages tomorrow morning and no doubt will be back in touch here. 
Pleased with such a quick response, thanks again.

 Go to System, Administration, Hardware Drivers, and see if you can enable your Nvidia card from there.

---

### Post by abooks on 2008-11-11
Hope this isn't too far off topic, but I'm trying to hook up a desktop with a newly installed 8.10. I don't have wifi, I'm working on a broadband connector, but I'd like to at least get dial up now. (the "network" setting under Admin isn't there, so I can't use that). I downloaded ppp 2.4.4 on my laptop in town, but can't figure out how to get it into the desktop. Tried apt-get but it says it's not there, and Syaptic will only work when it's online. Is there another method?

THX

---

### Post by lakersforce on 2008-11-11
try to do a lspci at command-line. you can see your hardware there.

---

### Post by Mark_in_Hollywood on 2008-11-12
> **abooks said:**
> Hope this isn't too far off topic, but I'm trying to hook up a desktop with a newly installed 8.10. I don't have wifi, I'm working on a broadband connector, but I'd like to at least get dial up now. (the "network" setting under Admin isn't there, so I can't use that). I downloaded ppp 2.4.4 on my laptop in town, but can't figure out how to get it into the desktop. Tried apt-get but it says it's not there, and Syaptic will only work when it's online. Is there another method?

THX

From a Ubuntu LiveCD you can open a terminal and set-up wvconfig

from the terminal then 

wvdial

and you will get your modem online and can download the GnomePPP

---

