---
title: "Place app in menu root with .desktop file"
date: 2010-05-11
forum: Programming Talk
---

### Post by AZorin on 2010-05-11
Hello,
I am trying to place an application I made in to the root of the application menu (where the software center is) using a .desktop file which I placed into /usr/share/applications. I managed to make it come up in menu>system>preferences and in the control panel by using Settings;DesktopSettings;GTK; as the category but I can't get it to come up in the root of the menu. What category commands should I use in the .desktop file to make it come up in the root of the menu? Also, is it possible to put the program into both the root of the menu and menu>system>preferences using two separate .desktop files or one ideally? Please help me.

Best Regards,
Azorin

---

### Post by derrick81787 on 2010-05-11
> **AZorin said:**
> Hello,
I am trying to place an application I made in to the root of the application menu (where the software center is) using a .desktop file which I placed into /usr/share/applications. I managed to make it come up in menu>system>preferences and in the control panel by using Settings;DesktopSettings;GTK; as the category but I can't get it to come up in the root of the menu. What category commands should I use in the .desktop file to make it come up in the root of the menu? Also, is it possible to put the program into both the root of the menu and menu>system>preferences using two separate .desktop files or one ideally? Please help me.

Best Regards,
Azorin

What does the Ubuntu Software Center .desktop file look like?  Can you find that in /usr/share/applications and basically just copy it?

---

### Post by AZorin on 2010-05-12
Sure! Here it is: 
```
[Desktop Entry]
Name=Ubuntu Software Center
GenericName=Software Center
Comment=Lets you choose from thousands of free applications available for Ubuntu
Exec=/usr/bin/software-center
Icon=softwarecenter
Terminal=false
Type=Application
Categories=PackageManager;GTK;System;Settings;
StartupNotify=true
X-Ubuntu-Gettext-Domain=software-center
```

Thanks,
AZorin

---

