---
title: "Selecting GDM/lightDM after 11.10 bate install"
date: 2011-08-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Andre-D on 2011-08-30
I forgot to switch to LightDM during installation of 11.10 beta.
So i tried to fix it by selecting LightDM with:
sudo dpkg-reconfigure gdm

everything was a mess, a loginscreen I've never seen before (not LightDM) - no menu and so on..  switched back to gdm.

Does anyone know what's missing ?

---

### Post by dino99 on 2011-08-30
lightdm works fine now on i386

sudo apt-get install lightdm lightdm-gtk-greeter
sudo service gdm stop

sudo dpkg-reconfigure lightdm
(select lightdm)

---

### Post by jbicha on 2011-08-30
Use unity-greeter instead of lightdm-gtk-greeter.

---

### Post by Andre-D on 2011-08-31
dino99: Thanks - it seems stopping gdm service was important - now it seems to work as expected.

jbicha: I did not install lightdm-gtk-greeter - I skipped some steps as I knew the necessary software were installed - because I've seen it running before.  however, I would not know how to switch from one "greeter" to another :)

Thanks to both of you

---

### Post by SilverWave on 2011-08-31
Thanks guys - just installing now and chose GDM in place of lightDM to configure.

so same advice for 64bit?

Upgrading from Natty.

---

### Post by alexvy13 on 2011-08-31
> **Andre-D said:**
> I forgot to switch to LightDM during installation of 11.10 beta.
So i tried to fix it by selecting LightDM with:
sudo dpkg-reconfigure gdm

everything was a mess, a loginscreen I've never seen before (not LightDM) - no menu and so on..  switched back to gdm.

Does anyone know what's missing ?

where'd you get the beta? i didnt know it was out yet..

---

### Post by cariboo on 2011-08-31
There are places on the internet that have a daily image that they claim is the beta, but until it is officially released on Sept. 1, anything claiming to be the beta release, is just a daily image.

---

### Post by SilverWave on 2011-09-01
> **cariboo907 said:**
> There are places on the internet that have a daily image that they claim is the beta, but until it is officially released on Sept. 1, anything claiming to be the beta release, is just a daily image.

Well I upgraded last night and have just checked Update manager and no more files needed updating.

....so it cant be far off lets say ;-)

Oh and of course that&#8217;s from their main server.

Alt+F2 key combination and typed in:

update-manager -d

---

### Post by barrmulio on 2011-09-01
the beta is finally up
[http://cdimage.ubuntu.com/releases/oneiric/beta-1/](http://cdimage.ubuntu.com/releases/oneiric/beta-1/)

---

### Post by cariboo on 2011-09-01
> **barrmulio said:**
> the beta is finally up
[http://cdimage.ubuntu.com/releases/oneiric/beta-1/](http://cdimage.ubuntu.com/releases/oneiric/beta-1/)

There aren't any i386 images yet, so it hasn't officially been released.

---

### Post by lucazade on 2011-09-01
> **cariboo907 said:**
> There aren't any i386 images yet, so it hasn't officially been released.

[http://releases.ubuntu.com/oneiric/](http://releases.ubuntu.com/oneiric/)

---

### Post by ScislaC on 2011-09-01
Does lightdm have issues on 64bit? I try to get it going after every update, but am still forced to use gdm. The greeter comes up with lightdm, but when I log into Unity it just stops at a black screen with the X cursor in the middle. At least gdm still works for now.

---

### Post by ventrical on 2011-09-01
Thanks for that clarification.

Alpha 3  works like a stable version as it is :)

---

### Post by cariboo on 2011-09-01
> **ScislaC said:**
> Does lightdm have issues on 64bit? I try to get it going after every update, but am still forced to use gdm. The greeter comes up with lightdm, but when I log into Unity it just stops at a black screen with the X cursor in the middle. At least gdm still works for now.

I'm got 3 64-bit installs, lightdm works without a problem on all of them.

---

### Post by ScislaC on 2011-09-01
> **cariboo907 said:**
> I'm got 3 64-bit installs, lightdm works without a problem on all of them.

Are you running the proprietary nvidia driver on any of them? (just trying to narrow it down)

---

### Post by cariboo on 2011-09-01
> **ScislaC said:**
> Are you running the proprietary nvidia driver on any of them? (just trying to narrow it down)

All three systems use the closed source nvidia driver.

---

### Post by jcrow on 2011-09-02
I have the same problem. GDM works fine. I am using the closed source driver.

---

### Post by cariboo on 2011-09-02
Check to make sure unity-greeter is installed.

---

### Post by SilverWave on 2011-09-03
> **dino99 said:**
> lightdm works fine now on i386

sudo apt-get install lightdm lightdm-gtk-greeter
sudo service gdm stop

sudo dpkg-reconfigure lightdm
(select lightdm)


Cheers that worked for me on 64 bit.
NVIDIA proprietary driver - current (Post release update).
The NVIDIA driver even allows TwinView Whoot!

---

