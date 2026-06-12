---
title: "Title Bar Buttons and Compiz Problems"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by Fatal Equinox on 2008-05-02
> **GavinZac said:**
> open a terminal and type "metacity --replace"

Does this bring them back?

That worked for me, good to have the title bar back :lolflag: ... Why does that happen?

And how can i fix it so that i get my effects(compiz) back with title bar?

Mod's Note:  This thread was moved.  This is [the thread]("http://ubuntuforums.org/showthread.php?t=779035") mentioned in the quote.

---

### Post by GavinZac on 2008-05-02
> **Fatal Equinox said:**
> That worked for me, good to have the title bar back :lolflag: ... Why does that happen?

And how can i fix it so that i get my effects(compiz) back with title bar?

It happens when Compiz's window manager fails, either because of a bug in it, or when your hardware graphics card is not configured properly.

You can probably get more information about why it is failing by switching back from metacity to compiz by typing the command:
sudo compiz --replace

or

sudo emerald --replace

(im not sure which one will work in hardy :lolflag:)

---

### Post by Fatal Equinox on 2008-05-02
southstarr@southstarr-laptop:~$ compiz --replace
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered


So i need to find my nvidia drivers?   or would re-installing compiz work... because it all worked pretty well untill i was messing with the session manager. >_<

---

### Post by Bakon Jarser on 2008-05-02
I've had this problem before too.  If you have an Nvidia card this seems to fix it.

sudo nvidia-xconfig --add-argb-glx-visuals -d 24

---

### Post by Fatal Equinox on 2008-05-02
> **Bakon Jarser said:**
> I've had this problem before too.  If you have an Nvidia card this seems to fix it.

sudo nvidia-xconfig --add-argb-glx-visuals -d 24


I got this as result 

```
Using X configuration file: "/etc/X11/xorg.conf".

WARNING: Unable to find CorePointer in X configuration; attempting to add new
         CorePointer section.


WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.

Option "AddARGBGLXVisuals" "True" added to Screen "Default Screen".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

I am assuming it didn't work as in it switched it to metacity and when i switch back it still lacks a title bar. 

Is this a driver issue or a compiz issue?

---

### Post by GavinZac on 2008-05-03
> **Fatal Equinox said:**
> I got this as result
I am assuming it didn't work as in it switched it to metacity and when i switch back it still lacks a title bar. 

Is this a driver issue or a compiz issue?
it seems like an nvidia problem. Could you attach your xorg.conf file?

---

