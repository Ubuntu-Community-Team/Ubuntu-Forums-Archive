---
title: "wxWidgets not found"
date: 2008-11-13
forum: Programming Talk
---

### Post by wmsedgar on 2008-11-13
Hi, I'm attempting to build the BOINC server, client, and API.  I keep getting the following error when I run ./configure even though I've verified that wxconfig is in my path and added /usr/lib to LD_LIBRARY_PATH.  Any suggestions?

================================================================================
WARNING: A suitable installation of wxWidgets could not be found
	 ==> building client without clientgui.

  If you add wxWidgets to your system, then this configure script will also
  configure your system to build the BOINC graphical client (clientgui).

  If wxWidgets is installed on your system, please check that wx-config is
  in the path, that the directory where wxWidgets libraries are installed
  (returned by 'wx-config --libs' command) is in LD_LIBRARY_PATH (or equivalent),
  and that wxWidgets version is 2.6.0 or above. Currently wxWidgets version
  2.6.0 (gtk based) is known to work with boinc_gui under Linux. You can
  use wx-config --version to find what version you have currently installed.

  NOTE: if building a portable client-release, you need the *static* version
  of the wx-libs installed!

  You can get wxWidgets by following the DOWNLOAD link at:
  [http://www.wxwindows.org/](http://www.wxwindows.org/)
================================================================================

---

### Post by snova on 2008-11-13
Install the 'libwxgtk2.8-dev' package.

---

### Post by wmsedgar on 2008-11-13
I already have libwxgtk2.8-dev installed.  Any other suggestions?

---

### Post by snova on 2008-11-13
Try the older version: libwxgtk2.6-dev.

Failing that, try wx2.6-headers.

---

### Post by wmsedgar on 2008-11-13
No dice unfortunately.  I already tried libwxgtk2.6-dev, and installed the headers. I'm going to do some more digging, but let me know if you come up with anything else.

---

### Post by wmsedgar on 2008-11-13
I just found the solution on BOINC forums in case anyone is interested. Problem is with BOINC server build script.  Here's the solution:

run:

wx-config --libs --unicode=yes

then, when you run configure, run it with the unicode enabled option:

./configure --enable-unicode

then it should find wxWidgets.  See this thread on BOINC forum:

[http://boinc.berkeley.edu/dev/forum_thread.php?id=2771&nowrap=true#20951](http://boinc.berkeley.edu/dev/forum_thread.php?id=2771&nowrap=true#20951)

---

