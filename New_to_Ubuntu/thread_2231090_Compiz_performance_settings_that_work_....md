---
title: "Compiz performance settings that work ..."
date: 2014-06-23
forum: New to Ubuntu
---

### Post by cwmoser on 2014-06-23
After doing some testing I thought I would share some Compiz performance settings
that really improved the responsiveness with my Ubuntu 14.04 Gnome Flashback:

**_Compiz Configuration Settings Manager_**
CCSM:
General &#8594; OpenGL &#8594; Texture Filter = Fast
	Sync To Vblank = uncheck
Effects -> Animations = uncheck
Effects &#8594; Fading Windows = uncheck

**_NVIDIA X Server Settings_**
NVIDIA X Server Settings &#8594; OpenGL Settings &#8594; Image Settings = High Performance

**_Command Line:_**
$  sudo apt-get install preload 


If you have some other performance tweaks, please share.

---

