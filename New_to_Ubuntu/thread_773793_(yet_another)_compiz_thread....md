---
title: "(yet another) compiz thread..."
date: 2008-04-29
forum: New to Ubuntu
---

### Post by adza on 2008-04-29
Okay, i've installed the restricted drivers, they are in use and enabled in the hardware devices screen, i've installed ccsm and have ticked the desktop cube and rotate cube effects in the settings manager, all should be good right? unfortunately, i still can't get compiz to bring on the eye candy - even wobbly windows won't work! help! i get the gears when typing glxgears into the terminal, however it doesn't appear to have Xgl support, when i try compiz --replace, the following appears 
> XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 39 requests (37 known processed) with 0 events remaining.
adza@adza-pc:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0391 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Starting gtk-window-decorator
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered


this is really, really wierd... i know it's something simple... can someone please help?

---

### Post by Vermind on 2008-04-29
Hello,
You seem to have nvidia, no Xgl is required. Compiz seems to start normally but complain about Your old configuration. Have You started compiz like this, and then tried changing settings with ccsm?

---

### Post by alienexplorers on 2008-04-29
What video card are you using and what driver are you using?  You need to have GLX running in order to run compiz.  If you are using a nvidia board then use Envy to setup your driver.  When you enter Envy tell it to unload your current driver.  Next let Envy set up the correct driver based on your graphics card.  After you have the correct driver installed then try to enable compiz and see if it works.

---

### Post by Michael.Godawski on 2008-04-29
Try to install this package:

```
sudo apt-get install xserver-xgl
```
and then log off and login changing the session to xclient.

---

### Post by adza on 2008-04-29
firstly, thanks for all your replies ppl :) let's try these one at a time however, @vermind, i can change the settings when compiz is 'running' (started like above), the cube works! so, here's what i did to fix my problem... firstly, installed emerald and started both emerald and compiz... very sweet... installed all emerald packages out of the repos (using synaptic - there were 3). The, opened the System -> Preferences --> Sessions and added both 'compiz' and 'emerald' into the startup... sweet... all is working now...

---

