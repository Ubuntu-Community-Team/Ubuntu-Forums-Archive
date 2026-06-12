---
title: "ndiswrapper and rt2500"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by vistasucksss on 2008-07-07
i have a linksys wifi card in my desktop and would like to know how i am supposed to get it to work. i have read many threads such as 

[http://ubuntuforums.org/showthread.php?t=563547&highlight=RaLink+RT2500](http://ubuntuforums.org/showthread.php?t=563547&highlight=RaLink+RT2500)

and others (believe me, alot)

i have ndsiwrapper installed but i really dont know where to go from there.i have downloaded 2 versions of this driver from linksys website v 1.0 and 2.0 and tried to install both of the .inf files that are included through ndsiwrapper but with no luck. the thread i posted above just confused me even more especially the part where it wants you to type 'unzip <your driver>.exe' in the command?? why/how would someone do this?

i only post questions when i feel i am at the absolute end of the road (i am considering just buying a new wifi card at this point) i hope someone out there hears my cry for help and lends me a hand. this forum is usually great from what i have seen so far and i just want to give thanks in advance.

---

### Post by tjwoosta on 2008-07-07
i was just searching google, and by the looks of it this card has native support (meaning you wouldnt even need ndiswrapper, just get a linux driver)

check out this thread (read 4th post and down and it says it worked out of the box)[http://ubuntuforums.org/showthread.php?t=570](http://ubuntuforums.org/showthread.php?t=570)

ndiswrapper is a tool so you can use windows drivers in linux (but if a linux driver already exists then ndiswrapper is useless)


Edit: ok i just found theese pages that have the linux drivers you need [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/134660]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/134660")

[http://packages.ubuntu.com/hardy/rt2500-source]("http://packages.ubuntu.com/hardy/rt2500-source")

---

### Post by vistasucksss on 2008-07-07
tjwoosta thanks for the quick reply..

i am downloading the 'source' from the very last link you posted. i hope this works i am downloading through synaptics.

thanks again i will post with my results

---

### Post by vistasucksss on 2008-07-07
[http://packages.ubuntu.com/hardy/rt2500-source](http://packages.ubuntu.com/hardy/rt2500-source)  <----should be made a sticky. solved my problem i now have wifi with my impossible wifi card!!

thanks again to tjwoosta and everyone who helps out the noobs on this site. seriously. thank you 


for any other noobs viewing this just go to SYSTEM -> ADMINISTRATION -> SYNAPTICS PACKAGE MANAGER and do a search for rt2500. download everything that comes up (2 files came up when i searched and i downloaded them both)

thanks again hope this helps others in their journey for a better and free OS


-vistasucksss

---

### Post by tjwoosta on 2008-07-07
ok this is what you should do 
(keep in mind that i dont have this same exact driver, i am just giving you general driver installation instructions)

according to the bottom link that i posted above it says

go to System-Administration-Synaptic Package Manager to download

so search rt2500 in synaptic

check the box beside the rt2500-source
click apply

according to the package info this will download the source for the driver to /usr/share/doc/rt2500-source

so navigate to /usr/share/doc/rt2500-source and read the readme.debian file 
(this should tell you how to compile as well as what dependencies you may need)

if you need help just post the readme so we can read it, but usually to compile just do this

first off to compile anything you need build-essential so do,
```
sudo apt-get install build-essential
```

then navigate to the directory the driver is in
```
cd /usr/share/doc/rt2500-source
```

then do
```
./configure
```

followed by
```
make
```

then 
```
sudo make install
```

now restart computer

then 
```
cd /usr/share/doc/rt2500-source
```

then
```
./wlan0up
```

and the driver should start working

(you will need to run ./wlan0up every boot unless you edit your /etc/rc.local)

if you get that far and need help with editing /etc/rc.local just let me know

also it says this in the info for the rt2500 package in synaptic (just incase the first driver dont work)
> An alternate driver, rt2500pci, is
available in the rt2x00-source package and in the Linux kernel from
version 2.6.24.

if you run into any troubles just post the errors or whatever and we here on the forum will be glad to help

---

### Post by tjwoosta on 2008-07-07
lol, i guess i was too slow writing that (glad you got it sorted)

---

### Post by vistasucksss on 2008-07-07
tjwoosta! thanks again for all ur help and i thought i was going crazy untill i read the post where you said you are too slow lol im like "didnt i just do that?!??!" haha but thanks again

also what is all the stuff you are saying after going to the readme.deb?? i didnt do any of that my wifi just worked right after i downloaded from synaptics...?

anyways thanks again my friend you really came through with that link

---

### Post by tjwoosta on 2008-07-07
o ok, you should be all set then


the package was named rt2500-source so i figured it was only the source code and that you would have to compile it yourself, but if it works then that means it compiled automatically

---

### Post by hyper_ch on 2008-07-07
rt2500 pci works out of the box... don't know about rt2500 usb

---

### Post by Ryuuga on 2008-07-10
> **hyper_ch said:**
> rt2500 pci works out of the box... don't know about rt2500 usb

here: [http://ubuntuforums.org/showthread.php?t=848975](http://ubuntuforums.org/showthread.php?t=848975)
i did it with rt2500usb.inf ^^

---

