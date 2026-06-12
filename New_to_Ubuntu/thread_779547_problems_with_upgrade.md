---
title: "problems with upgrade"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by bob8170 on 2008-05-02
So last week I upgraded to 8.04. I have not been able to get it to work. I was running Gutsy just fine and now I cannot get it to load. Here is my problem:

When I turn on the computer it goes through the normal motions. When it asks for my username and password it acts like it is trying and then it restarts, again asking for my username and password. I've been caught in this loop and kept trying numerous times.

If I go into Grub and use the older kernal (2.6.20-16) it will load fine. However, wheneve I try to boot 2.6.24.16 or .14 it goes into this loop. I have a feeling it has something to do with my ATI Radeon xpress200 video card because I know that has been a problem n the past. When I try to go into xorg usingthe old command (sudo reconfig...xorg...) it will allow me to config the keyboard and mouse but not the graphics card. 

It does seem to be working fine using the kernal 2.6.20.16 but it has become a pain to have to go into grub evertime the computer restarts.

Does anyone know what to do? I am using a AMD 64 3500+ processor with the above stated graphisc card.

Any help would be appreciated.

Probably important to mention. I did get 8.04 through upgrade versus doing a clean install.

---

### Post by tjwoosta on 2008-05-02
well if i were you the first thing i would try would be to backup all my important data on a couple of dvd's and just do a clean install of hardy

just for future refrence ive found that alot of the time when trying to upgrade an existing OS things go wrong.

id say the safest way to do an upgrade would be to partition your harddrive and just install the new version beside the old one, rather than trying to upgrade the existing one
(that way its all a clean install and if something goes wrong you can fall back to the other one)

after you have the new version beside the old one you can just mount the partition with your old one on it and move the files over to the new one fairly simple then delete the old partition and expand the newer one

---

### Post by empthollow on 2008-05-02
have you tried to edit the xorg.conf file manually?  you can try vesa or ati where it says driver.  I haven't run into this specifically so i can't suggest a definitive solution.

---

### Post by bob8170 on 2008-05-02
> **empthollow said:**
> have you tried to edit the xorg.conf file manually?  you can try vesa or ati where it says driver.  I haven't run into this specifically so i can't suggest a definitive solution.

I'm not sure on how to edit the xorg.conf file. I will search it now but if you could offer any help it would be much appreciated. 

I am a prime example of a little knowledge being a dangerous thing!

---

### Post by empthollow on 2008-05-02
probably be easiest to use the live cd for this.  If you can get to a terminal in your system you can type the following exactly.
sure, open a terminal and type 
```
sudo nano /etc/X11/xorg.conf
```
find a section that looks like this:
```
Section "Device"

	# 
    Identifier     "device1"
    Driver         "drivername"
    BusID          "PCI:1:0:0"
EndSection
```

on the line that says 'Driver' you want to change the word drivername (in my example) to either 'ati' or 'vesa'
if you have an ati card, 'ati' should work but vesa is a generic will work with any video card driver.

not really sure if changing the xorg will help but it's a good place to start.

---

### Post by bob8170 on 2008-05-02
Thanks for the help!

I actually got it to work by going through system>Hardware Driver>ATI in the kernal I was in. It now seems to be working fine. The computer restarts fine so I assume I am using the most recent kernal. I am fairly sure Compiz will not work but I'll save that for another day:confused:

I'll change this to solved.

Thanks Again!

---

### Post by empthollow on 2008-05-02
yeah, ati is at the beginning of supporting AIGLX which is what compiz needs to run both glx and direct rendering. I believe the ubuntu driver does have this support so you should be able to run it.  you probably will need to edit xorg.conf and add some extra lines but i'm made it work.

---

