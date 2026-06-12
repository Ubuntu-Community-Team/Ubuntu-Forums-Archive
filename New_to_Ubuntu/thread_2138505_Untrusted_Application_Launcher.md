---
title: "Untrusted Application Launcher"
date: 2013-04-24
forum: New to Ubuntu
---

### Post by benjie1 on 2013-04-24
Googled for info on this error and it tells me to change permission for that icon I want on the tesktop. But I can't change permission cause it says I am not the owner. Tried to get the icon from /usr/share/application and then copy to desktop.The icon does go to the desktop but fails to open the program and gives me the above error. How can this be fixed and also can I change permission if I am not the owner? The icon is for Open Office Writer. It does work from the Launcher. Have Ubuntu 12.2, and 32 bit on a Dell PC desktop, Inspiron 560. Thanks.

---

### Post by rburkartjo on 2013-04-24
open terminal type gksudo nautilus enter your password navigate to that desktop icon; click the icon ; then go to properties change the permission and make sure you tick execute-allow executing file as a program. happens to me sometimes when i drag an icon to the desktop.

---

### Post by benjie1 on 2013-04-24
Thanks. It works  fine.  Would I have to do this every time I get that Untrusted Application Launcher?  Is there a way to fix the permissions permanently?

---

### Post by Kopkins on 2013-04-24
Can't you just drag the launchers from the dash? Try searching the dash for the application you want then click-drag it to the desktop. I don't think that will cause any issues. You just have to make sure the dash doesn't cover the whole screen. 

Kopkins

---

### Post by deadflowr on 2013-04-24
Not sure about open office, but the libreoffice desktop files in /usr/share/applications are just links.
If you look in the properties of the open office desktop file, you can look and see if it  is a link, and the location, or not.
Link and Application desktop files work slightly different.
But if you find the actual Application desktop file you can simply copy it into your home folder desktop folder and then mark to execute, if need be.
If done right, the copied file should have changed to your permissions, and changing to root would be unnecessary.

---

### Post by benjie1 on 2013-04-24
That was the problem. Dragging it from the dash gave the Untrusted Application Launcher. That is why I contacted yoou and things are great now. Thanks.

---

### Post by benjie1 on 2013-04-24
A bit of stuff to digest but will do what you  mentioned. If the problem occurs again I 'm sure I can use gksudo nautilus again for another icon if need be .Just was wondering if there was a 'universal' way of making me the owner of icons in /usr/share/applications if it is necessary. It may not be. Thanks again and this is a good learning experience for a newbie.  :-)

Unable to find where to mark the post as [SOLVED]. I saw it and now I can't find it. Sorry.

---

### Post by col48 on 2013-04-24
An alternative way to change the permissions is using a Terminal command (chmod) which you would have to do using gksudo in this case as the files are presumably owned by root.  Using this, you can use a wildcard to include a batch of files, but be careful that you do not extend permissions more widely than you really need.

---

