---
title: "ATI Rage IIC integrated graphics driver"
date: 2016-10-09
forum: New to Ubuntu
---

### Post by new-york-giant on 2016-10-09
I recently "inherited" a stack of various HP ProLiant SCSI servers. I became interested in seeing what these machines could do and I started doing research on these "beasts". I learned that they supported other operating systems besides MS Server, and, through much more research (and trial and error), I have finally successfully installed Ubuntu 16.04 LTS on an HP ProLiant ML570 G2 SCSI i368 server. The graphical interface seems choppy and I am wondering if I have the latest display driver installed. How would I know if I have the latest driver installed, and if not, how would I find the driver and how do I install it? AMD has a driver update utility for discontinued ATI Rage series products for MS operating systems only.

---

### Post by Mark Phelps on 2016-10-09
Sadly, you're probably out of luck with Ubuntu 16.04.

AMD has discontinued support for their Linux fglrx drivers for it -- so those are not an option.

The older drivers will not work with the kernel versions present in 16.04 -- so those are not an option.

And the new drivers that AMD is developing are only for the brand new AMD hardware -- so those are not an option.

To find an fglrx driver that would work for the ATI Rage series, you'd have to go back lots of years, maybe all the way back to 8.04.

---

### Post by mastablasta on 2016-10-10
> **new-york-giant said:**
> I recently "inherited" a stack of various HP ProLiant SCSI servers. I became interested in seeing what these machines could do and I started doing research on these "beasts". I learned that they supported other operating systems besides MS Server, and, through much more research (and trial and error), I have finally successfully installed Ubuntu 16.04 LTS on an HP ProLiant ML570 G2 SCSI i368 server. The graphical interface seems choppy and I am wondering if I have the latest display driver installed. How would I know if I have the latest driver installed, and if not, how would I find the driver and how do I install it? AMD has a driver update utility for discontinued ATI Rage series products for MS operating systems only.

not sure what you planned ot use these for. the opensoruce radeon drivers probably offer only 2D hardware acceleration. while for 3D the CPU is used, which makes Unity found in Ubuntu (using 3D) sluggish. 

so the options 
1 - install Lubuntu or Xubuntu. they both use 2D desktop. Mate also has it.
2 - use various fall back options in deskotp. e.g. in KDE you can turn of all special effects, Unity may have some gnome fallback session avaiable.
3 - if you plan to use it for server, just install the server version. who needs desktop on server? it is just another attack vector.
4 - there are plenty window managers that are 2D (i3, icewm, jwm...)

---

### Post by mörgæs on 2016-10-10
I bought an ATI Rage in 1999, I believe, and it was considered a low-end graphics processor at that time. 

In 2016 you should expect this GPU to be able to display only the simplest kind of graphics. It's suitable for a text-only interface like on a typical server but not much more. 

If you want modern type graphics then a newer graphics card is the best option. It's not a matter of drivers.

---

