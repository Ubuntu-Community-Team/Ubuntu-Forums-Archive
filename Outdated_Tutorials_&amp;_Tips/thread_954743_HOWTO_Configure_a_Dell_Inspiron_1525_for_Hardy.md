---
title: "HOWTO: Configure a Dell Inspiron 1525 for Hardy"
date: 2008-10-21
forum: Outdated Tutorials &amp; Tips
---

### Post by beno1990 on 2008-10-21
**NOTE:** This howto was originally written for Ubuntu Hardy Heron 8.04 but I've now installed the release candidate for Ubuntu Intrepid Ibex 8.10 and tested the following configuration, and it is the same, except for the kernel modules which need to be downloaded for the Intrepid kernel to enable webcam. WiFi should work out of the box on Intrepid, however.

This how to assumes you are using a Dell Inspiron 1525 using Ubuntu 8.04 (Hardy Heron) in the Gnome desktop, from a fresh Ubuntu install.

***WiFi and webcam***

(This section should also work for Bluetooth but it is untested since my custom build doesn't include Bluetooth)

A fresh install from the Ubuntu disk does not include the wifi and webcam drivers by default, so you have to install them manually. If you can connect to the internet by ethernet (wire) from your laptop then do so. However, some people can't connect by wire either so after so skip to the bit where I describe what to do in your case.

**If you can connect by ethernet:**

Go to System -> Administration -> Software Sources -> Updates tab.

Check the box saying "Unsupported updates (hardy-backports)" and close the window.

Open a terminal window and type

```

sudo apt-get update

```

and then

```

sudo apt-get install linux-backports-modules-hardy

```

**NOTE** Replace with the following on Intrepid Ibex:

```

sudo apt-get install linux-backports-modules-intrepid

```

This is a meta-package that will install the relevant modules for your kernel version and keep them up to date whenever you install a new kernel version. After a reboot your WiFi and/or webcam should work now, and hopefully bluetooth but I'm not sure whether these modules will enable bluetooth or not.

**If you *cannot* connect by ethernet**

Go to the following page and download the file for your processor (AMD or Intel) to a removable storage device (eg. Pen drive). The file you want to download is under the header "Download linux-backports..."

[http://packages.ubuntu.com/hardy/base/linux-backports-modules-2.6.24-16-generic]("http://packages.ubuntu.com/hardy/base/linux-backports-modules-2.6.24-16-generic")

Also note that this package will ONLY work on the kernel version that comes out of the box with Ubuntu Hardy. (ie. 2.6.24.16)

Put the pen drive into your laptop and double click to run the .deb file you downloaded from that page. Install the package (you'll need to use your sudo password).

After that, a reboot should have your wireless and webcam running (if you have a webcam). However, you should now do all of the tasks listed under "If you can connect by ethernet" **before** any new updates. This is because kernel modules are kernel version dependent, and you need the meta package to ensure your kernel module is kept up to date with any new kernel versions.

***Sound***

Sound should be working with the default Ubuntu install on an Inspiron 1525, but with some limits, namely Pulseaudio won't work with all programs installed on your computer so you might be limited to only one application being able to produce sound at a time.

For a simple solution, just open Synaptic, search for "Pulseaudio" and install all the packages it lists.

You may not need to, but it may be best to reboot after installing these pulseaudio packages, to ensure the server and your desktop environment loads all of these new packages and uses them.

***Note***

This HOWTO is written as a "Works for me" and I can't guarantee that it'll work for you too, but I hope it does. If anyone thinks something should be changed here or added or anything else, let me know in this thread.

---

### Post by madarcher on 2008-11-16
I just want to post a slight warning about this laptop and intrepid.  Wireless works out of the box on 8.10 and a dell 1525.  However the webcam does not.

Installing the linux-backports-modules-intrepid does not fix the webcam and in addition breaks the wireless.  I'm guessing there is a module conflict somewhere!

Just thought I would post in the hope that it'll stop someone else scratching their head.  I'm off to reinstall hardy!

---

### Post by robotichead on 2008-11-16
my bluetooth works out of the box with 8.04... with no problems at all... :P

---

### Post by geo909 on 2008-12-02
Ok, sorry for posting that in *ubuntu* forums but I was wondering if something similar would work for debian. Is this "linux-backports-modules" package something for ubuntu only or one can find it for other distros too?

---

