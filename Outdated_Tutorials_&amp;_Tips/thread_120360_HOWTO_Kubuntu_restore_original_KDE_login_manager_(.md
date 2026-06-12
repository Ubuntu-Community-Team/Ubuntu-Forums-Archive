---
title: "HOWTO: Kubuntu: restore original KDE login manager (KDM)"
date: 2006-01-21
forum: Outdated Tutorials &amp; Tips
---

### Post by mendieta on 2006-01-21
If you have, as in my case, a customized KDE login manager, you may want to use it, instead of using Kubuntu's (excellent) theme. 

All you need to do is to set a line [color="blue"]**UseTheme=false**[/color] in the file  [color="blue"]**/etc/kde3/kdm/kdmrc**[/color]. That's it :cool:

Here is one way to do it. Type [alt]+[F2], to launch the "Run Command" dialog. Then type:

[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=5488&stc=1&d=113786095[/IMG]

Finally, set the line:

[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=5489&stc=1&d=1137861162[/IMG]

Save the file, logout from KDE and Voila !
:-D

Enjoy!,
Mendieta

---

### Post by Parkotron on 2006-02-07
A good tip, but personally I prefer to use the KDM Theme Manager. It's available from [http://www.kde-apps.org/content/show.php?content=22120](http://www.kde-apps.org/content/show.php?content=22120) , and very conveniently includes an Ubuntu deb.

---

