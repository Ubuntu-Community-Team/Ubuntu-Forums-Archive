---
title: "LXDE keyboard volume buttons stopped working"
date: 2012-03-07
forum: New to Ubuntu
---

### Post by matbluvenger on 2012-03-07
Hey all! I've started using LXDE on Ubuntu 11.10 regularly... it really is awesome.

However I have a bit of a problem. I did a fix to get my keyboard volume up/down/mute buttons to work on LXDE and it was successful for a couple days. But magically a little bit ago they stopped working.

Here's the fix I originally tried:

```
sudo pico ~/.config/openbox/lxde-rc.xml
```

And in the <keyboard> segment I inserted:

```
<keybind key="XF86AudioLowerVolume">
     <action name="Execute">
       <startupnotify>
         <enabled>true</enabled>
         <name>amixer</name>
       </startupnotify>
       <command>amixer -c 0 set Master 5- unmute</command>
     </action>
   </keybind>
   <keybind key="XF86AudioRaiseVolume">
     <action name="Execute">
       <startupnotify>
         <enabled>true</enabled>
         <name>amixer</name>
       </startupnotify>
       <command>amixer -c 0 set Master 5+ unmute</command>
     </action>
   </keybind>
```

Any help is greatly appreciated!

---

### Post by Jon Monreal on 2012-03-08
Have you checked to make sure that it's still there? Perhaps the file was overwritten.

---

### Post by matbluvenger on 2012-03-09
Yeah I definitely did. Still there. I even removed and replaced the code to no avail.

---

