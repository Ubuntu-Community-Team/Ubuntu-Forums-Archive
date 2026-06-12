---
title: "Annoying issue (Probably Graphical)"
date: 2014-02-07
forum: New to Ubuntu
---

### Post by jarchiepacheco on 2014-02-07
Hello, I am currently switching over from Windows 7 to 8 and I decided to try Ubuntu while Win 8 was shipped to me. I got it installed and running with only one major problem where I have no idea how to fix. This seems to be occuring randomly and my entire monitor will turn into this...[ATTACH=CONFIG]250176[/ATTACH]
I assume this is some sort of graphical issue. My video card is an Nvidia GTX 660 and I have tried installing the nvidia drivers by running 
```
sudo apt-get install nvidia-current
```
but everytime that does install when I try and boot my computer I get a black screen and have to go into recovery mode to purge the nvidia files.
Thanks in advance and please try and keep the solutions relatively simple as I am very very new to linux and have no idea how most of it works.
Thanks again.

---

### Post by Bucky Ball on 2014-02-07
Welcome. When you boot, do you get to a list of kernels to boot? A menu? If so, select your Ubuntu, but hit 'e' to edit the line.

Find the kernel line with 'quiet splash' at the end. Add to that 'nomodeset'. Proceed to boot by following the instructions at the bottom of the page. (Ctl+x from memory).

Can you get to a working desktop now?

---

### Post by jarchiepacheco on 2014-02-07
> **Bucky Ball said:**
> Welcome. When you boot, do you get to a list of kernels to boot? A menu? If so, select your Ubuntu, but hit 'e' to edit the line.

Find the kernel line with 'quiet splash' at the end. Add to that 'nomodeset'. Proceed to boot by following the instructions at the bottom of the page. (Ctl+x from memory).

Can you get to a working desktop now?

That itself isn't actually my problem. I can get to the working desktop I don't really need the latest Nvidia drivers anyways I am more concerned with the screenshot issue. And to answer your question no I don't get the menu but I have no problem getting to my desktop without the nvidia stuff installed.

---

### Post by Bucky Ball on 2014-02-07
So you are getting this random screen blur with no nvidia drivers, just working from the open-source video drivers?

If you are online, do an update and check 'Additional Drivers'. There might be a 'recommended' nvidia driver there to enable. See if that makes any diff if there is. This screen has shown no signs of misbehaving in the past?

---

### Post by jarchiepacheco on 2014-02-07
Ok I did the update and the stuff that updated mainly seemed to be Steam related and i checked the Additional Drivers tab of the Software & Updates program and it says No additional drivers available.

---

### Post by jarchiepacheco on 2014-02-07
> **Bucky Ball said:**
> So you are getting this random screen blur  with no nvidia drivers, just working from the open-source video drivers?

If you are online, do an update and check 'Additional Drivers'. There  might be a 'recommended' nvidia driver there to enable. See if that  makes any diff if there is. This screen has shown no signs of  misbehaving in the past?

Ok I did the update and the stuff that updated mainly seemed to be Steam related and i checked the Additional Drivers tab of the Software & Updates program and it says No additional drivers available.

---

### Post by Vladlenin5000 on 2014-02-07
Not the first time it happens... I mean, additional drivers showing nothing after manually installing nvidia-current. Actually you should've started by going there - in a fresh installation - and select and activate/install whatever is mentioned there as recommend (the nvidia criver version). You should only try other options when the results aren't to your liking or you want to try some newer drivers or other scenarios. A GTX660 should require the latest drivers (not necessarily bleeding-edge but some new version at least) and "additional drivers" should present the options accordingly.

Note: If you have Steam then you must have some games installed via Steam and as such your really need the nvidia proprietary drivers for optimal performance.

---

### Post by jarchiepacheco on 2014-02-07
> **Vladlenin5000 said:**
> Not the first time it happens... I mean, additional drivers showing nothing after manually installing nvidia-current. Actually you should've started by going there - in a fresh installation - and select and activate/install whatever is mentioned there as recommend (the nvidia criver version). You should only try other options when the results aren't to your liking or you want to try some newer drivers or other scenarios. A GTX660 should require the latest drivers (not necessarily bleeding-edge but some new version at least) and "additional drivers" should present the options accordingly.

Note: If you have Steam then you must have some games installed via Steam and as such your really need the nvidia proprietary drivers for optimal performance.

Ok thanks but then that brings me to the problem of getting the black screen when installing the latest nvidia drivers.

---

