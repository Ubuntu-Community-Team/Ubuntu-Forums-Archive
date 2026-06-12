---
title: "AMD A6, Radeon HD 8400: Ubuntu slow"
date: 2014-09-14
forum: New to Ubuntu
---

### Post by gab3dm on 2014-09-14
[B]I got Linux recently and ive updated everything and whatnot and it is still slow. Every video i watched about it talked about how awesome it was. Before when i got Linux on the internet and it was smooth, no lag at all. Now it slower, alot slower. 

I have a AMD laptop with A6 processor, 4 gigs of ram, and a radeon hd 8400 graphics card on the laptop. I have the latest version of Ubuntu
I dont have a Windows disk so i cant revert back to Windows.

Is there any way i can fix this problem

Anything Helps[/B]

---

### Post by pissedoffdude on 2014-09-14
Eh, lots of videos are biased.  If you use a modern desktop environment, it's really not much faster than Windows.  Anyway, are you saying web pages load slowly, or are you saying the system is slow in general?  If it's only internet related, it might be because of a driver, so provide as much info as you can.

---

### Post by gab3dm on 2014-09-14
My computer is slow. When i play games (ex. Minecraft) it got much slower 30 fps drop. Even on a minigame site like NotDoppler or Newgrounds it cant run those games without lagging. I have full bars of connection and i am right next to my Modem. I even installed the amd drivers and catalyst for the computer to help it. 
WOuld Lubuntu help? Or a Lighter Distro like puppy?

---

### Post by pissedoffdude on 2014-09-14
Alright.  This might be a graphics driver issue.  Is it slow when running multiple non-graphics intensive apps (eg browsers, word processors, email clients)?  Also, let us know if you get lag when playing videos.  Be sure to post the output of ```
sudo apt-get install mesa-utils
glxgears
```

And how did you go about installing amd's catalyst driver?

Lubuntu and Xubuntu would run faster, but if it's a graphics driver issue, it won't be as quick as you want it to be, so we should pinpoint what the issue is.

---

### Post by grahammechanical on 2014-09-14
So, it is when you are playing on-line games. It does not matter how strong the wireless signal is between the machine and the router, the important bit is the data upload and download speeds. If you are using wireless then it might be better to use an ethernet cable connection. The data transfer rates of ethernet are much, much faster than those of wireless,

Regards.

---

### Post by gab3dm on 2014-09-14
Thanks for the advice graham! It is slower when running non graphical intensive apps, Idk about videos because I use my ipad for videos. I don't remember how I installed catalyst, I got it from a YouTube video and It does work. And for the code should I put the first line first and then the second seperatly or together?
-Gabe

---

### Post by uRock on 2014-09-14
Each line is a separate command.

---

### Post by gab3dm on 2014-09-14
Glxgears:
5153 frames in 5.0 seconds = 1030.502 FPS
5335 frames in 5.0 seconds = 1066.928 FPS
4055 frames in 5.0 seconds = 810.872 FPS
4046 frames in 5.0 seconds = 809.036 FPS
4069 frames in 5.0 seconds = 813.663 FPS
4064 frames in 5.0 seconds = 812.727 FPS
4078 frames in 5.0 seconds = 815.432 FPS
4036 frames in 5.0 seconds = 807.011 FPS
4065 frames in 5.0 seconds = 812.925 FPS
4086 frames in 5.0 seconds = 817.172 FPS
4073 frames in 5.0 seconds = 814.513 FPS
4052 frames in 5.0 seconds = 810.349 FPS
4040 frames in 5.0 seconds = 807.947 FPS
4065 frames in 5.0 seconds = 812.801 FPS
4041 frames in 5.0 seconds = 808.124 FPS
1820 frames in 5.0 seconds = 363.928 FPS (Went fullscreen for a sec)
2989 frames in 5.0 seconds = 597.682 FPS (went out)
4058 frames in 5.0 seconds = 811.468 FPS
4049 frames in 5.0 seconds = 809.704 FPS
4072 frames in 5.0 seconds = 814.388 FPS
4066 frames in 5.0 seconds = 813.054 FPS
4085 frames in 5.0 seconds = 816.860 FPS

---

### Post by pissedoffdude on 2014-09-14
Hmm, 30 FPS drop is a lot  and those numbers aren't very high.  I'd suggest you try running that command with the open source drivers and try again.  Instructions for that are here: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I'm gonna assume for now it's a graphics issue because a 30 fps decrease is huge and if it were related to the entire system, it'd nearly come to a crawl otherwise.  Try that out and report back.  But do keep in mind AMD's GPU drivers on not on par with those on Windows

---

### Post by gab3dm on 2014-09-14
But I was running on 60 fps before, it dips Down to 15.

---

### Post by gab3dm on 2014-09-14
I already have "Using Video driver for the AMD graphics accelerators from fglrx (proprietary)" selected.
The other two choices are "Using Video Driver for the AMD graphics accelerator from fglrx-updates (proprietary)" or "Using X.Org X server -- AMD/ATI display driver wrapper from xserver-xorg-video-ati (open source, tested)"

---

### Post by gab3dm on 2014-09-14
sh amd-driver-installer-catalyst-13-4-x86.x86_64.run --buildpkg Ubuntu/trusty
sh: 0: Can't open amd-driver-installer-catalyst-13-4-x86.x86_64.run

This is what i get at step 3.1

SHould i just reinstall lubuntu instead of ubuntu and you can like guide me through because i already installed catalyst which made the guide difficult for me to go through

This process hasbeen frustrating and if i start from a fresh instal of lubuntu it may make this process much easier

---

### Post by pissedoffdude on 2014-09-15
It would run faster with Lubuntu, but if it's a hassle, you can try each of the drivers that are available under restricted drivers and see if that helps.

---

### Post by mastablasta on 2014-09-16
check this thread - maybe it is a similar issue: [http://ubuntuforums.org/showthread.php?t=2243850&p=13120384#post13120384](http://ubuntuforums.org/showthread.php?t=2243850&p=13120384#post13120384)

> I already have "Using Video driver for the AMD graphics accelerators from fglrx (proprietary)" selected. means you have the stable fglrx installed so it should work ok. I am not sure why you are attempting to install another set of drivers manually. but if you do plan on doing that you need to first remove the current ones that are installed.

---

### Post by gab3dm on 2014-09-16
If it were with the issue on the forum provided what would you recommend to disable. Also I can rinstall for Lubuntu or Xubuntu. Which ever you recommend. And get the right drivers.

---

