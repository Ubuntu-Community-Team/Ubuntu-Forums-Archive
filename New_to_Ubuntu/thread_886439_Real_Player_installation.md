---
title: "Real Player installation"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by audreymac on 2008-08-11
How to convert file entitled x.bin relating to Real Player and the BBC ?  This seems to be an add-on to enable me to play BBC radio stations live.
Radio Player11GOLD installed but BBC website says no Real Player installed.....

---

### Post by silkstone on 2008-08-11
The way I installed Real Player and the Firefox plugin is as follows - (taken from a tutorial)...

---------------

Installing Real Player 11 and Configuring Mozilla Plugin
--------------------------------------------------------

The following steps show how to install Real Player 11 and Mozilla Plugin for Firefox 3.0 browsers running on Hardy Heron.

Download Real Player 11 from:

  [www.real.com](www.real.com)

Open a terminal and change to the directory where the file was downloaded. Grant execute permissions and run the setup using the following commands:

  chmod 770 RealPlayer11GOLD.bin
  sudo ./RealPlayer11GOLD.bin
  

Use the following default installation directory during the installation:

  /opt/real/RealPlayer

The installer will copy the files and create menu shortcuts. Then run the following commands.

  cd /usr/lib/firefox-addons/plugins
  sudo ln -s /opt/real/RealPlayer/mozilla/nphelix.xpt nphelix.xpt
  sudo ln -s /opt/real/RealPlayer/mozilla/nphelix.so nphelix.so
  sudo mv /usr/lib/totem/gstreamer/libtotem-complex-plugin.so ~/.

Open Firefox and type about: plugins (without the space) in the address bar. Scroll down and look for the following entry.

  Helix DNA Plugin: RealPlayer G2 Plug-In Compatible
  File name: /opt/real/RealPlayer/mozilla/nphelix.so
  Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.4005 built with gcc 3.4.3 on Feb 25 2008

If found, your Real Plugin is installed properly!

------------------

Also, the BBC site no longer uses Real Player for radio streams, and you can tell it to stream video to Windows Media Player rather than Real Player - the Totem plugins should work with that.

---

### Post by audreymac on 2008-08-11
Helix DNA plugin:Real Player G2 plug in compatable:Totem.

---

### Post by philinux on 2008-08-11
+1 The helix plugin is installed by default.

---

