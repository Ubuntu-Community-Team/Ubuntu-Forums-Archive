---
title: "realtek firmware not compling"
date: 2013-10-05
forum: Packaging and Compiling Programs
---

### Post by bonbon642 on 2013-10-05
hello

i am trying to get my TL-WN823N usb wifi dongole working. i found out that the current firmware is not conpatable with my kernel. i found another post and they have a patch but i am getting error's there too.

output for uname -a

3.2.0-4-powerpc #1 Debian 3.2.46-1+deb7u1 ppc GNU/Linux

output for lsusb

Bus 001 Device 002: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter

the error i got from trying to "make" the driver from realtek:

[http://pastebin.com/9gisS2Pi](http://pastebin.com/9gisS2Pi)

the other post where they had the same problem:

[http://ubuntuforums.org/showthread.php?t=1881434](http://ubuntuforums.org/showthread.php?t=1881434)

i am not really sure what to do with the patch. i put it in the driver folder after i extracted the tar.gz.
it then it ask me for the file to patch:

root@greenman:/home/bon/Downloads/rtl2/driver# patch -p1 < /home/bon/Downloads/rtl2/driver/compile_fixes 
can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|Index: rtl_92ce_92se_92de_linux_mac80211_0004.0816.2011/rtl8192de/phy.c
|===================================================================
|--- rtl_92ce_92se_92de_linux_mac80211_0004.0816.2011.orig/rtl8192de/phy.c
|+++ rtl_92ce_92se_92de_linux_mac80211_0004.0816.2011/rtl8192de/phy.c
--------------------------
File to patch: 

this is the first part of the patch file "compile_fixes" :

Index: rtl_92ce_92se_92de_linux_mac80211_0004.0816.2011/rtl8192de/phy.c
===================================================================
--- rtl_92ce_92se_92de_linux_mac80211_0004.0816.2011.orig/rtl8192de/phy.c
+++ rtl_92ce_92se_92de_linux_mac80211_0004.0816.2011/rtl8192de/phy.c
@@ -1697,7 +1697,7 @@ static u8 _rtl92d_phy_patha_iqk(struct i
     RTPRINT(rtlpriv, FINIT, INIT_IQK,
         ("Delay %d ms for One shot, path A LOK & IQK.\n",
          IQK_DELAY_TIME));
-    udelay(IQK_DELAY_TIME * 1000);


i was thinking there is a newer driver and i need to update the patch files. but i have no idea what to change.

any idea's?

from ben

---

### Post by bonbon642 on 2013-10-07
bump

---

