---
title: "Need help in compiling firefox on ubuntu 7.10"
date: 2008-04-01
forum: Packaging and Compiling Programs
---

### Post by yinglcs2 on 2008-04-01
Hi,

I am trying to compile firefox 2.0.0.11 on ubuntu 7.10.  And I am getting the following error while linking.

I have checked that my LD_LIBRARY_PATH has /usr/lib
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib:/usr/lib:

And I do have 

 $  pwd
/usr/lib
 $ ls -la libXt*
-rw-r--r-- 1 root root 429164 2007-05-21 07:27 libXt.a
lrwxrwxrwx 1 root root     14 2007-10-18 17:06 libXt.so -> libXt.so.6.0.0
lrwxrwxrwx 1 root root     14 2007-10-18 17:06 libXt.so.6 -> libXt.so.6.0.0
-rw-r--r-- 1 root root 326564 2007-05-21 07:27 libXt.so.6.0.0

Can you please tell me how can I resolve my problem?

gtk2xtbin.o: In function `xt_client_focus_listener':
/home/yinglcs/firefox_working/firefox2.0.0.11/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:826: undefined reference to `XtDisplay'
/home/yinglcs/firefox_working/firefox2.0.0.11/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:828: undefined reference to `XtWindow'
/home/yinglcs/firefox_working/firefox2.0.0.11/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:834: undefined reference to `XtWindowToWidget'
/home/yinglcs/firefox_working/firefox2.0.0.11/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:845: undefined reference to `XtWindowToWidget'
collect2: ld returned 1 exit status
make[3]: *** [libgtkxtbin.so] Error 1
make[3]: Leaving directory `/home/yinglcs/firefox_working/firefox2.0.0.11/mozilla/firefox-objdir/widget/src/gtkxtbin'
make[2]: *** [tier_9] Error 2
make[2]: Leaving directory `/home/yinglcs/firefox_working/firefox2.0.0.11/mozilla/firefox-objdir'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/yinglcs/firefox_working/firefox2.0.0.11/mozilla/firefox-objdir'
make: *** [build] Error 2

---

