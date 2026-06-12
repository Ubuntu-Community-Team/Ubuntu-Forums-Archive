---
title: "[SOLVED] Need help with building python libraries for Velleman 8055 USB interface car"
date: 2008-07-06
forum: Programming Talk
---

### Post by Slippy Lane on 2008-07-06
Hey all. First off, as this involves building a set of libraries from C source, I'm pretty sure I've got the right section to post this, but if I haven't, please forgive and point me in the direction of the appropriate place to post this question.

Recently purchased and built a Velleman 8055 USB Experiment interface board. It works fine using the supplied software under Windows, but I want to use it on my Ubuntu Gutsy box.

I haven't the first clue about building libraries from source, never having done so before, although I'm comfortable working in bash when I do know what I'm doing.

I've downloaded the libk8055 v0.3 drivers from [here]("http://sourceforge.net/project/downloading.php?groupname=libk8055&filename=libk8055.0.3.tar.gz&use_mirror=switch"), which also includes pyk8055 python libraries.

Unpacked the tarball, which gave me a src directory, in which the README file told me to go ahead and do a "make all" followed by a "make install". Here's the output from the first command:
> slippy:~/vk8055/src$ make all
gcc -O2 -DDAEMON -DVERSION='"0.3"' -Wall   -c -o main.o main.c
main.c:37:17: error: usb.h: No such file or directory
make: *** [main.o] Error 1

Obviously, it's pointless me continuing with the instructions when the first one falls down, and my knowledge doesn't extend to how I configure all the necessary paths and what have you to build this library

My system exceeds the required dependencies of libusb >= 0.1.9 and kernel >= 2.4.18

I want to be able to get on and start using python to interface to this device, but I can't do it until I can build the libraries.

Is anyone willing to lead me by the hand through the build process, or point me in the direction of a pre-compiled package, if one exists? I'd hate to think I've wasted two days of soldering time! :-)

---

### Post by WW on 2008-07-06
Install the Ubuntu package [libusb-dev](http://packages.ubuntu.com/hardy/libusb-dev) and try again.

---

### Post by Slippy Lane on 2008-07-06
Ah, thank you. I told you I knew nothing!

Note to self: duh!

Successful build and install of k8055 libraries and python libraries. Thanks for the help!

---

### Post by LinuX-M@n1@k on 2008-07-06
Mark this thread as Solved please :).

Thread Tools > Mark this thread as Solved.
(it's on the top of your first post ;))

---

### Post by stefangr1 on 2008-12-22
For (anyones) information:

If you try to change the usb device ownership as instructed on the website where you can download the drivers for the k8055, it doesn't work.

What worked for me was:

add a textfile called   50-velleman.rules  to your /etc/udev/rules.d  containing:


cut------------------------------------------------------------------------------


SUBSYSTEM !="usb_device", ACTION !="add", GOTO="velleman_rules_end"

SYSFS{idVendor} =="10cf", SYSFS{idProduct} =="5500", SYMLINK+="k8055_0"
SYSFS{idVendor} =="10cf", SYSFS{idProduct} =="5501", SYMLINK+="k8055_1"
SYSFS{idVendor} =="10cf", SYSFS{idProduct} =="5502", SYMLINK+="k8055_2"
SYSFS{idVendor} =="10cf", SYSFS{idProduct} =="5503", SYMLINK+="k8055_3"

MODE="0666", OWNER="stefan", GROUP="root"

LABEL="velleman_rules_end"


cut-----------------------------------------------------------------------------


end then execute:
chmod 4755 /usr/local/bin/k8055
chown stefan /usr/local/bin/k8055

---

