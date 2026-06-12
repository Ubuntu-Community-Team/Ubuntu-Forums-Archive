---
title: "SeaMonkey automatic update has failed to complete"
date: 2012-10-18
forum: New to Ubuntu
---

### Post by Sleepy-zz-John on 2012-10-18
A few days ago,  on its own initiative,  my SeaMonkey browser and mail system tried to do an automatic update to v 2.4.1 but partially failed to complete such that my launch icon with command
"/home/john/seamonkey/seamonkey/seamonkey" no longer works at all.  Prior to the attempted upgrade my launch icon was working fine.

Command 'seamonkey' in Terminal does open v2.4.1 but at first it was producing 4 lines of:
```
(seamonkey-bin:1799): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap
```, 
I was able to get rid of that warning with tbe command 
```
sudo apt-get install gtk2-engines-pixbuf
```
which I obtained from Bug #853232.    

v2.4.1 does run now,  but it holds a Terminal window open all the time,  and it seems to have lost some (but not all) of my preferences in the process.  

I can't understand how 'seamonkey' from Terminal can launch it but my original launch icon can't.    Any suggestions?  

A somewhat fuller version of my story appears in [***this mozilla link***]("http://forums.mozillazine.org/viewtopic.php?f=40&t=2575541") where I first posted it,  but I'm now drawing a blank there because they're saying they're not familiar with Linux. 

I have some old backup copies of localstore.rdf and prefs.js,  and I'm wondering if it would be safe to try pasting either of these into my /home/.mozilla/seamonkey/xxxxxxxx.default folder in an attempt to restore the preference settings I seem to have lost.

---

