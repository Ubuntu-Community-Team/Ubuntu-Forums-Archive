---
title: "Envy and Nvidia 7800"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by pcostanza on 2008-04-26
I just upgraded to 8.04 and in Gutsy, Compiz worked fine with Nvidia 7800 card.  Now, I can't enable the desktop. I've tried Envy and see no difference and also tried the restricted drivers with no luck.  Is there a problem with Hardy?
I've read much about Nvidia cards and tried some of what's posted with no luck but things were easy in Gutsy.  What's the secret?

TIA

---

### Post by pcostanza on 2008-04-26
Well, I uninstalled the nvidia drivers in Envy, rebooted and turned off restricted drivers and it seems to have worked.  Then it said I needed to reboot and I did and I'm back to where I was.
So, I went into hardware drivers and turned off, rebooted and the res came back but in order to enable desktop effects, I have to allow restricted drivers which seems to stop me from using compiz. It's a loop.

---

### Post by Dr.Gringo on 2008-04-26
Make sure the restricted drivers are not in use and then download and install EnvyNG that should automatically take care of your display problems.

---

### Post by nicedude on 2008-04-26
I use compizconfig-settings-manager to config mine. Also try right click on desktop and select "change desktop background" then once that opens select the tab visual effects and see if its set to extra or custom if not chose extra and see what it says when you apply. If it says not supported than you have something missing or not configured correctly.

---

### Post by gerben1 on 2008-04-26
Well, I have been trying EnvyNG and also tried the manual installation (as explained here: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)), but it wont work. For me it also used to work fine in Gutsy (using envy to install).

Whatever I do I keep getting this:

gerben@CC1184274-A:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

---

### Post by pcostanza on 2008-04-26
> **nicedude said:**
> I use compizconfig-settings-manager to config mine. Also try right click on desktop and select "change desktop background" then once that opens select the tab visual effects and see if its set to extra or custom if not chose extra and see what it says when you apply. If it says not supported than you have something missing or not configured correctly.

I've tried this a number of times and I usually get the 'Enable driver' message which I enable. It tells me to run Appearnace/Desktop after a reboot but when I do this, upon reboot, I get a message to configure my card saying my card could not be detected. SO I again go thru the configuration and choose my Nvidia series 7 card, it continues booting but when I go back to the Appearance tab and try to check the effects box, I'm told it could not be enabled. 
This really shouldn't be this hard.  I know I'm a newb at this but I'm glad I have a dual boot system to get me by.

---

