---
title: "Accessing wireless-device as non-root"
date: 2009-12-16
forum: Programming Talk
---

### Post by JayD239 on 2009-12-16
Hello, 

I am currently working on a project that will make use of some hardware. I have never programmed for specific hardware and i'm not sure how to do this. Could anyone give me some pointers?

My situation: 
I'm developing an application (Java and C, this part will be C I think) that will make use of the wireless networks in the surrounding. I need to have information of the strength of the nearby networks (quality, bitrate, frequency). 
Using [FONT="Courier New"]iwlist wlan0 scan[/FONT] appears not be an option because it requires root privilege, and I rather not want to prompt the user for a password (and I'm can't have them start it as root).

---

### Post by dwhitney67 on 2009-12-16
> **JayD239 said:**
> ...
Using [FONT="Courier New"]iwlist wlan0 scan[/FONT] appears not be an option because it requires root privilege
No it doesn't.  A regular user can run iwlist.

---

### Post by JayD239 on 2009-12-16
Yes, but it will only give you the cached details of the network you are currently connected to.

Try running it twice as root and twice as normal user and see the differences.

---

### Post by dwhitney67 on 2009-12-16
You're right; I stand corrected.

---

### Post by Zugzwang on 2009-12-16
Isn't there the possibility to have your application "owned" by the root and use the sticky bit? This way the application will always have root rights, no matter which rights the user has. 

Warning: In this case, you have to write your application very carefully as it might introduce security holes.

---

