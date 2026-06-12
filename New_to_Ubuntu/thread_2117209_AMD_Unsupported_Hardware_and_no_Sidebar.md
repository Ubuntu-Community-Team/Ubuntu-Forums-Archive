---
title: "AMD Unsupported Hardware and no Sidebar"
date: 2013-02-17
forum: New to Ubuntu
---

### Post by TheXtreme1 on 2013-02-17
I am brand new to Ubuntu and have no idea how to fix this.

I tried to use the plugin/app to install drivers yesterday which seemed to cause this. The sidebar is gone, the system settings in the top right is there only on login and there is a AMD Unsupported Hardware watermark.

I have an AMD Radeon 7970m.

I can't really browse files or run programs due to me not having anything to click on besides the desktop however the terminal does still work.

---

### Post by DuckHook on 2013-02-17
You have a bleeding-edge, ultra-high-end video chip that is not yet supported by the drivers in the repositories. Therefore, Ubuntu does not know how to write info to it because the driver doesn't know how to translate. The driver is the SW component throwing up the watermark. You will have to build the latest driver for it from the AMD site as I had to for my 7950. This is a very complex procedure for new users, but manageable if you have some build-experience. Only you can determine if the increased performance is worth the effort. Otherwise, the solution is to go back to the default open-source driver that originally worked. Since you installed from the repositories, do the following:

Reboot but do not login. Instead at the login screen <Ctrl>+<Alt>+<F1> to get to an alternate TTY session. Login on this command line interface session and do:

```
sudo apt-get remove --purge xorg-driver-fglrx fglrx*
sudo apt-get remove --purge fglrx*
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0 dh-modaliases
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo dpkg-reconfigure xserver-xorg
sudo shutdown -r now
```This will have the added benefit of preinstalling the build components that you need should you decide to build the latest driver from AMD's site. We will leave that as a separate exercise should you decide to go there.

---

