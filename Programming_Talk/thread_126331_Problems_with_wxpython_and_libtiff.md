---
title: "Problems with wxpython and libtiff"
date: 2006-02-06
forum: Programming Talk
---

### Post by hawking on 2006-02-06
Friends I want to write a python application with wxpython which will use system tray. I first tried the example at [http://wiki.wxpython.org/index.cgi/FlashingTaskbarIcon](http://wiki.wxpython.org/index.cgi/FlashingTaskbarIcon) to test and look how it works. But I got this error : 
"ImportError: libtiff.so.3: cannot open shared object file: No such file or directory"
It turns out Ubuntu uses libtiff4 instead of libtiff3 so I tried linking libtiff.so.4 to libtiff.so.3 and then I got this error :

" ImportError: /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core_.so: symbol _ZTV19wxInternetFSHandler, version WXU_2.6 not defined in file libwx_base u_net-2.6.so.0 with link time reference" 

Can someone help me make this code work?
Regards,

---

### Post by vanth13 on 2006-10-07
I have the same problem with libtiff.so.3...

I need it... is there a way to get it? or I have to change linux release to run an app wanting it???

---

