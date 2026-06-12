---
title: "[SOLVED] 8.10 - Compiz 3D Cube &amp;amp; Enabling Desktop Effects"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by sharkster2007 on 2008-11-08
**compizconfig-settings-manager**

Website:[http://packages.ubuntu.com/intrepid/x11/compizconfig-settings-manager]("http://packages.ubuntu.com/intrepid/x11/compizconfig-settings-manager")

Adds System/Preferences/CompizConfig Settings Manager (GUI to Ubuntu's Menu bar)

FILES REQUIRED BY UBUNTU 8.10:

[COLOR="SeaGreen"]compizconfig-settings-manager_0.7.8-0ubuntu3_all.deb[/COLOR]
[COLOR="SeaGreen"]python-compizconfig_0.7.8-0ubuntu1_i386.deb[/COLOR]

After installing these 2 files go to System/Preferences/CompizConfig Settings Manager and click "General Options", "Desktop Size" Tab, set Horizontal Virtual Size to 4.

If required click "back" and turn off "Cube Reflection & Deformation" under the effects menu, If you prefer the the 3D Cube effect, switch this on if you prefer the 3D Sphere effect.

**To enable 3D Cube Reflection effects** (requires Compiz Config Setings Manager Installed)

If you want 3D cube reflection Effects.

Under SYSTEM>PREFERENCES>COMPIZCONFIG SETTINGS> 

EFFECTS

Click "Cube refelection & deformation" box so tick appears, Then double click on the description part ("Cube refection and deformation" text) on the deformation tag set deformation to "none".

Your 3D cube should now have reflection effects.

**Compiz Effects Plug-in Solution** (requires Compiz Config Setings Manager Installed)

Under SYSTEM>PREFERENCES>COMPIZCONFIG SETTINGS MANAGER>EFFECTS

Make sure "Animations" & "Animations Add-on" are ticked then click PREFERENCES button on lower left side.

Click "Plugin List" Tab, Disable then Enable Check box labeled "Automatic plugin sorting" then Click back.

After selecting effects click check box next to desired effect and click the Item's text box for key activation instructions.

*NVIDIA USERS: I have a Nvidia Driver, Activation & 3D Cube set up solution for Ubuntu 8.10 here at [http://ubuntuforums.org/showthread.php?t=973038]("http://ubuntuforums.org/showthread.php?t=973038")*

---

### Post by keplerspeed on 2008-11-08
Excellent how to: also the compiz config manager is easily installed with synaptic.

---

### Post by v4nilla on 2008-11-08
For anyone that may not know how to get the Config Manager installed, just do the following:

```
sudo aptitude install compizconfig-settings-manager

```

For me 8.10 had already installed everything except this, so that is all I had to do. Hope that helps.

---

### Post by Hilko on 2009-03-02
There are very very simple instructions here.

[http://ubuntuforums.org/showthread.php?t=918936&highlight=cube](http://ubuntuforums.org/showthread.php?t=918936&highlight=cube)

Just add/remove...  Advanced Desktop Effects
And then configure it in SYSTEM>PREFERENCES>COMPIZCONFIG SETTINGS. That's all. It worked for me.

---

### Post by thesuperjman on 2009-04-17
how do i work the cube after i install it?

---

### Post by raymondh on 2009-04-17
> **thesuperjman said:**
> how do i work the cube after i install it?

ctr + alt + left or right arrow or;

ctr + alt + left mouse button (button 1) and move mouse around. That is if you are using a mouse

see this too.

[http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074](http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074)

Enjoy.

---

