---
title: "Installation problem:Can anybody please help me"
date: 2011-09-17
forum: New to Ubuntu
---

### Post by tariq.v.s on 2011-09-17
Ubuntu Software center: During installations if i interrupt it,I am not able to install it. Unable to download, or check your internet connection....messages are coming.when I checked in the synaptic package manager non of the packages related to the installation was neither installed nor found to be broken.  Can any body please help me out with this...:D

---

### Post by anewguy on 2011-09-18
what happens if you do a sudo apt-get -purge (I think that's the correct format) and then try again?

Dave ;)

---

### Post by sikander3786 on 2011-09-18
> **tariq.v.s said:**
> Ubuntu Software center: During installations if i interrupt it,I am not able to install it. Unable to download, or check your internet connection....messages are coming.when I checked in the synaptic package manager non of the packages related to the installation was neither installed nor found to be broken.  Can any body please help me out with this...:D
Welcome to the forums :)

During installation of certain packages if Software Center is close, it might leave you with some half/non-configured packages. To configure them, go to Applications > Accessories > Terminal in Gnome Classic or search the Dash for Terminal in Unity and run:

```
sudo dpkg --configure -a
sudo apt-get install -f
```

If the packages don't still appear, you obviously need to install them again via Software Center, Synaptic or apt-get.

---

### Post by wildmanne39 on 2011-09-18
Hi, run 
```
sudo apt-get update
```
in the terminal then post the errors here all of them please by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

