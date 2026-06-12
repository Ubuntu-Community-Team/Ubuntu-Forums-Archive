---
title: "Desktop Background"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by subaruwrc01 on 2008-10-07
I am currently using Ubuntu 8.04 on my laptop.  I have a giant panoramic picture I want to use as my desktop background.  Is there any way I can spread the picture over my two workspaces?

---

### Post by shifty_powers on 2008-10-07
chop the picture in two and use

[http://anuragbansal.wordpress.com/2008/05/10/how-to-get-different-wallpapers-on-each-workspace-in-ubuntu/](http://anuragbansal.wordpress.com/2008/05/10/how-to-get-different-wallpapers-on-each-workspace-in-ubuntu/)

---

### Post by bodhi.zazen on 2008-10-07
yep, load 'er up ;)

---

### Post by subaruwrc01 on 2008-10-07
Thanks for the help.  I managed to install everything fine and rebooted, but I'm kinda stuck now.  The image shows up when I log in, but then the desktop turns white.  I'm wondering if I missed something.

---

### Post by y@w on 2008-10-07
Is this what you are seeing?: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/197221](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/197221)

---

### Post by subaruwrc01 on 2008-10-07
Yes.

---

### Post by y@w on 2008-10-07
Looks like it's a bug in Compiz :(

---

### Post by subaruwrc01 on 2008-10-07
Here is what I get in the terminal when trying to run compiz:

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2a02 (rev 0c) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
```

I can't find the path that is mentions.

---

