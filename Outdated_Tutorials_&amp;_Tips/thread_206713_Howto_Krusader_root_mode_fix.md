---
title: "Howto Krusader root mode fix"
date: 2006-06-30
forum: Outdated Tutorials &amp; Tips
---

### Post by Matchless on 2006-06-30
Hi,
   Some people have been having problems running Krusader from the root mode menu icon. Here is a fix:
**_Howto Krusader root mode fix_**

Krusader 1.6 has some shortcomings and crashes when you try to open /dev etc 
and version 1.7 fails when trying to open in root mode.

By default two menu icons are created when Krusader 1.7 is installed called Krusader and Krusader root mode. When trying to run by using the Krusader root mode, it fails.

To fix this open the Icon properties from the menu editor and add kdesu in the command line in front of krusader with a space (kdesu krusader). The trick here is then to ensure at the same time that Run as other user  -  root is also enabled.

Now your root mode krusader will run perfectly

---

