---
title: "Easy Gtk Tranparency (RGBA) howto for karmic and lucid"
date: 2010-02-20
forum: Outdated Tutorials &amp; Tips
---

### Post by SoftwareExplorer on 2010-02-20
I made a ppa for gtk transparency (rgba), and a how to for using it. I have tested it and it works for both Karmic and Lucid. You can also find this how to at [https://wiki.ubuntu.com/DesktopTeam/RgbaGtkWithPPA]("https://wiki.ubuntu.com/DesktopTeam/RgbaGtkWithPPA") . Enjoy!

0. It is assumed you have what ever driver for 3d and transparency installed. The ppa has been set up for both Karmic and Lucid.

1. To add the ppa's key, run

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B17A4FD

```
2. Then add the ppa by going to System -> Administration -> Software Sources, clicking on the other software tab, clicking add and putting in

```
ppa:erik-b-andersen/rgba-gtk
```

and then clicking Add Source and then close. Click Reload when prompted.

3. Go to System -> Administration -> Update Manager and install the updates, which will install the necessary packages for RGBA GTk.

4. Go to System -> Preferences -> Gnome Color Chooser. Go to the Engines tab. Check the box next to Global and choose Murrine in the drop down list next to the check box. Click Preferences. In the window that comes up find 'Configuration of Enable/Disable RGBA support', and check both boxes under that section. Click OK. Click Apply and then Close.

5. Go to System -> Preferences -> Appearance. On the theme tab click Customize... and then in the window that comes up on the Controls tab select a murrine theme. Close close and then close (again).

6. Log out and then log back in.

Optional

You may want to blur the transparency with compiz to make it easier to read text that is on a transparent area of a window. To do this,

1. Go to Applications -> Ubuntu Software Center.

2. Search for compiz and install the packages compiz-fusion-plugins-extra(you may have to install this using synaptic in karmic) and Advanced Desktop Effects Settings (ccsm).

3. Go to System -> Preferences -> Compiz Config Settings Manager.

4. Search for blur windows, and check the box next to it, and then click on it.

5. Set the Blur Filter to Gaussian and Gaussian Radius to around 4 or 5.

6. When you are satisfied with the result, just close the window.

Q & A

Q:Why doesn't Firefox, Totem, or OpenOffice run with RGBA?

A:Unfortunately, they crash if you run them with RGBA, so I disabled it for them.

Q:What does nautilus, the murrine engine, and murrine themes have to do with RGBA?

A:Nautilus is patched to not crash with RGBA and because of redraw problems, the murrine themes have a line added that enables transparency, and the murrine theme engine was recompiled to be more tranparent.

Q:Wasn't RGBA gtk going to be in Lucid by default?

A:It was, but it got postponed until Lucid+1. [See this bug comment.]("https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/491521/comments/66")

---

