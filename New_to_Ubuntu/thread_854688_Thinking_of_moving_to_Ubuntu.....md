---
title: "Thinking of moving to Ubuntu...."
date: 2008-07-09
forum: New to Ubuntu
---

### Post by Phrive on 2008-07-09
I am seriously thinking of moving over to Ubuntu over the next few weeks becauce i think its the best way to gain experience. At the moment i have it on one laptop which i use just for emails and internet browsing, and i really love it. I would also like to experiment with alternative OS's becauce ive done everything i want to do with Vista, and cant be doing with Mac, not a fan at all.

I have a few things i would like your community advice on before i take the (giant) step of moving.

These are my specs, just trying to figure out if there wil be any driver issues.

Motherboard: Asus P5N-T DELUXE
Ram: 2 GB
CPU: Intel Q6600
Hard Drive: 2 x Samsung 750GB (In raid 0)
GPU: NVIDIA GeForce 9600 GT
Wireless: Belkin F5D8053 N Wireless USB
External Storage: 500GB Western Digital USB (For Backup)

The only possible problem i can perceive is the GPU, but i understand there is nvidia drivers available so that should be ok. And also the Wireless, which could be a problem.

The biggest problem i see is my Zune, i know this wont work without a VM, which i would like to try and avoid.

What would your recomendation be, i have one hell of a lot of music so it isnt an option to put it on the other laptop and use that to update.

Is there different firmware i could get for it hack to make it work etc...

At the moment that is the only thing that is holding me back, and i really dont wnat to switch from my zune becauce im quite keen on it.

Any responces would be very welcome.

---

### Post by Sydius on 2008-07-09
Try playing with the live CD before installing it.  I don't know about Zune, but Ubuntu seems to treat my MP3 player as an external hard drive.

---

### Post by halitech on 2008-07-09
Looks like the Belkin should work according to info here:

[http://ubuntuforums.org/showthread.php?t=638864&highlight=F5D8053](http://ubuntuforums.org/showthread.php?t=638864&highlight=F5D8053)

the video card should be fine along with your external storage drive.

as to your zune, I think you may be stuck with needing a windows partition or running a virtual machine for it

---

### Post by tjwoosta on 2008-07-09
zune will not work on ubuntu without a VM (not even in wine)

i would say the best option would be to dual boot with windows

VM would be my second choice

---

### Post by chronographer on 2008-07-09
Go for it! I am looking to purchase a machine with similar specs in the next few months, and I will be running Ubuntu predominately, although XP will be on there so as I can play some games!

You will find that you are more productive, in my opinion, in Ubuntu and once its all set up its stable and there are all the applications you should need available in the repositories! This is the best aspect of Linux and Ubuntu in particular, the fact that you can update all your OS in one go, including all software installed from a repo, and that installing a program is as easy as "apt-get install thunderird". Often you will see a software on the internet you like the sound of, such as Banshee music player, "sudo apt-get install banshee" and you're all set!

Good luck. Agl

---

### Post by Phrive on 2008-07-09
Dual boot seems to be the option, before i do it will will for an alternative, i am getting 8 gig of ram in the next month or so, so i will be using 64 bit, as im quite happy with vista 64, and ubuntu must be the same idea. If i have that much ram, maybe a VM would be better, but im going to try some other alternatives before i do commit to it.

Also how are web cams with Ubuntu, i have amicrosoft on, so they wont do the firmware, but im sure they must be some generic ones about?

---

### Post by AnarkistNZ on 2008-07-09
Will the Ubuntu installer deal with RAID ok? I know installing Windows on a RAID setup is often a real bitch unless you slipstream the install file with the RAID drivers.

Might wanna double check that too.

---

### Post by Phrive on 2008-07-09
> **AnarkistNZ said:**
> Will the Ubuntu installer deal with RAID ok? I know installing Windows on a RAID setup is often a real bitch unless you slipstream the install file with the RAID drivers.

Might wanna double check that too.

The raid is done from the Motherboard, no 3rd party apps. Im not sure whether it would be a problem, vista run it fine.

Although i want to switch, im not abandoning microsoft, thats why i have the Zune, best MP3 player on the market, i just fancy a change, and a challenge

---

### Post by stchman on 2008-07-09
> **Phrive said:**
> I am seriously thinking of moving over to Ubuntu over the next few weeks becauce i think its the best way to gain experience. At the moment i have it on one laptop which i use just for emails and internet browsing, and i really love it. I would also like to experiment with alternative OS's becauce ive done everything i want to do with Vista, and cant be doing with Mac, not a fan at all.

I have a few things i would like your community advice on before i take the (giant) step of moving.

These are my specs, just trying to figure out if there wil be any driver issues.

Motherboard: Asus P5N-T DELUXE
Ram: 2 GB
CPU: Intel Q6600
Hard Drive: 2 x Samsung 750GB (In raid 0)
GPU: NVIDIA GeForce 9600 GT
Wireless: Belkin F5D8053 N Wireless USB
External Storage: 500GB Western Digital USB (For Backup)

The only possible problem i can perceive is the GPU, but i understand there is nvidia drivers available so that should be ok. And also the Wireless, which could be a problem.

The biggest problem i see is my Zune, i know this wont work without a VM, which i would like to try and avoid.

What would your recomendation be, i have one hell of a lot of music so it isnt an option to put it on the other laptop and use that to update.

Is there different firmware i could get for it hack to make it work etc...

At the moment that is the only thing that is holding me back, and i really dont wnat to switch from my zune becauce im quite keen on it.

Any responces would be very welcome.

You will have to tinker with the Nvidia drivers to get them to work.  If you have not yet purchased a video card the 8800GT/GTS/GTX works perfectly under Ubuntu and performs better than the 9600GT.

The wireless card will depend on the chipset.  The same card could have two different chipsets.

The Zune is a M$ proprietary player so no surprise that it won't work.  You can always sell the Zune and get a Sandisk.

---

### Post by Phrive on 2008-07-09
> **stchman said:**
> You will have to tinker with the Nvidia drivers to get them to work.  If you have not yet purchased a video card the 8800GT/GTS/GTX works perfectly under Ubuntu and performs better than the 9600GT.

The wireless card will depend on the chipset.  The same card could have two different chipsets.

The Zune is a M$ proprietary player so no surprise that it won't work.  You can always sell the Zune and get a Sandisk.

I already have the GPU, and was going to sli it, which i probably wont now, becauce im sure that wont work.

As for the zune, its sort of a deal breaker i really like the device, and it is constantly updated.

---

### Post by Tatty on 2008-07-09
> **Phrive said:**
> As for the zune, its sort of a deal breaker i really like the device, and it is constantly updated.

As someone said in a previous thread, try dual booting.  There is no need to remove windows to use ubuntu - especially if you have already paid for it!  
Even if you do eventually get to the stage where you never use windows anymore, its still a good idea to have it as a backup while you are still getting used to Ubuntu.

My advice on the Zune is to keep an eye out in the community to see if someone develops some linux software for it.  And try not to buy things which tie you into one OS in the futue ;)

---

### Post by Phrive on 2008-07-09
I have a complete image of my current os, which is done weekly. Thats not so much a problem, and i only have the oem liscense which is useless really.

As for the zune i see where u stand, but the problem is, in my opinion its the best out there, although custom firmwire i wouldnt say no to.

---

### Post by Tatty on 2008-07-09
> **Phrive said:**
> As for the zune i see where u stand, but the problem is, in my opinion its the best out there, although custom firmwire i wouldnt say no to.

Well its up to you.  I mean im obviously talking from the point of view of a linux user so I would value having linux over having a zune.

As i say, if i were you I would try dual-booting ubuntu and windows, and simply boot into windows for zune purposes, and see if thats a practical set-up for you.

Ultimately you have to do what works for you.

---

### Post by Phrive on 2008-07-09
I might do some research see what other are available, or try and find an alternate instal method, but i appreciate your opinion.

---

