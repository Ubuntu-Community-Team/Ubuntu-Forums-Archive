---
title: "Low graphics mode"
date: 2012-02-02
forum: New to Ubuntu
---

### Post by d4m1r on 2012-02-02
This is very strange and I don't understand how it's connected but today I upgraded my iPhone to iOS 5 and wanted to reinstall 2 libimobile2 packages I had installed under my Ubuntu partition through the software centre. Anyway, I:

1)uninstalled the first package with no issues
2)during the uninstall process of the 2nd package (which had a bunch of dependencies), my entire Ubuntu crashed (black screen, mount/unmount [OK], etc)
3)it did mention something about something in /etc/ not being found
4)restarted my PC and got a message "Ubuntu is running in low graphics mode" but it don't actually ever even go to the desktop
5)recovery mode, fix broken packages, it installed something like "python-gtk"
6)restarted again, still won't boot to the desktop

I can get to the console, but not to my desktop...It won't let me reconfigure my graphics options and the only other thing I can do is view xorg/xserver errors (stuff in there about no layout selection, no screen section available, etc). Does anyone have any ideas WTF is going on? :confused:

---

### Post by d4m1r on 2012-02-02
Weird...Now I can get to my desktop, kinda. My login screen looks normal, but when I login, there is no sound and my desktop doesn't actually load. I can launch programs via terminal but I have no unity bar, top bar, etc. I try uninstalling libimobiledevice2 again from the terminal this time and it says [SIZE=3]gdm[/SIZE] is a dependency?! :shock:

How I got to the login screen:

```
sudo apt-get update

sudo apt-get -d install --reinstall gdm

sudo apt-get remove --purge gdm

sudo apt-get install gdm

sudo apt-get remove --purge xserver-xgl compiz compiz-plugins compiz-core compiz-manager csm cgwd cgwd-themes

sudo apt-get install --reinstall compiz compiz-core  compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome  compiz-plugins libcompizconfig0

sudo dpkg-reconfigure -phigh xserver-xorg

sudo reboot
```

^Can anyone shed some light on what is happening, why, or how I can get my desktop back? ](*,)

---

### Post by d4m1r on 2012-02-03
Solved! What a waste to a night I thought I had for gaming though...

For some STUPID reason, gdm (gnome) is set as a dependency for libimobiledevice2 which is a library for communicating with iDevices. I thought I installed this manually after on 11.04 but when I tried to uninstall it yesterday, it uninstalled gnome, ubuntu-desktop, and other key packages that should NEVER be uninstalled ](*,)

After installing them all back via the console, things still didn't look right so I took a leap of faith and upgraded to 11.10....Spent the rest of the configuring it to how I had my 11.04 setup and now it's OK.

Why Ubuntu even allows those key system packages to be uninstalled is beyond me...it should be restricted....

---

### Post by mörgæs on 2012-02-03
If this solves your problem, please mark the thread so using 'thread tools'.

---

