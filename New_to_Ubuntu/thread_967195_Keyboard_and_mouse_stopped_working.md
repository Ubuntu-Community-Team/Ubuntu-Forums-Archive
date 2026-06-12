---
title: "Keyboard and mouse stopped working"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by Metaxa on 2008-11-01
Hello folks, 

I recently upgraded to 8.10. Once the machine did its thing, I shut it down for the night. This morning I turned on my machine and made it to the log in screen, but mouse and keyboard don't type anything or move. I can ctrl-alt-del to restart, but nothing else happens. I can provide any information you all may need to lend a hand.


Metaxa

---

### Post by 666porcondissaum on 2008-11-01
Same thing happenned to me, but no log screen... it just got static. Replies are welcome!!!!

---

### Post by Metaxa on 2008-11-02
Hey folks,

I have tried  the recovery mode choice in start up and nothing has changed. Any help would be great.

Metaxa

---

### Post by Crafty Kisses on 2008-11-02
If there's anyway you can get this command into the terminal with your Linux box, it would be really helpful:
```
lsusb
```

---

### Post by Metaxa on 2008-11-02
bus 004 Device 001: ID 1d6b:0001
Bus 003 Device 001: ID 1d6b:0001
Bus 002 Device 001: ID 046d:c03d Logitech, Inc.
Bus 002 Device 001: ID 1d6b:0001
Bus 001 Device 001: ID 1d6b:0002



This is what I get

---

### Post by Metaxa on 2008-11-02
Any other information I can offer?

---

### Post by Metaxa on 2008-11-03
Some other information I thought might be useful.

My system has a ps/2 keyboard and usb mouse. 

I can get to the log in screen with a blinking cursor where I would normally type my user name.

When I go into recovery mode for any of the three kernels available to me, they try connecting to the internet but can't connect.

---

### Post by Metaxa on 2008-11-03
Bump for some help

---

### Post by K-D on 2008-11-04
Same problem,

I was using a wireless mouse and keyboard.

I switched it to a usb keyboard and mouse and I could enter information and get logged in.

However the mouse and keyboard only worked for about 2/3 mins then stopped.....not to scare anyone but since I cannot even get anything up and my screen (no signal by all accounts)

ive lost my boot disk so I am screwed!

---

### Post by K-D on 2008-11-04
I found this other forum which may be of help to those who it has affected:

[http://ubuntuforums.org/showthread.php?t=943909&highlight=keyboard+mouse+stopped+working](http://ubuntuforums.org/showthread.php?t=943909&highlight=keyboard+mouse+stopped+working)

---

### Post by handydan918 on 2008-11-04
> **Metaxa said:**
> Hello folks, 

I recently upgraded to 8.10. Once the machine did its thing, I shut it down for the night. This morning I turned on my machine and made it to the log in screen, but mouse and keyboard don't type anything or move. I can ctrl-alt-del to restart, but nothing else happens. I can provide any information you all may need to lend a hand.


Metaxa

monitor keyboard and mouse are all functions of the xserver, so why not try ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Hardly seems likely to hurt anything....

And just to get this straight, you can log into a console, correct?

---

### Post by Metaxa on 2008-11-04
Yes I can use xserver. I tried what you said and still can't log in. I also followed the links provided and I had the same problem as the last poster.

---

### Post by K-D on 2008-11-05
I have now managed to get an input signal back to my monitor....I think the nights sleep did it well.

However My machine now goes into a check because it has been booted 38 times without it being checked (im pretty new to Ubuntu).  It freezes half way through and I can't get to the log in page to attempt to fix the keyboard and mouse problem.

Any ideas on how to by pass this automatic saftey check?

:confused:

---

### Post by Metaxa on 2008-11-06
Pump for some help

---

### Post by K-D on 2008-11-07
This is driving me crazy now and no one seems to have an answer!

I can occasionally get the boot menu to appear on my monitor but if i boot as normal i can get logged on and it eventually crashes (freezes).

For some reason the majority of times I attempt to boot up no signal goes through to my monitor.

I have managed to acquire a boot disk of 7. something.  Is this a more stable version that isn't going to destroy my degree???????

Also how do I enter the bios on Ubuntu so I can attempt to boot from disk rather than my hard drives??

any help or advise would be very helpful!:)

---

