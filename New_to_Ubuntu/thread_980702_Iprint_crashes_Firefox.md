---
title: "Iprint crashes Firefox"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by arngrim on 2008-11-13
Hi,

when using Iprint (to get access to the University printers) Firefox crashes. Everything works ok until I press the "yes"-button to confirm installation of a specific printer (i.e. the installation of the Firefox plugin works but not the installation of the printer). Then Firefox crashes. I have searched a lot on the web but haven't found any solution. However, there seems to be other people having the same problem. I'm running Ubuntu 8.10 and Firefox 3.0.3.

Anyone?

Best,

Arngrim

---

### Post by PartisanEntity on 2008-11-13
I am not familiar with Iprint, is it a plugin for Firefox?

Try launching Firefox from the terminal and then use Iprint, post any error messages that appear in the terminal here in the thread.

---

### Post by arngrim on 2008-11-13
Hi,

the University is using Iprint in Novell NetWare to access printers. A user is installing printers using Iprint, a plugin in Firefox, IE etc.

Here is the output from the terminal:

...........................
*** glibc detected *** /usr/lib/firefox-3.0.3/firefox: munmap_chunk(): invalid pointer: 0xaf6eefb1 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7e023f4]
/usr/lib/libcups.so.2(httpClearFields+0x5f)[0xaf69572f]
/usr/lib/libcups.so.2[0xaf695997]
/opt/novell/lib/libiprint.so.1(MyCupsDoFileRequest+0xbd7)[0xaf7055c7]
/opt/novell/lib/libiprint.so.1(IPRINTSendRequest+0x81)[0xaf6f0b81]
/opt/novell/lib/libiprint.so.1(IPRINTGetUserRightsToPrinter+0x339)[0xaf6f68b9]
/opt/novell/iprint/plugin/npnipp.so[0xb07ff2a4]
/opt/novell/iprint/plugin/npnipp.so(NPP_New+0x1b2)[0xb07ff7e2]
/opt/novell/iprint/plugin/npnipp.so(Private_New+0x49)[0xb0800eb9]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb784630b]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb784cf97]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb784bdad]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb7854d75]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb74018aa]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb7405065]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb75072dd]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb7509b73]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb79ff56c]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb79cff88]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb79532c4]
/usr/lib/xulrunner-1.9.0.3/libxul.so[0xb77e8ab8]
/usr/lib/xulrunner-1.9.0.3/libxul.so(XRE_main+0x1d5c)[0xb724d508]
/usr/lib/firefox-3.0.3/firefox[0x80491ab]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7da9685]
/usr/lib/firefox-3.0.3/firefox[0x8048d11]
======= Memory map: ========
08048000-0804f000 r-xp 00000000 08:05 1557461    /usr/lib/firefox-3.0.3/firefox
0804f000-08050000 r--p 00006000 08:05 1557461    /usr/lib/firefox-3.0.3/firefox
08050000-08051000 rw-p 00007000 08:05 1557461    /usr/lib/firefox-3.0.3/firefox
083b1000-0977b000 rw-p 083b1000 00:00 0          [heap]
af560000-af562000 r-xp 00000000 08:05 4030511    /lib/libkeyutils-1.2.so
af562000-af564000 rw-p 00001000 08:05 4030511    /lib/libkeyutils-1.2.so
af564000-af56b000 r-xp 00000000 08:05 1515997    /usr/lib/libkrb5support.so.0.1
af56b000-af56c000 r--p 00006000 08:05 1515997    /usr/lib/libkrb5support.so.0.1
af56c000-af56d000 rw-p 00007000 08:05 1515997    /usr/lib/libkrb5support.so.0.1
af56d000-af576000 r-xp 00000000 08:05 4048054    /lib/tls/i686/cmov/libcrypt-2.8.90.so
af576000-af577000 r--p 00008000 08:05 4048054    /lib/tls/i686/cmov/libcrypt-2.8.90.so
af577000-af578000 rw-p 00009000 08:05 4048054    /lib/tls/i686/cmov/libcrypt-2.8.90.so
af578000-af59f000 rw-p af578000 00:00 0 
af59f000-af5c1000 r-xp 00000000 08:05 1515781    /usr/lib/libk5crypto.so.3.1
af5c1000-af5c2000 r--p 00022000 08:05 1515781    /usr/lib/libk5crypto.so.3.1
af5c2000-af5c3000 rw-p 00023000 08:05 1515781    /usr/lib/libk5crypto.so.3.1
af5c3000-af652000 r-xp 00000000 08:05 1515808    /usr/lib/libkrb5.so.3.3
af652000-af654000 r--p 0008e000 08:05 1515808    /usr/lib/libkrb5.so.3.3
af654000-af655000 rw-p 00090000 08:05 1515808    /usr/lib/libkrb5.so.3.3
af655000-af67d000 r-xp 00000000 08:05 1515777    /usr/lib/libgssapi_krb5.so.2.2
af67d000-af67e000 r--p 00028000 08:05 1515777    /usr/lib/libgssapi_krb5.so.2.2
af67e000-af67f000 rw-p 00029000 08:05 1515777    /usr/lib/libgssapi_krb5.so.2.2
af67f000-af6b2000 r-xp 00000000 08:05 1516620    /usr/lib/libcups.so.2
af6b2000-af6b3000 ---p 00033000 08:05 1516620    /usr/lib/libcups.so.2
af6b3000-af6b4000 r--p 00033000 08:05 1516620    /usr/lib/libcups.so.2
af6b4000-af6b5000 rw-p 00034000 08:05 1516620    /usr/lib/libcups.so.2
af6b5000-af6d9000 r-xp 00000000 08:05 1515855    /usr/lib/libglitz.so.1.0.0
af6d9000-af6da000 rw-p 00024000 08:05 1515855    /usr/lib/libglitz.so.1.0.0
af6ea000-af71a000 r-xp 00000000 08:05 4391019    /opt/novell/lib/libiprint.so.1.0.0
af71a000-af71b000 rw-p 0002f000 08:05 4391019    /opt/novell/lib/libiprint.so.1.0.0
af71b000-af71d000 rw-p af71b000 00:00 0 
af71d000-af761000 r--p 00000000 08:05 360563     /usr/share/fonts/truetype/msttcorefonts/Arial.ttf
af761000-af7a7000 r--p 00000000 08:05 360561     /usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf
af7a7000-af7d4000 r-xp 00000000 08:05 1983035    /usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/i386/libjavaplugin_nscp.so
af7d4000-af7da000 rw-p 0002d000 08:05 1983035    /usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/i386/libjavaplugin_nscp.so
af7da000-af7f0000 r-xp 00000000 08:05 1983550    /usr/lib/jvm/java-6-sun-1.6.0.10/jre/plugin/i386/ns7/libjavaplugin_oji.so
af7f0000-af7f4000 rw-p 00015000 08:05 1983550    /usr/lib/jvm/java-6-sun-1.6.0.10/jre/plugin/i386/ns7/libjavaplugin_oji.so
af7f4000-b07f4000 rw-p af7f4000 00:00 0 
b07f6000-b07f8000 r-xp 00000000 08:05 4030614    /lib/libcom_err.so.2.1
b07f8000-b07f9000 r--p 00001000 08:05 4030614    /lib/libcom_err.so.2.1
b07f9000-b07fa000 rw-p 00002000 08:05 4030614    /lib/libcom_err.so.2.1
b07fa000-b0803000 r-xp 00000000 08:05 4391022    /opt/novell/iprint/plugin/npnipp.so
b0803000-b0804000 rw-p 00008000 08:05 4391022    /opt/novell/iprint/plugin/npnipp.so
b0804000-b1155000 r-xp 00000000 08:05 1606479    /usr/lib/adobe-flashplugin/libflashplayer.so
b1155000-b1188000 rw-p 00950000 08:05 1606479    /usr/lib/adobe-flashplugin/libflashplayer.so
b1188000-b1273000 rw-p b1188000 00:00 0 
b1273000-b1285000 r-xp 00000000 08:05 1615419    /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so
b1285000-b1286000 r--p 00011000 08:05 1615419    /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so
b1286000-b1287000 rw-p 00012000 08:05 1615419    /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so
b1287000-b1297000 r-xp 00000000 08:05 1615418    /usr/lib/totem/gstreamer/libtotem-mully-plugin.so
b1297000-b1298000 r--p 0000f000 08:05 1615418    /usr/lib/totem/gstreamer/libtotem-mully-plugin.so
b1298000-b1299000 rw-p 00010000 08:05 1615418    /usr/lib/totem/gstreamer/libtotem-mully-plugin.so
b1299000-b12b1000 r-xp 00000000 08:05 1615417    /usr/lib/totem/gstreamer/libtotem-gmp-plugin.so
b12b1000-b12b2000 r--p 00018000 08:05 1615417    /usr/lib/totem/gstreamer/libtotem-gmp-plugin.so
b12b2000-b12b3000 rw-p 00019000 08:05 1615417    /usr/lib/totem/gstreamer/libtotem-gmp-plugin.so
b12b3000-b12b5000 r-xp 00000000 08:05 1515774    /usr/lib/libtotem-plparser-mini.so.12.0.3
b12b5000-b12b6000 r--p 00001000 08:05 1515774    /usr/lib/libtotem-plparser-mini.so.12.0.3
b12b6000-b12b7000 rw-p 00002000 08:05 1515774    /usr/lib/libtotem-plparser-mini.so.12.0.3
b12b7000-b12c7000 r-xp 00000000 08:05 1615415    /usr/lib/totem/gstreamer/libtotem-basic-plugin.so
b12c7000-b12c8000 r--p 0000f000 08:05 1615415    /usr/lib/totem/gstreamer/libtotem-basic-plugin.so
b12c8000-b12c9000 rw-p 00010000 08:05 1615415    /usr/lib/totem/gstreamer/libtotem-basic-plugin.so
b12c9000-b12e8000 r--p 00000000 08:05 360574     /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold.ttf
b12e8000-b1307000 r--p 00000000 08:05 360545     /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS.ttf
b1307000-b1308000 ---p b1307000 00:00 0 
b1308000-b1b08000 rwxp b1308000 00:00 0 
b1b08000-b1b49000 rw-p b1b08000 00:00 0 
b1b49000-b1b4d000 r-xp 00000000 08:05 4048060    /lib/tls/i686/cmov/libnss_dns-2.8.90.so
b1b4d000-b1b4e000 r--p 00003000 08:05 4048060    /lib/tls/i686/cmov/libnss_dns-2.8.90.so
b1b4e000-b1b4f000 rw-p 00004000 08:05 4048060    /lib/tls/i686/cmov/libnss_dns-2.8.90.so
b1b4f000-b1b50000 ---p b1b4f000 00:00 0 
b1b50000-b2350000 rwxp b1b50000 00:00 0 
b2350000-b2351000 ---p b2350000 00:00 0 
b2351000-b2b51000 rwxp b2351000 00:00 0 
b2b51000-b2b58000 r-xp 00000000 08:05 1556559    /usr/lib/firefox-3.0.3/components/libnkgnomevfs.so
b2b58000-b2b59000 ---p 00007000 08:05 1556559    /usr/lib/firefox-3.0.3/components/libnkgnomevfs.so
b2b59000-b2b5a000 r--p 00007000 08:05 1556559    /usr/lib/firefox-3.0.3/components/libnkgnomevfs.so
b2b5a000-b2b5b000 rw-p 00008000 08:05 1556559    /usr/lib/firefox-3.0.3/components/libnkgnomevfs.so
b2b5b000-b2c5f000 rw-p b2b5b000 00:00 0 
b2c5f000-b2cf4000 r--p 00000000 08:05 1654800    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b2cf4000-b2df8000 rw-p b2cf4000 00:00 0 
b2df8000-b2e81000 r--p 00000000 08:05 1654801    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b2e81000-b2e90000 r-xp 00000000 08:05 4031090    /lib/libbz2.so.1.0.4
b2e90000-b2e91000 r--p 0000f000 08:05 4031090    /lib/libbz2.so.1.0.4
b2e91000-b2e92000 rw-p 00010000 08:05 4031090    /lib/libbz2.so.1.0.4
b2e92000-b2ec3000 r-xp 00000000 08:05 1517248    /usr/lib/libcroco-0.6.so.3.0.1
b2ec3000-b2ec6000 rw-p 00030000 08:05 1517248    /usr/lib/libcroco-0.6.so.3.0.1
b2ec6000-b2ef6000 r-xp 00000000 08:05 1516882    /usr/lib/libgsf-1.so.114.0.8
b2ef6000-b2ef8000 r--p 0002f000 08:05 1516882    /usr/lib/libgsf-1.so.114.0.8
Aborted
...........................

Thanks!

Arngrim

---

### Post by Line on 2008-12-01
Hi
Firefox crashes for me to, I see Novel iPrint plug-in in the internet preferences

---

### Post by mcpondy on 2009-01-07
I am having a similar issue, has anybody had any luck with this?

---

### Post by angelkiller on 2009-03-02
> **arngrim said:**
> Hi,

when using Iprint (to get access to the University printers) Firefox crashes. Everything works ok until I press the "yes"-button to confirm installation of a specific printer (i.e. the installation of the Firefox plugin works but not the installation of the printer). Then Firefox crashes. I have searched a lot on the web but haven't found any solution. However, there seems to be other people having the same problem. I'm running Ubuntu 8.10 and Firefox 3.0.3.

Anyone?

Best,

Arngrim
I am also having the exact same issue. Only difference is that I'm on Firefox 3.0.6. I'd really like for help here because this is one of the last things that I have not gotten working in Ubuntu yet.

Thanks!

---

### Post by RadicalRaid on 2009-05-11
Same problem here.. Works for a classmate of mine though, that's quite odd.

---

### Post by Linux_Kid66 on 2009-05-11
Try an older version of firefox, or a different browser (anything but IE of course)

---

