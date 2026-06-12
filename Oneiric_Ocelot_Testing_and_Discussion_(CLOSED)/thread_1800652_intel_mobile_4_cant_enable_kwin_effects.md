---
title: "intel mobile 4 cant enable kwin effects"
date: 2011-07-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by buzzmandt on 2011-07-09
haven't been able to enable effects since the first xorg intel update.  let it go for a while then got a bit more desperate and grabbed the xorg-edgers ppa.  Still won't work. 

Any one have any ideas?


```
buzzmandt@buzzmandt-Compaq-Presario-CQ60-Notebook-PC:~$ kwin --replace
OpenGL vendor string:                   Tungsten Graphics, Inc
OpenGL renderer string:                 Mesa DRI Mobile IntelÂ® GM45 Express Chipset 
OpenGL version string:                  1.4 (2.1 Mesa 7.12-devel)
Driver:                                 Intel
GPU class:                              i965
OpenGL version:                         1.4
Mesa version:                           7.12
X server version:                       1.10.2
Linux kernel version:                   3.0
Direct rendering:                       no
Requires strict binding:                yes
GLSL shaders:                           no
Texture NPOT support:                   yes
kwin(3529): glCheckFramebufferStatus failed:  "GL_NO_ERROR" 
Application::crashHandler() called with signal 11; recent crashes: 1
KCrash: Application 'kwin' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
sock_file=/home/buzzmandt/.kde/socket-buzzmandt-Compaq-Presario-CQ60-Notebook-PC/kdeinit4__0
OpenGL vendor string:                   Tungsten Graphics, Inc
OpenGL renderer string:                 Mesa DRI Mobile IntelÂ® GM45 Express Chipset 
OpenGL version string:                  1.4 (2.1 Mesa 7.12-devel)
Driver:                                 Intel
GPU class:                              i965
OpenGL version:                         1.4
Mesa version:                           7.12
X server version:                       1.10.2
Linux kernel version:                   3.0
Direct rendering:                       no
Requires strict binding:                yes
GLSL shaders:                           no
Texture NPOT support:                   yes
kwin(3533): glCheckFramebufferStatus failed:  "GL_NO_ERROR" 
Application::crashHandler() called with signal 11; recent crashes: 2
KCrash: Application 'kwin' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
sock_file=/home/buzzmandt/.kde/socket-buzzmandt-Compaq-Presario-CQ60-Notebook-PC/kdeinit4__0
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/buzzmandt/.config/ibus/bus

[1]+  Stopped                 kwin --replace

```

```
lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)

```

---

### Post by buzzmandt on 2011-07-09
wow, did some more digging and it all came down to the blur effect, disable blur effect and everything else in kwin effects work.

---

