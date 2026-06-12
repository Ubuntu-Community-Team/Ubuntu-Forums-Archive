---
title: "Force Compiz Effects to work"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by northtownheatre on 2008-06-03
I have been trying to get the compiz effects enabled on a computer that is showing "Desktop Effects could not be enabled" with no success.  I would like to know if there is a way to force compiz to work or to fool ubuntu into accepting it.

I am running a HP Pavioion tx2000 tablet PC which has:
4GB ram
AMD Turion 64-bit X2 TL-64
NVIDIA GeForce Go 6150 integrated graphics card

:confused:  Thanks!  :confused:

---

### Post by starcannon on 2008-06-03
post the output of
```
glxinfo | grep render
```

You should be able to get compiz working with that card.

---

### Post by iaculallad on 2008-06-03
Type "compiz" in the terminal and post the output.

---

### Post by typofreak183 on 2010-02-20
I have the same problem. I don't care whether or not Ubuntu likes my graphics card, I just want Compiz to WORK. Results:
```
direct rendering: Yes
OpenGL renderer string: Software Rasterizer
```
```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 
```

I am using a Dell Dimension 4600i. Don't know anything about the graphics card. I have already tried to use the "SKIP_CHECKS" or whatever thing in the terminal. When I do, the screen goes all white except for the cursor. I can't see anything else, and the only option left is to blindly guess where the logout button is. **Help!**

EDIT: I know that Compiz works, as I had it working at one point a year or so ago. When I try to enable, I just get "Desktop Effects could not be enabled". I have tried using the System > Administration > Hardware Drivers, but there appear to be none.

---

