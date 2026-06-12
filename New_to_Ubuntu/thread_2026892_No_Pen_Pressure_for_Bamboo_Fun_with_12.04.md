---
title: "No Pen Pressure for Bamboo Fun with 12.04"
date: 2012-07-15
forum: New to Ubuntu
---

### Post by StardustLuna on 2012-07-15
Hello there, if my post count doesn't make it obvious, I am brand-spanking new to these forums and Ubuntu. I installed it yesterday on my computer after windows decided to hate me. For the most part I love it, but I have one problem for which I can't find a simple in-plain-english solution for, my Bamboo Fun tablet is not registering pen pressure in GIMP. 

Apparently my version of Ubuntu came pre-loaded with a wacom tablet program that let's you choose settings for buttons and such, but after fiddling with that I'm still getting life-less lines. I looked through some of the other similar threads, but the solutions I found were a tad too advanced for me. 

I appreciate any help, but as I said above, I'm still learning my ABC's with Ubuntu and such. Especially the file system, it's kind of a shock after using Windows for so long. If the solution is one in which I have to mess with the code, please bear with me and all of my obvious questions. 

And here are my specs in case it's something to do with hardware:
Ubuntu 12.04
HP Pavilion dv7
Intel core i7
Intel SandyBridge Mobile


~Stardust.

---

### Post by anewguy on 2012-07-15
The first thing you should do is a net search.  I turned this up, but have no idea how current it is (I know that xorg has changed so you really don't create the xorg.conf file but instead put different options in different files) nor what you may need to change to be ubuntu specific:

[http://https://wiki.archlinux.org/index.php/Wacom_Tablet]("http://https://wiki.archlinux.org/index.php/Wacom_Tablet")

---

### Post by Favux on 2012-07-15
Hi StardustLuna,

Welcome to Ubuntu forums!

Your model should be supported in Precise (12.04).  But to be sure open a terminal and run this command:
```
lsusb
```
and post the line with Wacom in it.

I think all you need to do is configure Gimp.  In Gimp go to Edit > Preferences > Input Devices >  Configure Extended Input Devices and set the stylus and eraser (in Device drop down) to Screen (in Mode drop down).  And you need to do something similar in Inkscape.

---

### Post by StardustLuna on 2012-07-16
Thanks for the help! Apparently I had to just adjust the settings in GIMP. I had a sneaking suspicion but I was having trouble getting the bar at the top to show file, edit, help, etc so I figured it was something else. :P 

However, once I get home I'll have my PhotoShop CD and want to make sure it'll work with that too. 

So here's the line that you mentioned Favux. 

```
Bus 003 Device 002: ID 056a:0017 Wacom Co., Ltd Bamboo Fun 4x5

```

---

### Post by Favux on 2012-07-16
Glad you have pressure in Gimp now.  Right, to get the stuff in the bar at the top you have to make sure it is Gimp in focus not something else.  You'll get used to that quickly.

Thanks for the lsusb line.  That model Bamboo should be totally supported alright.

---

### Post by StardustLuna on 2012-07-16
Good to hear! And yes, the more I mess around with it, the more I'm getting used to it.

---

