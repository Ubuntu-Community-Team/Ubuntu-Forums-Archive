---
title: "graphics quality better on VESA then ATI drivers?"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by kali005 on 2008-10-04
Hi All,

i finally installed, after hours of strugelling, the most recent ATI Drivers, but it worked only trough ENVY, i spend several hours trying to install them manually, always ending up with "failed to start xserver" screen. The gfx  I've got are two Radeon HD 2600 xt in xfire.
Now the ATI drivers seem to be installed, even Catalyst is working, but the quality is much worse now then it was on the VESA drivers. You can even see it when moving a window...

Could anyone help here?:confused:

---

### Post by kali005 on 2008-10-04
Forgot to add, its Feisty.

---

### Post by markbuntu on 2008-10-04
The driver from Envy is 8.6 it does not have much xfire support. You can get the 8.9 driver from here, follow method 2:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

After you install it you can type aticonfig --help to see all the setup options, including for crossfire. it is still a little rudimentary but the ati guys are working on it and expect to have the ati linux drivers on par with the windoze drivers by about Feb2009. ATI releases new drivers for linux about every 5 weeks.

---

### Post by kali005 on 2008-10-05
Ok, thanks, i'll check it in a sec. I'm currently trying to upgrade it to Gutsy, i've read somewhere that Feisty might not be supported...

---

### Post by JohnFH on 2008-10-05
If you're upgrading, why not go directly to Hardy?  Gutsy support will end relatively soon as well, while Hardy is LTS.

As for the graphics, I learnt my lesson with ATI graphics cards the hard way and ended up getting an NVidia one.  Probably not the news you wanted to hear.

---

### Post by kali005 on 2008-10-05
So, i've upgraded to Hardy, installed the driver according to [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide), and still facing same problem - the quality and performance is worse then it was on the VESA drivers... I don't really want to switch to Nvidia, because Ubuntu is still my second OS, and the xfire is working fine on Win. 
I actually have no clue what to do now, to get it to work...

---

### Post by markbuntu on 2008-10-05
In that guide, did you use method 2?
If you upgraded from feisty, you need to remove the package:

xserver-xgl

as this will cause the ati driver to revert to mesa rendering.

---

