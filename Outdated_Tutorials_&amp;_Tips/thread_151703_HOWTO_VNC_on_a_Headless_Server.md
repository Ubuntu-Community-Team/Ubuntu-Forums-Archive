---
title: "HOWTO: VNC on a Headless Server"
date: 2006-03-28
forum: Outdated Tutorials &amp; Tips
---

### Post by hagen00 on 2006-03-28
Hi guys

If you have a basic server with no X installed, this is how you get a VNC server up and running. 

1. Get the vnc server. I chose tightvncserver
```
apt-get install tightvncserver
```

2. Get the fonts needed to run X
```
apt-get install xfonts-base xfonts-75dpi 
```
Note: You might want to get some more, just apt-cache search xfonts

3. Change the vnc config file
vi /etc/vnc.conf and change line to:
$fontPath = “/usr/lib/X11/fonts/75dpi/,/usr/lib/X11/fonts/misc/”
Note: This was on my system. Make sure you put in the correct font paths.

4. Get a windows manager and xterm
```
apt-get install twm xterm
```

5. Start the vncserver by typing
```
vncserver
```

All the important files are found in ~/.vnc/
such as logs and the startup script, where you specify what applications to launch with VNC such as xterm.

Hope that helps

H

---

### Post by kmi on 2006-03-30
Hello hagen00,
Thanks for reporting your problems/success with tightvncserver in previous posts and for this how-to.
Could you also please post the main config files associated with this how-to (vnc.conf especially) ?
My way of following your method did not give the expected results and all seems so easy for you that I suddenly feel too lazy to search... :mrgreen: 
:)

---

