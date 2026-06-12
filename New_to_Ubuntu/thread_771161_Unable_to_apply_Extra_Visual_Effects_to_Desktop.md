---
title: "Unable to apply Extra Visual Effects to Desktop"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by jctalluri on 2008-04-27
Hi,

I am new to Linux world. I have recently installed Ubuntu 8.04 on my Thinkpad T23. It uses S3 graphics hardware. I have tried to apply Extra Visual Effects to the Desktop. Error message says 'Desktop Effects could not be enabled'. Searched in some threads and tried to use command 'Compiz' in terminal. The output reads as below. Can someone help me resolve this?

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

Thanks,
JC

---

### Post by vbman11 on 2008-04-27
Try going to "add/remove applications" in the Applications menu, search for "advanced desktop effects settings" and install it.:)

---

### Post by jctalluri on 2008-04-27
I have tried that. Still I get the same error message

---

### Post by vbman11 on 2008-04-27
you might need different video card drivers then, what is your video card?

---

### Post by jctalluri on 2008-04-27
It is S3 SuperSavage/IXC

---

### Post by vbman11 on 2008-04-27
I'm sorry, but I don't know how to configure that. Try searching for "S3 SuperSavage/IXC Ubuntu" on google.:(

---

### Post by daberger on 2008-04-27
ur guna want to run

SKIP_CHECKS=yes compiz


that shud be a tempory solution. i had same problem and it resolved it
my thread for this problem here [http://ubuntuforums.org/showthread.php?t=738321](http://ubuntuforums.org/showthread.php?t=738321)

---

### Post by jctalluri on 2008-04-27
Tried that option too. Got the below output... :(

Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: Not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

---

### Post by daberger on 2008-04-28
and did your screen flicker?

---

