---
title: "Freezes and Many reboots!"
date: 2016-01-26
forum: New to Ubuntu
---

### Post by neno2 on 2016-01-26
Hi Guys and Gal, 

I'm new to Ubuntu (got it for my job) and so far I like it. However, I find that it's rather unstable on my computer. It freezes when I'm running certain programs (multiple instances of pdfgui for example). I had to do three hard reboot today!

I've had to reinstall twice during the first few days of installing it last week. Moreover, when I hibernate, it restarts instead (which I realize I shouldn't be doing as I have a ssd). I also cannot get my image [FONT=arial]MF220 wireless  printer to work (was working with Wind 10) even though i have the right drivers and there appears to be a connection...I'm just ugh...I initally wanted to do a dual booth and got convinced into going all the way with Ubuntu, but things like this qre crushing my spirit in Ubuntu. Can anyone help me?[/FONT]

My computer's stats are:

Lenovo Y50 touch
Memory: 7.7 gbs
Processor: ntel® Core™ i7-4720HQ CPU @ 2.60GHz × 8 
Graphic: Intel® Haswell Mobile 
64 bit 
976 GB of memory 
NVIDIA Getforce GTX


Can anyone help me figure what's going on?

---

### Post by Darth4212 on 2016-01-27
Maybe reinstall but this time change the amount of RAM and make it larger amount?

---

### Post by blade4 on 2016-01-27
Couple of things here : 

1. Can you tell us which version of ubuntu you're running ? 

2. If the system hangs , pressing Ctrl + Alt + F1 will transfer you to the tty terminal ( just a black screen with a command prompt ). You'll need to reenter your username and password but once you're in , enter the word 'top' ( minus quotes ) , press return, and check if anything is using up your cpu ( top is like system monitor but for command line ). Let us know if any process is using too much cpu - it'll help narrow down the problem. 

You can safely shutdown or restart from the command prompt by entering the following commands : 

For shutdown
```
 sudo shutdown -h now 
``` 

For restart 
```
 sudo reboot 
```


Regarding the printer connectivity, I'm not sure how to approach it but someone else here will probably help you out soon.

---

### Post by neno2 on 2016-01-27
> **blade4 said:**
> Couple of things here : 

1. Can you tell us which version of ubuntu you're running ? 

2. If the system hangs , pressing Ctrl + Alt + F1 will transfer you to the tty terminal ( just a black screen with a command prompt ). You'll need to reenter your username and password but once you're in , enter the word 'top' ( minus quotes ) , press return, and check if anything is using up your cpu ( top is like system monitor but for command line ). Let us know if any process is using too much cpu - it'll help narrow down the problem. 

You can safely shutdown or restart from the command prompt by entering the following commands : 

For shutdown
```
 sudo shutdown -h now 
``` 

For restart 
```
 sudo reboot 
```

Regarding the printer connectivity, I'm not sure how to approach it but someone else here will probably help you out soon.


Thanks. So, I'm using Ubuntu 14.04 and just out of curiosity, I went into the tty terminal and upon entering my password, the thing froze!

---

### Post by kansasnoob on 2016-01-27
I suspect a hybrid graphics issue because the specs for that puter show:

Intel HM86
NVIDIA GeForce GTX 860M

I don't have any personal experience with that exact mash-up so I can only provide a link, suspecting that falls into the Optimus category (ignore the AMD stuff):

[https://help.ubuntu.com/community/HybridGraphics#NVIDIA_Optimus](https://help.ubuntu.com/community/HybridGraphics#NVIDIA_Optimus)

I did have some luck with [Bumblebee]("https://wiki.ubuntu.com/Bumblebee#Setup_for_14.04_and_later") on different hardware once, but your mileage may vary.

---

### Post by blade4 on 2016-01-28
This does sound like a GPU issue. But before doing anything , check the system logs and see if there is any error message : 

```
 gedit /var/log/syslog.1 
```

This will open up the log file . You'll want to look for key words like " stuck on render " or "GPU hang". Words like these in the log will definitely mean a bug in your graphics setup. If not, just do a global search for "error" in the log file and let us know what you find. 

BTW the syslog file is constantly updated so when you close it, it'll ask if you wanna save. Choose to "Close without saving" in this case. 

It's also a good idea to check if there are additional drivers available for your setup ( This is a hit or miss thing. For many users it doesn't find any additional drivers but it is a very safe way to install them if it does ). You can look up details in this video : 

[https://www.youtube.com/watch?v=X2ZYaWQFoIc](https://www.youtube.com/watch?v=X2ZYaWQFoIc)

Hope this helps.

Cheers

---

