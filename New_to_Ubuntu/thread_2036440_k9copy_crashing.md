---
title: "k9copy crashing"
date: 2012-08-01
forum: New to Ubuntu
---

### Post by diablo75 on 2012-08-01
I'm trying to help a friend by remote troubleshoot a problem with k9copy.  To get some verbose output I had him run k9copy from a terminal window and then copy/paste the whole terminal windows contents after the crash and send it to me in an email.  He said he is trying to make a backup copy of a DVD.

Here's the terminal output:
```
:~$ k9copy
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
kbuildsycoca4 running...
kbuildsycoca4(3604) KBuildSycoca::checkTimestamps: checking file timestamps
kbuildsycoca4(3604) KBuildSycoca::checkTimestamps: timestamps check ok
kbuildsycoca4(3604) kdemain: Emitting notifyDatabaseChanged ()
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Setting new source
New source:  QUrl( "file:///usr/share/sounds/KDE-Sys-Warning.ogg" ) 
Transitioning to state "playing"
State change
Moving from "null" 0 to "ready" 1
State change
Moving from "ready" 1 to "paused" 4
Stream changed to file:///usr/share/sounds/KDE-Sys-Warning.ogg
State change
Moving from "paused" 4 to "playing" 2
About to finish
Got next source. Waiting for end of current.
New source:  QUrl( "" ) 
Finally got a source
About to finish
Got next source. Waiting for end of current.
New source:  QUrl( "" ) 
Finally got a source
Transitioning to state "ready"
State change
Moving from "playing" 2 to "paused" 4
State change
Moving from "paused" 4 to "ready" 1
" /bin/sh -c /usr/bin/genisoimage -gui -v -graft-points -volid SECONDHAND_LIONS -appid k9copy -volset-size 1 -volset-seqno 1 -no-cache-inodes -udf -iso-level 1 -dvd-video /tmp/kde-gary/k9copy/SECONDHAND_LIONS |/usr/bin/wodim -dao -overburn -data -v dev=/dev/sr0 tsize=2251618s -"
Setting new source
New source:  QUrl( "file:///usr/share/sounds/KDE-Sys-Warning.ogg" ) 
Transitioning to state "playing"
State change
Stream changed to file:///usr/share/sounds/KDE-Sys-Warning.ogg
Moving from "ready" 1 to "paused" 4
State change
Moving from "paused" 4 to "playing" 2
About to finish
Got next source. Waiting for end of current.
New source:  QUrl( "" ) 
Finally got a source
About to finish
Got next source. Waiting for end of current.
New source:  QUrl( "" ) 
Finally got a source

*** libdvdread: CHECK_VALUE failed in /build/buildd/k9copy-2.3.8/src/dvdread/ifo_read.c:1226 ***
*** for ptl_mait->nr_of_vtss != 0 ***


*** libdvdread: CHECK_VALUE failed in /build/buildd/k9copy-2.3.8/src/dvdread/ifo_read.c:1260 ***
*** for ptl_mait->countries[i].pf_ptl_mai_start_byte + 16U * (ptl_mait->nr_of_vtss + 1) <= ptl_mait->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in /build/buildd/k9copy-2.3.8/src/dvdread/ifo_read.c:1226 ***
*** for ptl_mait->nr_of_vtss != 0 ***


*** libdvdread: CHECK_VALUE failed in /build/buildd/k9copy-2.3.8/src/dvdread/ifo_read.c:1260 ***
*** for ptl_mait->countries[i].pf_ptl_mai_start_byte + 16U * (ptl_mait->nr_of_vtss + 1) <= ptl_mait->last_byte + 1U ***

KCrash: Application 'k9copy' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
sock_file=/home/gary/.kde/socket-gary-desktop/kdeinit4__0
Transitioning to state "ready"
State change
Moving from "playing" 2 to "paused" 4
State change
Moving from "paused" 4 to "ready" 1

[1]+  Stopped                 k9copy
```

---

### Post by levlaz on 2012-08-01
I have not used k9copy in years. 

Why dont you try using [Brasero disc burner]("http://projects.gnome.org/brasero/")? It works great.

It should be installed by default, but if not;

```
 sudo apt-get install brasero 
```

---

### Post by diablo75 on 2012-08-01
> **levlaz said:**
> I have not used k9copy in years. 

Why dont you try using [Brasero disc burner]("http://projects.gnome.org/brasero/")? It works great.

It should be installed by default, but if not;

```
 sudo apt-get install brasero 
```

I believe what he's trying to do is make a copy of a commercial DVD or some form of video DVD where the source is larger than your standard ~4GB sized blank disk.  I don't think Brasero does any sort of re-encoding/shrinking...

---

