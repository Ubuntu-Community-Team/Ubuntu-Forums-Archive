---
title: "Installed Skype application doesn't launch."
date: 2015-05-24
forum: New to Ubuntu
---

### Post by 4ntonio.p3r3ira on 2015-05-24
I downloaded Skype for Linux from the official site installed it, it looks ok but when I try to launch the application I click on it and nothing happens. 
It seems that the last version supported by them its the 12.04.. Could it be because of it?
Is there any line of code that I need to plug in for it to work?

I have the 14.04 LTS installed.

Thanks for the help again. =D

---

### Post by DirtDawg on 2015-05-24
Try running the program via command line and see if there are any errors. Try using those errors to solve the problem, or post them here to see if anyone can help decipher them.

Otherwise, installing Skype from the Ubuntu Software Center *may* help. I'm not sure if you need to uninstall the version you have first. (If you don't see it in the Software Center, in Software Center, click Edit> Software Sources, then under the Other Software tab make sure both Canonical Partners check boxes are ticked. Then, close Software Center, open a terminal and enter 'sudo apt-get update'. After it's finished refreshing, open Software Center again and look for Skype.)

---

### Post by Bucky Ball on 2015-05-25
Install the version that is known to work with your release from the official Ubuntu repositories (Software Centre or Synaptics).

---

### Post by 4ntonio.p3r3ira on 2015-05-30
Thanks for the reply's I'll be trying to mend it tomorrow hope i can do it.

---

### Post by craig10x on 2015-05-30
I'd remove the one you installed FIRST and then grab it from the ubuntu software center...

---

### Post by cariboo on 2015-05-30
> **craig10x said:**
> I'd remove the one you installed FIRST and then grab it from the ubuntu software center...

Make sure you use the option to completely remove skype. If you only remove skype, the configuration files won't be removed, which may lead to more problems.

---

### Post by tristan16 on 2015-05-30
> **Bucky Ball said:**
> Install the version that is known to work with your release from the official Ubuntu repositories (Software Centre or Synaptics).

I just double-checked, and there is _no Skype program in the Ubuntu Software Centre._ All I could find were plugins for Empathy or Pigdin. The only way to install is from the .deb file on Skype.com.

I really hope Microsoft updates the Skype application within the next few years. 12.04 is coming up on EOL next year, and the program is very outdated.

---

### Post by craig10x on 2015-05-30
You have to go to software and updates (find that using the dash search) and under the "other software" tab check the 2 boxes that say Canonical Partners...then close it (as you do that it will tell you to hit the refresh button)...Then, when you open the ubuntu software center you will see skype...that will bring it in...

And like cariboo said...use the synaptic package manager first, bring up the skype you have installed and ask it to remove it COMPLETELY (including configuration files) BEFORE you go to the Ubuntu Software Center to install Skype...

---

### Post by Mike_Walsh on 2015-05-31
I would take Cariboo & Craig's advice.....making absolutely certain to remove every trace of the Skype you installed, and making sure to check the 'Canonical Partners' tick-boxes on the 'Other Software' tab in 'Software & Updates'.

Then, through the terminal:-

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Followed by:-

```
sudo apt-get install skype
```


Works for me every time.


Regards,

Mike.

---

### Post by mastablasta on 2015-06-01
or try to start it like this (copy the command we can help you make launcher later):

```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
```

---

### Post by 4ntonio.p3r3ira on 2015-06-01
I've installed it correctly now. The problem is i have no idea how I made it work. LOL. 
I cleaned all the installed files and did it again, it still didn't work, so I did it again. And then again, and on the 3rd time I was browsing trough the application center and tried to launch it again and it worked. (?!) I did reset the computer on every step.

---

### Post by mastablasta on 2015-06-01
mark thread as solved then.

Linux works in mysterious ways.

---

### Post by 4ntonio.p3r3ira on 2015-06-01
Yeah. Its solved I just don't know how.

---

