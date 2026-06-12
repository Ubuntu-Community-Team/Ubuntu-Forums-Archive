---
title: "xslideshow has missing fonts?"
date: 2014-05-07
forum: New to Ubuntu
---

### Post by paul1945 on 2014-05-07
When xscreensaver comes up (I have set it to go through a series of JPGs) it comes up in the top left cornet of the screen with:
```
gls slideshow unable to load font -*-helvetica-medium-r-normal-*-180-*, using fixed
```
It appears to me that there are some fonts missing in my recent Ubuntu 14.04 install.
Can anyone help me as regards the command line syntax to download and install these?
Thanks, Paul.

---

### Post by paul1945 on 2014-05-16
Found a post that showed showed a workaround on how to disable this message.
```
Open your file manager. Navigate to your home directory and turn on the option to view hidden files. 
Edit the hidden file, .xscreensaver, (~/.xscreensaver) as root. If the file does not exist, you may create it. 
You must edit the file as root in order to modify the file.
Change the option:
"captureStderr: True" to "captureStderr: False"
and
"overlayStderr: True" to "overlayStderr: False"
```
This worked fine for me.

---

