---
title: "Ubuntu 8.10 (Intrepid Ibex) New network manager confusion"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by brack on 2008-11-12
There are several things I find uncomfortable with new network manager:

1. There is no longer "Manual configuration..." menu item on left-click on network-status icon in gnome.

2. Left-click on network status icon brings the same window as left-click->properties. I would assume that Properties should be different from status.

3. There is no Hosts configuration tab in Network configuration GUI so I have to edit /etc/hosts via terminal.

4. I couldnt save manual setup of my IP until something happened which helped me to do so. (i just kept trying for a few days, if you can call this "solution").

does anyone know solutions for those?

---

### Post by drakeman007 on 2008-11-12
> **brack said:**
> There are several things I find uncomfortable with new network manager:

1. There is no longer "Manual configuration..." menu item on left-click on network-status icon in gnome.

2. Left-click on network status icon brings the same window as left-click->properties. I would assume that Properties should be different from status.

3. There is no Hosts configuration tab in Network configuration GUI so I have to edit /etc/hosts via terminal.

4. I couldnt save manual setup of my IP until something happened which helped me to do so. (i just kept trying for a few days, if you can call this "solution").

does anyone know solutions for those?

You tried with this?


[http://ubuntuforums.org/showthread.php?t=979372](http://ubuntuforums.org/showthread.php?t=979372)

there is a inside link in the post too, you can check it out.

---

### Post by brack on 2008-11-12
> **drakeman007 said:**
> You tried with this?


[http://ubuntuforums.org/showthread.php?t=979372](http://ubuntuforums.org/showthread.php?t=979372)

there is a inside link in the post too, you can check it out.

as I say - I solved the static ip problem. When I changed ip settings to static, it suddenly asked me for password (it dint do it before) and then I decided to logout and login again. Static ip was there since. But I still have other questions standing. I didnt find the way to start network manager from within network status applet, and I dont see any part of new network manager managing hosts. Am I missing something?

---

### Post by brack on 2008-11-13
Ok I figure part of the question: There is no right-click menu item on network status icon because it is gnome-network-status-applet but not nm-applet so then the question is HOW to get nm-applet on the panel? shouldnt it be automatically?

---

### Post by whollycow on 2008-11-28
These bug filings may help:

[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bugs](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bugs)

especially this one:

[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/289466](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/289466)

---

