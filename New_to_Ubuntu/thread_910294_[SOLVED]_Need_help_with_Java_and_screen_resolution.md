---
title: "[SOLVED] Need help with Java and screen resolution pls :)"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by ruderbecca on 2008-09-04
I have just done a clean install of Hardy Heron and found I could only have 600x800 screen resolution so I enabled the restricted driver for the nvidia nforce and it made the screen res worse (640x480) lol.  I have downloaded so many packages to try and fix it to no avail.  I also play a lot of java/applet based games and even tho I have dowloaded every java package I could find through synaptic (not all at the same time) it keeps telling me java cannot be found.  Any help with either of these too problems would be much appreciated.

---

### Post by peejamm on 2008-09-04
I had the screen res problem but found the following on another thread that worked;

> **Kaploink said:**
> I had the same resolution problem with the Nvidia drivers.  I could only go to 640-480 max. I finally fixed it by running "sudo displayconfig-gtk" from a terminal and selecting the correct monitor. Apparently in my case, Ubuntu did not detect the monitor.

---

### Post by aloshbennett on 2008-09-04
If you are using ubuntu 32 bit, install sun-java6-plugin.
Else, you might have to live with icedtea-gcjwebplugin (half the stuff would work)

Try [http://www.w3.org/People/mimasa/test/object/java/clock](http://www.w3.org/People/mimasa/test/object/java/clock) to see if your applets are working.

---

### Post by ruderbecca on 2008-09-04
ty guys I have fixed the java problem and i have managed to get the screen res to 1280x1024 except for a couple of pages which still look huge.  Is there any reason this may happen?  Srry for the silly question lol
tyvm in advance :)

---

### Post by jemate18 on 2008-09-04
> **ruderbecca said:**
> ty guys I have fixed the java problem and i have managed to get the screen res to 1280x1024 except for a couple of pages which still look huge.  Is there any reason this may happen?  Srry for the silly question lol
tyvm in advance :)

SO you have managed to adjust the screen to 1280x1024... What pages look huge? I mean when you try [www.ubuntu.com](www.ubuntu.com), the display is huge?

---

### Post by freak42 on 2008-09-04
are you talking about webpages that are huge (in firefox?). try reseting the zoom lvl with ctrl-0 (zero) or view->zoom->reset

hth

---

### Post by ruderbecca on 2008-09-05
thankyou everyone I finally worked it all out :)

---

