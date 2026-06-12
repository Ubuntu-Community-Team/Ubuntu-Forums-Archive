---
title: "Device Manager Could Not Found!"
date: 2012-05-05
forum: New to Ubuntu
---

### Post by punit144 on 2012-05-05
Hi,
I Just Installed Ubuntu 12.04 Today But i am Not able to find my device Manager Anywhere.
I Dont Have Administration in my System Setting.
Please Can Anyone Give me the Right Directions
Thanks,

---

### Post by Rodney9 on 2012-05-05
I'm not sure what you mean, all your system settings are in 'System Settings' see the screen shot below - 


Help Guides to Ubuntu Precise-Pangolin version 12.04

[http://wp.me/p1G6ys-WK](http://wp.me/p1G6ys-WK)

[http://beginlinux.com/blog/2012/04/getting-help-with-ubuntu-12-04-lts-precise-pangolin/](http://beginlinux.com/blog/2012/04/getting-help-with-ubuntu-12-04-lts-precise-pangolin/)

Rodney

---

### Post by alphapapa on 2012-08-17
Try this : [https://help.ubuntu.com/community/HardInfo](https://help.ubuntu.com/community/HardInfo)

HardInfo is a hardware analysis, system benchmark and report generator.

Once you install the package, Simply select 'Generate Report' from the top toolbar, a dialogue box will appear allowing you to export all desired computer, device, network or benchmark results to a HTML file. Upon completion an option to open the file immediately for viewing is provided.

Hope this is what you are looking for.! :guitar:

---

### Post by gordintoronto on 2012-08-17
What do you want to do?

Device Manager is part of Windows, not Linux.

Perhaps you want "Additional Drivers".

---

### Post by thompsw on 2013-03-20
> **gordintoronto said:**
> What do you want to do?

Device Manager is part of Windows, not Linux.

Perhaps you want "Additional Drivers".

I'm also looking for a device manager.  I just upgraded from 10.something and used to use the gnome-device-manager to check on things attached to usb, get uuids on new/modificed disk drives etc.

Dave.

---

### Post by thompsw on 2013-03-20
I just tried hardinfo and while it provides lots of information, it doesn't seem to have the level of detail that the gnome-device-manager provides.

---

### Post by ibjsb4 on 2013-03-20
gnome-device-manager was last included in 10o4.

[URL="http://packages.ubuntu.com/lucid/gnome-device-manager"]http://packages.ubuntu.com/lucid/gnome-device-manager

[/URL]Try

```
sudo lshw
```

---

### Post by gordintoronto on 2013-03-20
If you want a detailed description of your hardware, open Terminal and enter this command:
sudo lshw -html > Desktop/myconfig.htm

If you double-click on myconfig.htm, it should open in your browser, and give you a nicely formatted report about your hardware.

---

