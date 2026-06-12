---
title: "My screen is stretched."
date: 2012-07-20
forum: New to Ubuntu
---

### Post by Nasko1111 on 2012-07-20
Hi friends.
I have installed UBUNTU on my home PC, and i am using HDMI cable to connect GPU with my monitor.
The problem is that my screen is stretched somehow, and i am unable to see my task bar, and a half of a Unity items on the left. I tried using different resolutions, but nothing works. My GPU is NVIDIA. Can anyone help me with that? I want to use UBUNTU as my desktop, but this think bodders me greatly. Thank you in advance! :(

---

### Post by BoogeyOfTheMan on 2012-07-20
I have had the same issue you are having. First time was when I was using a 37in LCD TV for a monitor, DVI-HDMI cable, resolution set in nvidia settings to 1280x720. It cut off the side of my screen and left me with a black bar on the other side. 

I found that I can change the screen alignment on my TV by hitting the left/right arrows on the remote, much like the options on most monitors. That seemed to fix it then.

I then got a new 42in LCD TV and started using that, same problem, but I couldnt adjust the screen on this TV, so I messed around in nvidia-settings  with various resolutions and eventually got it to work. Unfortunately, I cannot remember what I did, or if it was just an update to the driver that fixed it. (This was 2 or so years ago, I want to say it was switching the TV to "Just Scan" mode, but I'm not sure)

Recently, my DVI-HDMI cable stopped working, so I got a DVI-VGA cable and the problem appeared again. This time I discovered that the VGA port on the TV expected the native resolution to be 1920x1200 instead of 1080, and that cleared it right up.

God I hope that made sense, I've been awake way too long.

---

### Post by Nasko1111 on 2012-07-21
Thanks for your reply. I will try the things that you mentioned.
I have tried also the - gksu nvidia-settings - command, but i could not figure it out, again. That is a big pain in my --- :)
I hope to manage it somehow.
Thanks for your reply BoogeyOfTheMan.

---

### Post by NikTh on 2012-07-21
Hi , 
try to set the overscan , as far as it satisfy your needs.

It is not necessary to open nvidia-settings with super user privileges.

Regards

---

### Post by Nasko1111 on 2012-07-21
That worked flawlessly NikTh!!! Thank you so much for your help. Now i can continue using my UBUNTU with pleasure ;) And i will!
Thank you so much good people.

---

### Post by NikTh on 2012-07-21
Hi , 
glad that worked.
Do not forget to mark this** thread as solved** , from **thread tools**. 

Regards

---

### Post by NightScreams on 2012-07-21
hello. i am new user and new member here, registering like 5 min ago when i didn't need to apparently. I came here to solve this exact problem.
Overscan corrected it, thanks.

i would like to now ask, why does this issue exist? Seems so odd, i have never seen any other OS that ever did this.
Couple years back, i had an issue in Kubuntu where after i installed my video driver, all my fonts got super tiny, had to use kmag to read it.

Just recently, i had a major issue just to install any distro. i found out after over 12 hours of searching and trying crazy things, that it wasn't a UEFI bios issue, but my particular Nvidia 5800gtx graphics card has a known issue involving the Noveau driver or whatever it is and after a 2d mode of installing, had to insert some noaccel.conf file in my root to keep it at bay? or something like that.

I really try hard to like Linux, i do for many reasons but some of these oddball issues kill me. I get at least 1 major issue of something that appears mundane that takes me hours to figure out, But it was nice to actually see a solution that did not require me to open terminal and type a bunch of complex commands in for once. But this solution never came up when i searched google, but i guess it depends how you word it.

Anyway, thanks. i'm sure my membership won't go in vain as i'll have to ask help here in the future i'm certain.

---

### Post by BoogeyOfTheMan on 2012-07-21
I have font issues whenever I try to use KDE as well. Usually too small to read, recently, fonts were fine, then all the sudden they were huge and I couldnt change them. I want to play around with KDE but stuff like that bugs the crap out of me.

When it comes to your nvidia card, is there a reason you havent tried the nvidia drivers?

As to the screen stretching/not fitting, I've had this issue in windows too when I've switched monitors. I just chalk it up to not everything is perfect and sometimes you have to tinker around to get it to work.

---

### Post by NightScreams on 2012-07-22
> **BoogeyOfTheMan said:**
> I have font issues whenever I try to use KDE as well. Usually too small to read, recently, fonts were fine, then all the sudden they were huge and I couldnt change them. I want to play around with KDE but stuff like that bugs the crap out of me.

**When it comes to your nvidia card, is there a reason you havent tried the nvidia drivers?**

As to the screen stretching/not fitting, I've had this issue in windows too when I've switched monitors. I just chalk it up to not everything is perfect and sometimes you have to tinker around to get it to work.

you misunderstood. The default noveau driver was the issue. So i could not even get Ubuntu to even boot liveCD. i had to figure out how to disable that noveau driver first and after i installed, i could not simply just install Nvidia drivers, There was some oddball issue that forced my desktop into low resolution and the actual Nvidia driver would not function....i eventually found i had to insert a .conf file into a specific directory called Noaccell.conf and put some command line in it...ONLY then did my Nvidia driver function correctly. Again had something to do with a known issue with the newer Noveau driver that Fedora, Ubuntu..etc all  use by default. At first i thought it was a UEFI bios issue. Only when i searched for 5800 GTX issues in Linux did i eventually discover that issue under a page showing "known issues" for Fedora...then i said Eureka!!
But that was very painful experience...i imagine any new user wanting to try Linux for the first time would abandon Linux forever if they had that much trouble and is why that issue should be fixed immediately.

I've never seen the stretched desktop issue with any windows version on any monitor. Nor have i with OSX or going back in time, DOS and Amiga's. never in my 30 years of using computers have i saw that except recently on Linux...so to me, that seems the most odd and mundane thing that just shouldn't even happen to begin with on a properly tested and coded OS.

---

