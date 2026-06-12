---
title: "How to get transparent right click menu - Ubuntu 13.10"
date: 2014-01-26
forum: New to Ubuntu
---

### Post by michael100 on 2014-01-26
New to Ubuntu, but loving it so far and very impressed - completely ditched Windows 7, and I have my desktop looking very much how I want it with Unity Tweak tool to enable transparency. But there are 2 elements I want to be slightly transparent and can't seem to figure out how:

The right click menu, which I've seen others having been transparent in tutorial videos I've watched but looking for an answer online I've come across a few ways, one using CCSM, but before I try any of these I thought maybe there was an easier/preferred way of doing this since those posts are a couple years old now.

The window headers, where the close/minimize/maximize buttons reside.

Any assistance is appreciated.

---

### Post by stinkeye on 2014-01-26
You will need to install compizconfig-settings-manager compiz-plugins and dconf-editor...
In terminal....
```
sudo apt-get install compizconfig-settings-manager compiz-plugins dconf-editor
```

After install log out/in.

Run ccsm and goto **Accessibility > Opacity, Briughtness and Saturation**. Enable the plugin and  add a window specific opacity value...
```
(type=PopupMenu)
```

Run dconf-editor and drill down to **org.compiz.gwd** and set your inactive and active opacity. 
Only affects the titlebar.

---

