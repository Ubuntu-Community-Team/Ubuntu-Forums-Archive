---
title: "[SOLVED] Can't Install NVIDIA Card Acer 4530 on Ubuntu 8.10"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by l1th1um on 2008-10-31
I'm very glad with the release of Interpid Ibex. Because I dont get a lot of hardware problem compare with 8.04. Now I just confuse how to install the VGA Drivers. I get notification that there are NVIDIA drivers (recommended using version 177) for my laptop, but when i tried to activate it, it doesnt work. It doesnt install anything (i connected to internet). Anybody can help me out from this?

---

### Post by Titan8990 on 2008-10-31
I am still currently downloading the upgrade so I can't verify this 100% but in Hardy you could use Envyng:


sudo apt-get install envyng-gtk


Then it would be located in Applications -> Systems Tools


The name of envy might have changed or it might have lost support in 8.10 so just check around.

That program will download, install, and configure your drivers for you.

---

### Post by syrano on 2008-10-31
download the new nvidia driver
[http://http.download.nvidia.com/XFree86 ... 9-pkg1.run]("http://http.download.nvidia.com/XFree86 ... 9-pkg1.run")

---

### Post by l1th1um on 2008-10-31
> **Titan8990 said:**
> I am still currently downloading the upgrade so I can't verify this 100% but in Hardy you could use Envyng:


sudo apt-get install envyng-gtk


Then it would be located in Applications -> Systems Tools


The name of envy might have changed or it might have lost support in 8.10 so just check around.

That program will download, install, and configure your drivers for you.
envyng-gtk, it doesnt work anymore


When I go to update driver, the progress bar doesnt move from 0%

---

### Post by alan34 on 2008-10-31
Same thing happened to me. Install using Synaptic Package Manager - Just seach for "nvidia".
 
System - Adminstration -  Synaptic Package Manager

Right click on the package to install then go Apply.

Install Nvidia Settings manager at the same time if you want.

---

### Post by l1th1um on 2008-10-31
when i woke up and turn on my laptop, suddenly the driver had installed :D. I dont know why, but it solved :D

---

### Post by ashik_8.10 on 2008-11-05
Thanks from my side too. On the very night of oct.30th i told a friend of mine that this release sucks coz it detected my 800 gb xfs partition[on my desktop] as a dvd drive.(it does even now) The same day i bought a new laptop. 
And it just didnt boot up with my regular ubuntu cd for 8.04[ regular or something else, how do you call it?? not the alternate one].
I was happy in a sense, I have got work now. something similar to something what i did for making an i810 graphic chip work on kernel 2.2.14[in the old days of redhat 6.2, when i compiled the kernel first time]. 
 Well, my new acer 4530  installs only ubuntu 8.10 ( i bought a linux preinstalled version available in india[bangalore]. The distribution that they give is linpus linux[ with no drivers for x or wireless[thanks, lan drivers are preinstalled ] ], and may be they they still think linux is something like freedos). 8.10 comrade just picked up everything and didnt even leave a chance for me :)
[ i had tried fedora 11 etc meanwhile, kernel2.26.-- ]
well, i havnt got wireless. so not tested yet.
dont know if the parentheses match. well. feeling too happy :)

---

### Post by alme1304 on 2009-02-28
sorry to bring up an old topic, but i have the exact same issue as the first poster, and in synaptics the 1.77 box is already checked.

any other solutions?

---

