---
title: "HOWTO: Acrobat Reader plugin with Opera."
date: 2005-08-05
forum: Outdated Tutorials &amp; Tips
---

### Post by sk545 on 2005-08-05
I had the most miserable time to get the acrobat reader plugin to work with opera, so here is how i did it:

1) sudo apt-get install lesstif1 lesstif2 lesstif2-dev libmotif3  libqt3-headers libqt3-mt-dev libqt3c102-mt libqthreads-12 qt3-dev-tools qt3-qtconfig acroread acroread-plugins mozilla-acroread

*Note: All the 'qt' packages are needed for the shared version of opera.  They are not necessary, but you will need them sooner or later so install them anyways.* 

2) sudo gedit /usr/bin/opera, and before line 52, insert this and save:

LD_PRELOAD="libXm.so:${LD_PRELOAD}"
export LD_PRELOAD

The full section of interest should now look like this:

===============================
# Opera enviroment
if test "${OPERA_DIR}" = '' ; then
if test -d /usr/share/opera/ ; then
OPERA_DIR=/usr/share/opera/
else
echo "OPERA_DIR unset and not in default location (/usr/share/opera/)"
exit 1
fi
fi
export OPERA_DIR

LD_PRELOAD="libXm.so:${LD_PRELOAD}"
export LD_PRELOAD
OPERA_LD_PRELOAD="${LD_PRELOAD}"
export OPERA_LD_PRELOAD
==================================

3) Go into Tools > Preferences > Advanced > Plug-in Options and set the plugin path to /usr/lib/mozilla-firefox/plugins or any of these directories if you don't have firefox installed:

/usr/lib/mozilla/plugins
/usr/lib/netscape/plugins-libc6
/usr/lib/mozilla-snapshot/plugins

Hit 'OK' to all the dialog messages, and restart opera.


4)  When opera comes up, in the address put in 'opera: plugins'.  It should list the adobe plugin in there.

4b) Go to Tools > Preferences > Advanced > Downloads.  In the "Quick Find" dropdown box, type 'pdf' and hit Enter.  Select 'application/pdf' and hit "Edit" on the right.  In the next dialog box, go all the way down and select "Use Plug-in" (the Adobe plugin should be there now).  Hit OK.

5) Go here to test the plugin:

[http://www.adobe.com/products/acrobat/pdfs/pdfaccess.pdf](http://www.adobe.com/products/acrobat/pdfs/pdfaccess.pdf)

6) Close opera, and start up a terminal.  Type 'opera --debugplugin' and see what output you get in the terminal...most things should come up as normal, if they don't you will get a  'opera: [plugin failed ]' message. There is one error that everyone is getting which is a bug:

[http://my.opera.com/forums/showthread.php?s=&threadid=95989&highlight=missingsyms.so](http://my.opera.com/forums/showthread.php?s=&threadid=95989&highlight=missingsyms.so)

Thanks to opera forums for all the help, the following thread in particular:

[http://my.opera.com/forums/showthread.php?s=&threadid=84286&pagenumber=2#post920847](http://my.opera.com/forums/showthread.php?s=&threadid=84286&pagenumber=2#post920847)

This method has been tested on Opera 8.10 Preview 2, static debian version.

Please post any problems you get.

---

### Post by Ramon on 2005-08-05
It works fine thnx. :D

---

### Post by sk545 on 2005-08-05
[QUOTE=Ramon]It works fine thnx. :D[/QUOTE]
 cool, good to hear.  Maybe we should have a thread devoted to opera and getting it up and running (all the extra things that are needed like libmotif, libtiff, etc).  Also, we could put in how to get other plugins to work with it (kaffeine, flash).  Here is a good link:

[http://www.opera.com/linux/docs/plugins/install/](http://www.opera.com/linux/docs/plugins/install/)

---

### Post by jrobcet on 2005-08-05
Works great! Thanks  :)

---

