---
title: "Help with recovering functionality of ccsm (compiz configuration settins manager)"
date: 2012-04-21
forum: New to Ubuntu
---

### Post by jps2012 on 2012-04-21
Folks, I'm hoping you can help me understand some error messages in ccsm, and possibly fix what's wrong. A couple of days ago I uninstalled ccsm because it wasn't allowing me to configure much at all. Seemed pretty useless to me. 

I thought MAYBE something had gone wrong with the initial install, therefore I decided to gamble on reinstalling it to (I'd hoped) repair whatever was broken. After the reinstall, I couldn't close out programs with the red circle-x; I lost my of the boundaries to my windows (oftentimes there's no clear distinction now between where one window begins and another ends). 

I ran ccsm from Terminal and got this result (maybe you folks know what this is saying, and would be willing to tell me how to dix the errors): 

Initializing core options...done
/usr/lib/python2.7/dist-packages/ccm/Window.py:92: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  self.LeftPane.pack_start(page.LeftWidget,   True, True)
/usr/lib/python2.7/dist-packages/ccm/Window.py:95: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  self.show_all()
/usr/lib/python2.7/dist-packages/ccm/Widgets.py:1567: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed

Would those errors be the fundamental cause of the missing window borders, lost GUI elements? 

Many thanks.

---

