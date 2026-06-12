---
title: "Possible to install Xubuntu-Desktop or XFCE over Lubuntu?"
date: 2013-10-27
forum: New to Ubuntu
---

### Post by Remten on 2013-10-27
I need an alternative install option and I would like to end up with a distro similar to Xubuntu. However, Xubuntu 13.10 does not include an alternative install. It seems that the only *buntu 13.10 that offers an alternative install option is Lubuntu.

So would a reasonable work around be to simply install Lubuntu 13.10 using the alternative install, and then to install the Xubuntu-desktop package or the XFCE4 manager?
(I'm not 100% sure what that means, although I gather that the Xubuntu-dekstop package would include a version of xfce as a desktop manager along with various Xubuntu-preferred applications, while XFCE4 would just be a desktop manager stuck on top of whatever applications had come with the original Lubuntu install. Is this correct?)

---

### Post by ajgreeny on 2013-10-27
You are right. xfce4 will add just the desktop environment but xubuntu-desktop will add that plus all the apps that come with xubuntu,  some of which you might not want or .Try xfce first and you can then add anything else you find you want later.

---

### Post by vasa1 on 2013-10-27
You can compare the outputs of
apt-get install -s xubuntu-desktop
apt-get install -s xfdesktop4 (which is what I use along with Thunar instead of PCManFM)
apt-get install -s xfce4

---

### Post by verymadpip on 2013-10-27
Hi there.
Mini-iso + Xubuntu desktop?

---

### Post by Remten on 2013-10-30
> **verymadpip said:**
> Hi there.
Mini-iso + Xubuntu desktop?

I didn't try this because I did not know whether the mini-iso includes an easy way to setup logical volumes and encryption for root/swap/home at the time of the system install.

I ended up using the lubuntu alternate installer and then installing xfce4 and xfce4-goodies.
That seems to have worked so far overall, although I initially had some problems with error messages appearing each time I would log into the xfce sessions that did not appear when I would log into the plain lubuntu sessions.
I am still trying to sort out some other issues, such as getting Synaptic Package Manager to function normally (that is, the same as in lubuntu sessions) in xfce sessions and getting laptop function keys working properly, but not sure yet whether those are directly related.

---

