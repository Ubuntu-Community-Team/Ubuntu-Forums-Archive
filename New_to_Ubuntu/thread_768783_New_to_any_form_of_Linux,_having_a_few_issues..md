---
title: "New to any form of Linux, having a few issues."
date: 2008-04-26
forum: New to Ubuntu
---

### Post by FrEaK40 on 2008-04-26
So, I'm dual booting Vista & Ubuntu 8...

anyways, so far I love ubuntu but there is a lot of things I need to get done and I was hoping you guys could help me ><. I have a bit of a list of things I want to sort of get through... but I'm having troubles.

LAPTOP: Asus W7S - A1W

EDIT: the ":D" is really : D with no space :S
A) Bluetooth mouse (ASUS) does not work, when I try to connect to the mouse through the device manager (browse devices) I get an error saying
"Couldn't display "obex://
[00:0F:F6:66:07:DA]/".
Error:Host down
Please select another viewer and try again."
Also have tried hcitool scan & sudo hcitool scan, neither pick up the mouse

B) Any other drivers I may need? everything seems to be in a general working order.

C) This stupid fish, I hit ALT+F2 and wrote "Free the Fish" or something like that and this fish will not go away, I'm going to huck my entire laptop out the window, I'm SO SICK OF LOOKING AT HER!

D) Video codecs I may need.


Thanks in advance guys, any help would be greatly appreciated, I'm a total noob with Ubuntu/Linux but I'm eager to learn and love it so far.

---

### Post by philinux on 2008-04-26
Click the medibuntu link for codecs. Best to use copy and paste in the terminal.

---

### Post by FrEaK40 on 2008-04-26
> **philinux said:**
> Click the medibuntu link for codecs. Best to use copy and paste in the terminal.

TY ^^ thats one off the list

---

### Post by philinux on 2008-04-26
The fish.

[http://ubuntu-tutorials.com/2007/07/09/a-few-gnome-easter-eggs/](http://ubuntu-tutorials.com/2007/07/09/a-few-gnome-easter-eggs/)

---

### Post by duckgoesoink on 2008-04-26
> **FrEaK40 said:**
> C) This stupid fish, I hit ALT+F2 and wrote "Free the Fish" or something like that and this fish will not go away, I'm going to huck my entire laptop out the window, I'm SO SICK OF LOOKING AT HER!

Heh, you did that too? Mine went away when I logged out I think...

---

### Post by Michael.Godawski on 2008-04-26
> B) Any other drivers I may need? everything seems to be in a general working order.

You can check if there are drivers inactive in 
System > Administration > Restricted Driver Manager (Hardware Manager)

> C) This stupid fish, I hit ALT+F2 and wrote "Free the Fish" or something like that and this fish will not go away, I'm going to huck my entire laptop out the window, I'm SO SICK OF LOOKING AT HER!

[http://ubuntuforums.org/showthread.php?t=499761](http://ubuntuforums.org/showthread.php?t=499761)

> 
D) Video codecs I may need.

In terminal
```

sudo apt-get install ubuntu-restricted-extras
```

---

### Post by ugm6hr on 2008-04-26
Have a look at the multimedia link in my signature for a complete guide to media on Ubuntu.

Drivers are generally automatically loaded by the Linux kernel, if they exist.  So extras are generally unnecessary.  The exception is video cards, which tend to have proprietary drivers available, which sometimes allow extra functions.  Envy is the only easy way to get hold of the latest nvidia / ati drivers (if you want them - see the graphics card link below).

Don't know about the Fish thing.

Not sure about the mouse either.

---

### Post by FrEaK40 on 2008-04-26
okay, thanks for all the info guys :D


anyone got any ideas for the mouse though? I hate trackpads so much ><

EDIT: ugm6hr, your graphics card driver link is down (Page not found)

---

### Post by anjilslaire on 2008-04-26
Wanda is pretty cool. Does anyone know of any easter eggs in KDE, btw? Anything similar?

---

### Post by FrEaK40 on 2008-04-26
> **anjilslaire said:**
> Wanda is pretty cool. Does anyone know of any easter eggs in KDE, btw? Anything similar?

a little off topic =\

lol, still nothing on the mouse eh? guess I'll just learn it me-self

---

### Post by Ponomous on 2008-04-26
Bluetooth has been buggy in the latest release, not sure why but I have a bunch of friends who have similar problems with their stuff.  Hopefully someone will find a fix.  Please post here if you end up finding an answer.

---

### Post by philinux on 2008-04-26
Have a read through this..

[https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/148712](https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/148712)

---

### Post by FrEaK40 on 2008-04-26
> **philinux said:**
> Have a read through this..

[https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/148712](https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/148712)

ah,
well apparently there is no workaround for this with HH yet =\

---

