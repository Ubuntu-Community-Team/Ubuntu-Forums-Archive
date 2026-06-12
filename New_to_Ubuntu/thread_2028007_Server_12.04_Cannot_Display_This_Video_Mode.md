---
title: "Server 12.04 Cannot Display This Video Mode"
date: 2012-07-17
forum: New to Ubuntu
---

### Post by ChaLug on 2012-07-17
Optimum Resolution 1280x1024 60Hz
 
I have installed Ubuntu Server 12.04 x86 on an old Dell PowerEdge 2600.
 
Once installed; I decided that I wanted a GUI.  I followed the instructions on [this]("http://www.ubuntugeek.com/how-to-install-gui-on-ubuntu-12-04-precise-server.html") site.
 
Once I installed everything according to that site; I restarted the server: $ sudo reboot
 
Once the server reboots; I get the following on a black screen:
 
Cannot Display This Video Mode
Optimum resolution 1280x1024 60Hz
 
I have Google'd the heck out of this and found sites suggesting using "xrandr" to set the resolution to something else.  However; whenever I run "xrandr" from a terminal (CTRL-ALT-F1), I get a message "Can't open display".
 
Can anyone tell me what I can do to get my GUI?! :D
 
Thank you!

---

### Post by Cheesemill on 2012-07-17
If you are going to install ubuntu-desktop on a server then you might as well just install the Desktop version of Ubuntu in the first place, you end up with exactly the same thing.

Try booting from a Ubuntu desktop Live CD and see if you get any errors.

---

### Post by jmfal on 2012-07-17
Welcome to Ubuntu
The specs for you graphics card are:
Integrated ATI-Rage XL controller with 8MB of SDRAM

I may be wrong but I don't think that is enough to run gnome desktop.

If it is a tower you have a PCI slot and they srill sell pci graphics cards
[http://www.tigerdirect.com/applications/Category/guidedSearch.asp?CatId=28&sel=Detail%3B55_158_2872_2872](http://www.tigerdirect.com/applications/Category/guidedSearch.asp?CatId=28&sel=Detail%3B55_158_2872_2872)

---

### Post by ChaLug on 2012-07-17
> **Cheesemill said:**
> If you are going to install ubuntu-desktop on a server then you might as well just install the Desktop version of Ubuntu in the first place, you end up with exactly the same thing.
 
Try booting from a Ubuntu desktop Live CD and see if you get any errors.
 
Really? It is the same thing?
 
I had kind of thought about doing that but I am putting this in a server environment and did not want the extra overhead of a full desktop. The option I took from the link I provided had a noinstall-recommended.
 
I suppose the server version is simply leaner and more locked down than the desktop version. I would prefer that but would also like a GUI.
 
I am going to try the LiveCD...

---

### Post by ChaLug on 2012-07-17
> **jmfal said:**
> Welcome to Ubuntu
The specs for you graphics card are:
Integrated ATI-Rage XL controller with 8MB of SDRAM
 
I may be wrong but I don't think that is enough to run gnome desktop.
 
If it is a tower you have a PCI slot and they srill sell pci graphics cards
[http://www.tigerdirect.com/applications/Category/guidedSearch.asp?CatId=28&sel=Detail%3B55_158_2872_2872](http://www.tigerdirect.com/applications/Category/guidedSearch.asp?CatId=28&sel=Detail%3B55_158_2872_2872)
 
I believe you have hit the nail on the head.  LiveCD errored out on video.  #-o
 
I am going to order a PCI card.
 
There's still life in the old lady yet!
 
I'll post back if this works.

---

### Post by jmfal on 2012-07-17
Good
You should check the newegg site  they may have same /better prices.

---

### Post by Cheesemill on 2012-07-17
Why do you want a GUI in the first place?

It's best to run a server without one.

---

