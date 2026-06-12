---
title: "[SOLVED] Selecting which packages to install during installation?"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by drazgo on 2008-10-13
hi everybody, 

title says pretty much all. I'm wondering if there's a way to select which packages to install during the installation (graphical or text-based doesn't matter) of ubuntu? For example, i don't really need the openoffice.org package on my system. Can i exclude it during the installation or am i forced to remove it after installation?

thanks in advance!!
Drazgo

---

### Post by namegame on 2008-10-13
I'm not sure if you can as openoffice is a part of the ubuntu-desktop meta package. I've had errors trying to remove it post-installation as well. 

You could do a command line install from an alternate CD and install only the applications you want.

---

### Post by snowpine on 2008-10-13
You can use the Mini.iso or the Alternate CD to install a CLI (command line only) minimal install, then add only the packages you need.

(edit) There is also Xubuntu, which uses Abiword + Gnumeric instead of Openoffice, I believe.

---

### Post by drazgo on 2008-10-13
the problem is that when i install starting from CLI, some functions don't work, like i can't seem to get compositing working. I am running such a system at this very moment.

---

### Post by snowpine on 2008-10-13
I understand your frustration, but what I hear you saying is: 1) You don't want to start with a full install then remove what you don't want; 2) You are not comfortable starting with a minimum install then adding what you do want. You see the problem. ;)

---

### Post by bodhi.zazen on 2008-10-13
It is far far easier to start with a minimal installation and add only what you need then perform a "full installation" and subtract.

IMO it is unfortunate that Ubuntu does not allow better control of package selection at installation like some distros do (Fedora, OpenSUSE, and Slackware come to mind).

This thread may help : [http://ubuntuforums.org/showthread.php?t=298835](http://ubuntuforums.org/showthread.php?t=298835)

---

### Post by drazgo on 2008-10-13
> **bodhi.zazen said:**
> It is far far easier to start with a minimal installation and add only what you need then perform a "full installation" and subtract.

IMO it is unfortunate that Ubuntu does not allow better control of package selection at installation like some distros do (Fedora, OpenSUSE, and Slackware come to mind).

This thread may help : [http://ubuntuforums.org/showthread.php?t=298835](http://ubuntuforums.org/showthread.php?t=298835)

i used that thread to install my lightweight gnome, but i just can't seem to get compiz working :? And as for removing after installation: If you remove some package, you also remove their depencies, which could be essential for other packages and so install other packages which you still need...

---

### Post by Nxion on 2008-10-13
Here is a another way to go as well. I used this way, I found that it help a lot.

[https://help.ubuntu.com/community/Diet%20Ubuntu](https://help.ubuntu.com/community/Diet%20Ubuntu)

Hope this helps,
Nxion

---

### Post by adaptr on 2008-10-13
I have read and understand all the reasons behind the "turn-key" installation procedure for Ubuntu, and I agree with it.
But I don't see why an "Advanced" installation path (reachable from a simple button that first-time users are unlikely to experiment with) cannot be offered to users who know what they want.

---

### Post by drazgo on 2008-10-13
> **Nxion said:**
> Here is a another way to go as well. I used this way, I found that it help a lot.

[https://help.ubuntu.com/community/Diet%20Ubuntu](https://help.ubuntu.com/community/Diet%20Ubuntu)

Hope this helps,
Nxion

hmm, this may do the trick, thank you very much!! :)

---

### Post by drazgo on 2008-10-13
> **adaptr said:**
> I have read and understand all the reasons behind the "turn-key" installation procedure for Ubuntu, and I agree with it.
But I don't see why an "Advanced" installation path (reachable from a simple button that first-time users are unlikely to experiment with) cannot be offered to users who know what they want.

totally agree, they really should consider including such a button in their installation!

---

### Post by bodhi.zazen on 2008-10-13
> **adaptr said:**
> I have read and understand all the reasons behind the "turn-key" installation procedure for Ubuntu, and I agree with it.
But I don't see why an "Advanced" installation path (reachable from a simple button that first-time users are unlikely to experiment with) cannot be offered to users who know what they want.

> **drazgo said:**
> totally agree, they really should consider including such a button in their installation!

+1 . I have made similar suggestions, I suggest you either file a "bug report"  on launchpad or start a thread in testing 

[http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

---

