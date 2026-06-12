---
title: "FIX:  Gaps in GoogleMaps viewed with Firefox."
date: 2007-12-05
forum: Outdated Tutorials &amp; Tips
---

### Post by Maverickprowls on 2007-12-05
Some people have noted that after a recent update to Firefox, gaps appear in the view of GoogleMaps, and some other websites display poorly, with garbled graphics and poor text display in images.

I've tracked this down, on my system, to the following issue with the ImageZoom Plugin.  You can simply disable or uninstall the plugin, but for those who wish to keep the functionality of this otherwise extremely useful add-on can follow the steps below.

[LIST=1]
[*]Open a new tab in Firefox, type "about:config" (No quotes) and press return.
[*]type "imagezoom" (No quotes) into the search bar of this new window.
[*]Locate the line entitled "imagezoom.defaultGlobalZoom".
[*]Right-click on the number at the far right of this line (under the column titled "value") and select "Modify", set the value to 100.
[*]Restart Firefox (Not usually necessary, but ImageZoom needs to be restarted).
[*]Start Firefox and go to [GoogleMaps]("http://maps.google.com"), it should now display correctly.
[/LIST]

I hope that helps someone.

---

