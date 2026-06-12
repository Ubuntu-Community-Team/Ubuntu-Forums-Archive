---
title: "did I get a corrupted copy or what...?"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by 83k1500 on 2008-11-18
Ok. So I decided to give ubuntu another try, I am getting out of gaming so that is no longer a major factor.
However... I spend 5 hours each downloading it all of 4 times, from different sources/mirrors.
I spend 10 (yes 10) disks to try to get it to burn and verify. When I finally do get it to burn and verify I go to install it on my rig.
It does not install.
It goes through a few screens, never to the normal set up screens however.
Right now it is sitting at a screen at a command prompt with ubuntu@ubuntu$

So what exactly is going on here?
I downloaded 8.10x64.
System is a PD 775 DC 3.0, XFX 680i LT SLI board, 2 gigs XMS2 6400, Geforce 8500GT 512 vid, 160 gig Seagate Sata2. 
Will this not support Pentium x64 chips?

Well I am going to assume that the issue is that ubuntu will not support 64 bit Pentium chips with a 64 bit version of the os. So going under this assumption (unless someone corrects this) I am forced to go back to Vista.

---

### Post by bodhi.zazen on 2008-11-18
My guess is your nvidia card is not being recognized.

Two options :

First when you boot, select "Safe Graphics Mode" (Hit F4 at the boot screen).

If that fails, you will need to install from the alternate CD.

Either way, after you install you will need to install the nvidia drivers and re-boot :

```
sudo apt-get install nvidia-glx-177 nvidia-settings
```

After you reboot , configure nvidia with :

```
gksu nvidia-settings
``` or ```
sudo nvidia-xconfig
```

---

### Post by jimmy the saint on 2008-11-18
the amd64 version does support intel 64bit chips.  Does the live cd load up so you can use Ubuntu or will that not even load?

---

### Post by 83k1500 on 2008-11-18
> **jimmy the saint said:**
> the amd64 version does support intel 64bit chips.  Does the live cd load up so you can use Ubuntu or will that not even load?

It will load in my other machine old Dell Optiplex GX240.
I think the video card would not be a problem since it is a year or two old... guess not.
This other system where I want to load it has XP installed, but it has been acting up due to what I am sure is a virus but nothing will detect it or get rid of it.

And by the time anyone had even replied to this I had already gotten Vista on and running.
Sorry. I guess it still has some way to go in native hardware support.

---

### Post by bodhi.zazen on 2008-11-18
> **83k1500 said:**
> I think the video card would not be a problem since it is a year or two old... guess not.

Why would you think that ? Did you attempt the safe graphics mode ?

---

### Post by ECPCLINUX on 2008-11-18
Assuming there is nothing wrong with your burner or/and CD media Maybe you should concentrate on the motherboard's Chipset. You have the nVidia 680i LT SLI, have you tried to Google compatibility between Ubuntu x64 and 680i? I have a Pentium Core2Duo e6600 and it runs well under Ubuntu 7.10 -8.10 x64. However, the motherboard chipset is the Intel P35. My old 775 system was a D805 CPU on a nVidia nForce 4 chipset, same nVidia 8600 card I use now. No issues running on Ubuntu 7.10 x64 . I honestly don't believe there is an issue between the intel CPUs and Ubuntu x64, At least not based on my limited experience. My second system board has the nVidia 520 chipset, with the AMD x2 6000.  You could try and play with dual boot while using Visa. Hope this will give you some ideas.

---

### Post by 83k1500 on 2008-11-18
I was going to use the ubuntu machine as basically a pure ripper/encoder machine. Maybe some other light work, but primarily that.
Since Vista still has some issues with my preferred programs I was gonna give linux a shot and learn something new. But I am sorry I am just not going to go out of my way to get it to install in a machine that the majority of parts is at least 18 months old. 
I am well aware of linux's lack of support (or better stated flaky support) for brand new hardware, that is why I chose the machine and hardware that I did. 

Yes I want an OS that will install without having to go out of my way to get it installed. I want to pop in a disk and click go. I have tried linux before and will probably try it again later when it has become easier to use.

---

