---
title: "Ubuntu Minimal install problems"
date: 2012-05-06
forum: New to Ubuntu
---

### Post by roodypoo on 2012-05-06
I've installed Ubuntu minimal. I have a few problems.

I downloaded truecrypt's .deb file, but I can't install it. Clicking on it does nothing. The executable bit is set. I tried install Ubuntu software center, but it will not start either. A crash report comes up.
 
In the upper corner the network manager says it is not connected, but it is.

After the install I installed (from the command line)

apt-add-repository ppa:gnome3-team/gnome3

python-software-properties
gnome-shell
gdm
gnome-terminal
ubuntu-software-center
firefox

What else should I add?

Thanks

---

### Post by Cheesemill on 2012-05-06
Try installing it from a terminal:
```
dpkg -i truecypt.deb
```

---

### Post by roodypoo on 2012-05-06
Sorry, I had to extract it first.

---

### Post by Paqman on 2012-05-06
> **roodypoo said:**
> Sorry, I had to extract it first.

Er, that's probably not the best way of doing it. You can extract from .debs, but if you do so you won't be able to upgrade or uninstall it using your package manager.

Did you try Cheesemill's suggestion?

---

### Post by Bucky Ball on 2012-05-06
I think you need to install gdebi. I was having the same trouble with a minimal install I've recently done tonight. Couldn't get debs to automagically install. 

Yea, just had a look. Install gdebi and try again. Do you have Synaptics installed? Makes things a little easier. ;)

```
sudo apt-get install synaptic
```

Just out of curiousity: What was the package list you installed after the base system installed? The part where you add the packages and apps you want, if you follow me?

---

### Post by roodypoo on 2012-05-06
My minimal install is not much smaller than the standard and the memory footprint is about the same.

Is that normal?

Paqman,

I did, but it did not install until I added gdebi per Bucky's recommendation.

Bucky,

I did not select any. Just added things from the command line after install.

---

### Post by Bucky Ball on 2012-05-06
> **roodypoo said:**
> Bucky,

I did not select any. Just added things from the command line after install.

Yea, that's what I'm talking about. What was the list of things you added at the command line? If you added virtually everything that is in a regular Ubuntu install, yes, it would be about the same size. My mini install takes up less than 3Gb from memory. I have installed probably less than a dozen apps though. Check in Gparted for used and unused space on the mini install partition.

---

### Post by Paqman on 2012-05-07
> **roodypoo said:**
> My minimal install is not much smaller than the standard and the memory footprint is about the same.

Is that normal?


Totally depends on what packages you install. If you take the minimal image and add things like ubuntu-desktop then it will actually be exactly the same as a regular install.

In your case you've installed a lot of the full Gnome3 based desktop, so I wouldn't expect it to be particularly light. Gnome Shell isn't a lightweight environment.

---

### Post by Bucky Ball on 2012-05-07
> **Paqman said:**
> Totally depends on what packages you install. If you take the minimal image and add things like ubuntu-desktop then it will actually be exactly the same as a regular install.

In your case you've installed a lot of the full Gnome3 based desktop, so I wouldn't expect it to be particularly light. Gnome Shell isn't a lightweight environment.

+1. I have xfce4 and not much installed. Runs like a rocket on a ten year old machine with 1Gb RAM, single core AMD processor and two IDE drives (prob 5400s). Never been better ...

If you install ubuntu-desktop may as well do a regular install ... ;)

---

### Post by Paqman on 2012-05-07
> **Bucky Ball said:**
> 
If you install ubuntu-desktop may as well do a regular install ... ;)

There are actually good reasons to do that. If you're installing a version that's been out for a while it saves installing a bazillion updates right after installing, as you're using the latest packages instead of whatever old ones are on the install image. If you're on metered bandwidth you could save yourself hundreds of MB.

---

### Post by Bucky Ball on 2012-05-08
> **Paqman said:**
> There are actually good reasons to do that. If you're installing a version that's been out for a while it saves installing a bazillion updates right after installing, as you're using the latest packages instead of whatever old ones are on the install image. If you're on metered bandwidth you could save yourself hundreds of MB.

All true but not really the point of a minimal install, which is where OP is coming from. The system will run about the same speed and take up about as much space as a regular install once you install ubuntu-desktop on/in a minimal install. May as well just install the desktop edition to start with ... ;)

---

