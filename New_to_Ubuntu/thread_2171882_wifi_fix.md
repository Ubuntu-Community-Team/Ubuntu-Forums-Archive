---
title: "wifi fix"
date: 2013-09-02
forum: New to Ubuntu
---

### Post by lamont2 on 2013-09-02
[B]Re: Wireless not working in Ubuntu 12.04

[/B][INDENT]                     Please do:
     ```

     sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```  
     ```

     sudo apt-get install linux-firmware-nonfree
```  
     ```

     sudo modprobe b43
```  
 Then if it does not come on try:
     ```

     sudo rfkill unblock all
``` 
 The wl driver will work with your device but I believe that the b43 driver works better IMO.
 Thanks
[/INDENT]


[[COLOR=#dd4814]this turns my wifi on,but if i shut laptop off it wount work unless i do this again[/COLOR]]("https://help.ubuntu.com/community/CompositeManager")

---

### Post by newb85 on 2013-09-02
This initial post seems to be a duplicate of [http://ubuntuforums.org/showthread.php?t=1966633&page=9&p=12776707#post12776707](http://ubuntuforums.org/showthread.php?t=1966633&page=9&p=12776707#post12776707).

It is poorly formatted (doesn't have proper code tags).

Moreover as an initial post, it's a tutorial, not a support request, so it was posted in the wrong forum.  Also, the title is very poorly crafted for this purpose.

---

### Post by Frogs Hair on 2013-09-02
***Code tags added***

---

### Post by varunendra on 2013-09-03
lamont2,

If you need help with your wireless, please follow the "Wireless Script" link in my signature > follow the instructions in the linked post and post back (attach) the "wireless-info.txt" file it creates.

And if English is not a problem for you, please post the details of the problem, with any backgrounds if necessary. Thanks.

---

