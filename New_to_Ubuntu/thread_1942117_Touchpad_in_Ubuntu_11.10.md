---
title: "Touchpad in Ubuntu 11.10"
date: 2012-03-16
forum: New to Ubuntu
---

### Post by RobikShrestha on 2012-03-16
In the program, "mouse and touchpad", there is no tab for "touchpad". I  want to enable vertical and horizontal scrolling. I also want two finger zooming. How do I do that?

I am using a Dell Inspiron N 5110 laptop. The OS is 64-bit Ubuntu 11.10.

The output of 

xinput list 

is:
[I]
Virtual core pointer id=2 [master pointer (3)] 
 Virtual core XTEST pointer id=4 [slave pointer (2)] 
 PS/2 Generic Mouse id=13 [slave pointer (2)] 
Virtual core keyboard id=3 [master keyboard (2)] 
Virtual core XTEST keyboard id=5 [slave keyboard (3)] 
 Power Button id=6 [slave keyboard (3)] 
Video Bus id=7 [slave keyboard (3)] 
Video Bus id=8 [slave keyboard (3)] 
Power Button id=9 [slave keyboard (3)] 
Sleep Button id=10 [slave keyboard (3)]
 Laptop_Integrated_Webcam_HD id=11 [slave keyboard (3)]
 AT Translated Set 2 keyboard id=12 [slave keyboard (3)] 
 Dell WMI hotkeys[/I]

I don't see my touchpad in this output.

---

### Post by RobikShrestha on 2012-03-17
I can use gpointing-devices for middle mouse button emulations and other stuffs but I still can't use the touchpad for scrolling and zooming.

---

### Post by Jake5 on 2012-03-17
I Have a touchpad tab, Sorry if this is not helpful, but I am not sure how to install one.

---

### Post by Jake5 on 2012-03-17
as for your mouse, it looks to me like this line:
```
*PS/2 Generic Mouse id=13 [slave pointer (2)] *
```
unless this is an actual hardwired full size mouse

---

### Post by RobikShrestha on 2012-03-17
@[Jake5]("http://ubuntuforums.org/member.php?u=1560867")

Ubuntu is not showing my touchpad.
I do not have mouse. I guess it is showing my touchpad as mouse. May be it does not have proper driver. 

What should I do?

---

### Post by peter d on 2012-03-17
I believe the laptop you have has an ALPS touchpad. I have one too and didn't have the touchpad tab in Mouse and Touchpad settings. I installed psmouse-alps-dkms which solved the problem.

You can get it here [http://people.canonical.com/~sforshe...s_0.10_all.deb](http://people.canonical.com/~sforshe...s_0.10_all.deb)

I guess this only works with ALPS Glidepoint touchpads. Hope it works.

---

### Post by RobikShrestha on 2012-03-18
I had installed it. It does not work.

---

