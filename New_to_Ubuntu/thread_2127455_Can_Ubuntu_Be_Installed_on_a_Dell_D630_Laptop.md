---
title: "Can Ubuntu Be Installed on a Dell D630 Laptop?"
date: 2013-03-20
forum: New to Ubuntu
---

### Post by TomBrooklyn on 2013-03-20
Can Ubuntu be installed on a Dell D630 laptop computer? 


Can it be installed on any Dell laptop computer? 


If so, what is the procedure to do so?

---

### Post by Abhinav Kumar on 2013-03-20
Hi
> **TomBrooklyn said:**
> Can Ubuntu be installed on a Dell D630 laptop computer? 
I searched on the net for this model and it looks this model is a bit older since this is currently unavailable.
[http://www.dell.com/us/dfb/p/latitude-d630/pd](http://www.dell.com/us/dfb/p/latitude-d630/pd)

I think Ubuntu can be installed on this laptop. But, I would like you to first check the system requirements
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)
 You would be glad to know that there is even light-weight Ubuntu (lubuntu) OS available that don't consume much of the resources 
You can also use Ubuntu 10.04 rather than using Ubuntu 12.04 or Ubuntu 12.10

> Can it be installed on any Dell laptop computer? 
No I dont think so. Ubuntu can only be installed on those systems which fulfill the system-requirements criteria.

> If so, what is the procedure to do so?
Please refer
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

Regards,
Abhinav

---

### Post by sudodus on 2013-03-20
[COLOR=#ff0000][/COLOR]According to this link [COLOR=#ff0000]http://www.cnet.com/laptops/dell-latitude-d630/4505-3121_7-32445398.html[/COLOR]

your computer has a core2duo processor and at least 512 MB ram and intel graphics. Ubuntu 12.04 LTS and 12.10 should work, but*** if less than 768 MB ram, you need the alternate iso to make the install CD/USB drive***.

But as indicated by *Abhinav Kumar*, it will run much better with ***Lubuntu*** or ***Xubuntu***, which has the same ubuntu linux engine under the hood, but ultra-light LXDE or light XFCE desktop environments. If you have 2 GB of ram (or more), you will get reasonably good performance running Ubuntu with Unity or Kubuntu with KDE.

***If you have at least 768 MB ram, you should download the standard desktop iso files and try them live before deciding what to install.***

---

### Post by c2tarun on 2013-03-20
> **Abhinav Kumar said:**
> 

[QUOTE=TomBrooklyn;12565693]

Can it be installed on any Dell laptop computer? 


No I dont think so. Ubuntu can only be installed on those systems which fulfill the system-requirements criteria.


Please refer
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

Regards,
Abhinav[/QUOTE]

I think you said 'No' here by mistake. Ubuntu can be installed on all Dell laptop computers which fulfill the system-requirements criteria. I am using ubuntu on dell inspiron N4010

---

### Post by Impavidus on 2013-03-20
> **TomBrooklyn said:**
> Can it be installed on any Dell laptop computer?

English is ambiguous.
If any=every: no
If any=at least one: yes

It depends on the specific hardware, like CPU, RAM, graphics, wifi. If something is incompatible that component may not work satisfactory.

---

### Post by mörgæs on 2013-03-20
In [hardware]("http://ubuntuforums.org/forumdisplay.php?f=332") there are four sticky threads describing what is known to work and known not to work.

Please take a look and feel free to add your observations.

---

### Post by grahammechanical on 2013-03-20
The way we find out if Ubuntu can be installed on our machine is to download an ISO image and burn it to DVD/USB stick and try running it as a Live Session. Things will run a little slower because the operating system is not being loaded from the hard disk but at least we can find out if our hardware (wireless and stuff) is supported. Doing this is a good way to find out if there will be any issues with installing Ubuntu. Then we can research in advance to solve the problems when they happen.

[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)

---

### Post by TomBrooklyn on 2013-03-20
Hi.  Thanks for the informative responses. 

To elaborate a little:
[SIZE=3]**I am shopping for a pre-owned laptop to use primarily for watching internet streaming video wirelessly and portably in my home.** [/SIZE]   In particular, the MIT OpenCourseWare videos and similar ones, if it matters.   


I'm not actually tied to a Dell D630 with 2GB of RAM.    Since posting this thread, I have found several other notebook models from around the same era  (2007ish) that fit the budget and I think will suit the desired purpose.     Some of those are the: 

Dell D620 (precursor to the D630)
Dell E6400 (successor to the D630)
Lenovo Thinkpad T400
HP Elitebook model=?


Also, I may be able to find a notebook with 4GB or more of RAM, which I would greatly prefer to 2GB, which is the minimum I am considering to get.  

**Can Ubuntu or any Linux distros take advantage of more than 3 GB of RAM?**

If I'm not mistaken, only 64bit operating systems can do that.


**It would be a bonus if I could efficiently run Mathcad, Maple, Mathlab or Mathematica, or some GNU equivilent; and google Sketch-Up or some other architectural design and CAD programs. **

---

### Post by oldfred on 2013-03-21
I have a 6 year old Toshiba with 1.5GB of RAM. I run the 64bit version, 1.5GB of RAM is "offically" too small for 64 bit, but it runs full Ubuntu with fallback or gnome-panel not Unity without any real issue. With that amount of RAM I occasionally open too many apps at once and see swap used and some slowdown. 

If you have over 2GB of RAM install the 64bit version. But the 32bit versions will sort of use over 3GB of RAM with PAE, but that is a kluge, but better than not using it at all.
       Linus does not like PAE or 32 bit.
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/)

---

### Post by sudodus on 2013-03-21
> **TomBrooklyn said:**
> Hi.  Thanks for the informative responses. 

To elaborate a little:
[SIZE=3]**I am shopping for a pre-owned laptop to use primarily for watching internet streaming video wirelessly and portably in my home.** [/SIZE]   In particular, the MIT OpenCourseWare videos and similar ones, if it matters.   


I'm not actually tied to a Dell D630 with 2GB of RAM.    Since posting this thread, I have found several other notebook models from around the same era  (2007ish) that fit the budget and I think will suit the desired purpose.     Some of those are the: 

Dell D620 (precursor to the D630)
Dell E6400 (successor to the D630)
Lenovo Thinkpad T400
HP Elitebook model=?

The hardware of a Dell D630 with 2GB of RAM is enough to stream such video, particularly if you have several desktop environments, and select a light-weight one when you need speed, for example lubuntu-desktop (LXDE) or the simple window manager Openbox.
> 

Also, I may be able to find a notebook with 4GB or more of RAM, which I would greatly prefer to 2GB, which is the minimum I am considering to get.  

**Can Ubuntu or any Linux distros take advantage of more than 3 GB of RAM?**

Yes, with pae it takes care of 4 GB of RAM without problems> 

If I'm not mistaken, only 64bit operating systems can do that.
With more than 4 GB of RAM, you are definitely better off with 64 bit systems. But don't worry about it. Download iso files of both versions (32 and 64 bits) and try them live (booted from the install CD/DVD/USB drive) before you decide what to install. Furthermore, consider more flavours than standard Ubuntu: Lubuntu, Xubuntu, Kubuntu :-)> 

**It would be a bonus if I could efficiently run Mathcad, Maple, Mathlab or Mathematica, or some GNU equivilent; and google Sketch-Up or some other architectural design and CAD programs. **

Most of those programs have been around long enough to be possible to run on rather old hardware.

---

### Post by PhilGil on 2013-03-21
Many of the older machines you're looking at only have 32 bit processors. As oldfred mentioned, Linux can utilize more than 3 GB of RAM using a hack called PAE. Linux is quite memory efficient - most distros can run comfortably with only 2GB of RAM, and more than 4GB is overkill unless you have a special need for it.
 
I'm running a Dell E4300 (equivalent to the E6400 but a smaller screen) with a Core2 Duo processor and 2GB of RAM. I'm not running Ubuntu at the moment, but I am running Debian 7.0, which is very similar under the hood to Ubuntu 12.04 LTS. Everything worked "out of the box" on my machine, and I'm having no problem running a full, 3D composited desktop environment (in my case, Gnome Shell). The only issue you may run in to with the Latitude E4300, E5400, E6400 line is that some of them shipped with Broadcomm wireless cards, which are notoriously hard to get working in Linux. It can be done, but it takes some extra work.

The Thinkpad line is reputed to have good Linux compatibility, but I don't have any personal experience to back that up.
 
 As far as graphics programs go... Just bear in mind that you're talking about a 4-6 year old laptop with a mobile processor.  You could probably run 3D modeling or CAD software but I wouldn't expect miracles.

---

### Post by mitmag on 2013-03-21
It most certainly can.
I run Version 10.04 LTS and Version 12.04 LTS on a Dell D620.
I have no problems at all. Just use normal installation procedure.
Hope this helps.

---

### Post by DanPerecky on 2013-05-13
> **grahammechanical said:**
> The way we find out if Ubuntu can be installed on our machine is to download an ISO image and burn it to DVD/USB stick and try running it as a Live Session. Things will run a little slower because the operating system is not being loaded from the hard disk but at least we can find out if our hardware (wireless and stuff) is supported. Doing this is a good way to find out if there will be any issues with installing Ubuntu. Then we can research in advance to solve the problems when they happen. 

[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)

Have an IBM Thinkpad X60s with 2GB of RAM [http://support.lenovo.com/en_US/downloads/detail.page?DocID=PD000842](http://support.lenovo.com/en_US/downloads/detail.page?DocID=PD000842). Pics at: [http://www.google.com/search?hl=en&site=imghp&tbm=isch&source=hp&biw=1232&bih=657&q=ibm+thinkpad+x60s&oq=ibm+thinkpad+x60s&gs_l=img.3..0j0i24l4.2804.7243.0.7552.17.14.0.3.3.0.299.1811.9j2j3.14.0...0.0...1ac.1.12.img.FLLwWtCskDc](http://www.google.com/search?hl=en&site=imghp&tbm=isch&source=hp&biw=1232&bih=657&q=ibm+thinkpad+x60s&oq=ibm+thinkpad+x60s&gs_l=img.3..0j0i24l4.2804.7243.0.7552.17.14.0.3.3.0.299.1811.9j2j3.14.0...0.0...1ac.1.12.img.FLLwWtCskDc)

Loaded a 4GB _USB _Flash Drive with vrs. 12.04. Changed the BIOS to load from the USB Flash Drive first. It just hung when the PC started.

Taking advice from SSULLY at [http://ubuntuforums.org/showthread.php?t=1547323&p=10256929#post10256929](http://ubuntuforums.org/showthread.php?t=1547323&p=10256929#post10256929) I loaded a different 4GB Flash Drive with UBUNTU vrs. 10.10. This version _*ran great*_ right out of the box.

The procedure to create a bootable USB is here: [http://www.youtube.com/watch?v=o_02Ca5LJpg](http://www.youtube.com/watch?v=o_02Ca5LJpg)

Found UBUNTU 10.10 at [http://linux.softpedia.com/](http://linux.softpedia.com/), and used 11.x (.something) in the NetBootin selection, as 10.10 was not listed for some interesting reason. NetBootin worked fine, as the PC booted vrs 10.10 w/no problems from my USB 4GB Stick (which only used 800mb).

I hope this helps.

---

### Post by mörgæs on 2013-05-13
Both 10.10 and 11.* are out of support and should not be used. A light 13.04 like Xubuntu is a better choice.

---

### Post by VinDSL on 2013-12-07
> **TomBrooklyn said:**
> [...] I may be able to find a notebook with 4GB or more of RAM, which I would greatly prefer to 2GB, which is the minimum I am considering to get.  

Can Ubuntu or any Linux distros take advantage of more than 3 GB of RAM?

If I'm not mistaken, only 64bit operating systems can do that.
Sorry, for being late_to_the_party...

I don't normally reply to 'old' threads, but the Dell Latitude D620/D630 series are arguably the best selling Dell laptops of all time.  They're built like tanks, and I have a *feeling* they'll be around for a long time.

I am running a Lubuntu fork (Peppermint 4 OS, 64-bit) on both a D620 & ATG D630; currently on top of a Linux 3.13-rc3 'Trusty' kernel.  Both of them work great.

To answer the RAM question directly:

[LIST]
[*]The D620 will recognize 4GB (2x2GB) RAM, but due to a bug in the BIOS chip, only 3GB is usable.  So, on the D620 I run 2GB in the A-socket, and 1GB in the B-socket.  It'll work fine with 2x2GB RAM installed, but it's a waste of resources, since only 3GB is usable.


[*]The ATG D630 will recognize 8GB (2x4GB), with certain BIOS firmware.  However, 4GB SODIMMs are pretty expensive  ($150-$200 for the pair, at last check) so the sweet_spot IMO is 4GB (2x2GB), all of which is usable, minus a small amount of overhead.  AFAIK, all D630 BIOS firmware will recognize/use the full 4GB RAM.
[/LIST]
Bottom line:  

[LIST]
[*]You can run 64-bit Ubuntu et al. on both the D620 & D630.


[*]Usable RAM on a D620 is 3GB -- usable RAM on a D630 is 8GB -- 4GB being the most cost-effective.
[/LIST]

---

### Post by VinDSL on 2013-12-07
> **PhilGil said:**
> The only issue you may run in to with the Latitude E4300, E5400, E6400 line is that some of them shipped with Broadcomm wireless cards, which are notoriously hard to get working in Linux. It can be done, but it takes some extra work.
I know we're talking apples n' oranges here, but...

Regarding Ubu on the D620/D630 -- I've had the best luck using the lowly Dell 1390 WLAN mini-card (Broadcom) via b43 drivers -- works great, no blinking WIFI LED, et cetera.  Just saying.

I just snapped some screenies of my ATG D630, if anyone is interested:

[[IMG]http://vindsl.com/images/vindsl-desktop-7-dec-2013-1(650x407).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-7-dec-2013-1.png")


[[IMG]http://vindsl.com/images/vindsl-desktop-7-dec-2013-2(650x407).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-7-dec-2013-2.png")


The Conky widgets on the right-side pretty much tell it all.

If you look at the bottom panel, you'll see two battery icons.  I'm running a 9-cell primary battery, and a 6-cell secondary.

Also, you might notice the green WIFI icon on the bottom panel looks different.  I run WiCD for the network manager.  Can't stand NM.

Oh, and one last thing.  Conky reports the 2.6GHz C2D CPU is loafing along @ 0.80GHz.  It automagically does this to save the batteries and reduce heat (46C/47C reported in the lower panel) when the extra power isn't needed.

There's a lot of life left in these things.  They're the '55 & '57 Chevies of Dell computers... ;)

---

