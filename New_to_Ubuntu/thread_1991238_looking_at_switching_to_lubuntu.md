---
title: "looking at switching to lubuntu"
date: 2012-05-30
forum: New to Ubuntu
---

### Post by odrin on 2012-05-30
I am looking at switching my old compaq c502 to lubuntu, but it has a broadcom wireless chipset... can I just switch builds or am I going to need to do anything special to get it to work?

---

### Post by irv on 2012-05-30
> **odrin said:**
> I am looking at switching my old compaq c502 to lubuntu, but it has a broadcom wireless chipset... can I just switch builds or am I going to need to do anything special to get it to work?
Download an iso file and burn a DVD/CD or USB and test it in a live setting. This will tell you if all your Hardware will work.

---

### Post by Paqman on 2012-05-30
What OS is it running currently? If it's already running Ubuntu you can install the desktop from Lubuntu without reinstalling. So any hardware that works now would keep working.

---

### Post by Rex Bouwense on 2012-05-30
Irv has an excellent point.  Try it.  If I remember correctly, you may have a problem getting your WIFI working with a Broadcom chip set. So you should connect with an ethernet cable and you will be able to download the driver.
I'm not sure that you get Lubuntu if you simply download the LXDE desktop on top of a Ubuntu install as Paqman suggests.

---

### Post by Paqman on 2012-05-30
> **Rex Bouwense said:**
> 
I'm not sure that you get Lubuntu if you simply download the LXDE desktop on top of a Ubuntu install as Paqman suggests.

Not if you install the vanilla LXDE packages, but if you install [lubuntu-desktop]("apt:lubuntu-desktop") you will. Obviously to get a system identical to the one on the Lubuntu disk you'd then need to uninstall all the Gnome packages. Aysiu has the correct list of packages to do that on his site Psychocats:

[Install Lubuntu, remove Gnome]("http://www.psychocats.net/ubuntu/purelubuntu")

---

### Post by Lyfang on 2012-05-31
Try to create a bootable Live USB flash drive with UNetbootin using lubuntu-12.04-desktop ([http://cdimages.ubuntu.com/lubuntu/releases/precise/release/](http://cdimages.ubuntu.com/lubuntu/releases/precise/release/)).

See also: [http://askubuntu.com/questions/97937/lubuntu-hardware-manager](http://askubuntu.com/questions/97937/lubuntu-hardware-manager)

---

### Post by verymadpip on 2012-05-31
Sorry to interject here, but are there not some "under the bonnet (hood)" differences between Ubuntu & Lubuntu apart from default applications, DE etc?

Am I just not understanding something?

---

### Post by TBABill on 2012-05-31
It's completely possible to enable a Broadcom device using either b43 or STA, depending on your device, from a LiveDVD. I do it for my BCM4312 to test Ubuntu and it does not require connecting via ethernet first. 
 
Load up the live session, go to additional drivers, enable the correct driver for your device and when it says you need to restart, do NOT restart. Simply modprobe the driver instead by ```
sudo modprobe wl
``` Substitute b43 for wl if you install the b43 driver. Wl is for the STA driver.
 
If your wireless already works on Ubuntu, adding lubuntu-desktop will keep it working when you boot into LXDE (Lubuntu).

---

### Post by irv on 2012-05-31
There are 7 Desktop Environments that come with Ubutntu.
1. KDE
2. Xfce
3. LXDE
4. Fluxbox
5. Enlightenment
6. Unity
7. Gnome

If you want to read about each one goto: [http://www.pcworld.com/businesscenter/article/214930/6_alternative_ubuntu_desktops_worth_trying.html]("http://www.pcworld.com/businesscenter/article/214930/6_alternative_ubuntu_desktops_worth_trying.html") For some reason they left out Gnome on this page. They only listed the first 6.

There are different things that each one load, like file managers, windows manager etc. One can install any of them from the package manager and switch between them at boot up. This really give one a large selection to choose from. I have tried them all, and I now stick with one, “Unity”. This is my choice, but I always say, “different strokes for different folks.”

---

