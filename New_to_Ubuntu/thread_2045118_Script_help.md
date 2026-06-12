---
title: "Script help"
date: 2012-08-20
forum: New to Ubuntu
---

### Post by bilboubu on 2012-08-20
etc/pm/sleep.d/afile.sh


#!/bin/sh


case "$1" in
suspend|hibernate)
/etc/init.d/tvheadend stop
;;
resume|thaw)
/usr/bin/wakeonlan 00:1d:92:dd:1a:0d
sleep 20
/etc/init.d/tvheadend start
killall -9 xbmc.bin
;;
esac


Why is it that in the above the wakeonlan does not run until AFTER the sleep 20? I want the remote pc to wakeup before xbmc is restarted.

---

### Post by bilboubu on 2012-08-21
This is bugging me now, it seems that now matter how long or where I put the sleep after "wakeonlan" the media/library server still does not wake up until xbmc re-appears so if I put 

/usr/bin/wakeonlan 00:1d:92d:1a:0d
sleep 100
/etc/init.d/tvheadend start
killall -9 xbmc.bin

The remote computer will not wake up until after 100 seconds and xbmc has restarted, that does not make sense to me? If 20 seconds the server wakes after 20 etc.

Also is killall -9 xbmc.bin about the best way to restart xbmc from a resume script or is there a better way (i dont lose sound this way)

Thanks

---

