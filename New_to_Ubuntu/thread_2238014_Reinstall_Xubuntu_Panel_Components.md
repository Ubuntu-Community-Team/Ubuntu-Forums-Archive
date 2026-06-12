---
title: "Reinstall Xubuntu Panel Components"
date: 2014-08-05
forum: New to Ubuntu
---

### Post by Curtis_Bryant on 2014-08-05
I just installed Xubuntu 14.04 on my laptop and managed to uninstall the battery and WiFi monitors from the panel. I wanted them to hide them and should have stopped when the warning said the component would be permanently removed. I deserve a dunce cap for that. 

But how do I get them back? The battery plugin seems to be xfce4-battery-plugin-1.0.5. The page [http://goodies.xfce.org/projects/panel-plugins/xfce4-battery-plugin](http://goodies.xfce.org/projects/panel-plugins/xfce4-battery-plugin) says to get it through the package manager or by downloading and compiling the source code. I couldn't find it in the package manager, so I have downloaded the source code.

After running ./configure, it said to install libintl. That was available through the package manager. Now it says it can't find the required package gtk+-2.0. It says it needs at least version 2.20.0. 

I figure I probably do have GTK because Xubuntu came with The GIMP, which uses GTK as I recall. It says another option is to "adjust the PKG_CONFIG_PATH environment variable. 

So my questions are:
[LIST]
[*]How would I find out if I have GTK installed, where it is, and update PKG_CONFIG_PATH? 
[*]Do you know an easier way to reinstall the battery monitor and WiFi monitor XFCE panel plugins? 
[/LIST]

---

### Post by Toz on 2014-08-05
I think you may be mis-interpreting the message you received. I don't think they've been permanently removed from your system - only from the panel. Right-click the panel and select Panel >> Panel Preferences, then click on the "Items" tab. Look for both the "Notification Area" and "Indicator Plugins" to be listed there. If they are not, then click the Plus sign and add them. This should bring back the battery and network icons for you.

---

### Post by Curtis_Bryant on 2014-08-05
You're right, Toz! Your instructions were enough to restore them. It would be odd if removing the panel item would have completely uninstalled it, and I'm glad that hadn't happened. I'm looking forward to learning my way around Xubuntu. I love how fast it runs. Firefox starts in 2 seconds!

---

