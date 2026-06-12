---
title: "Installing TOra and Oracle client (Jaunty)"
date: 2010-08-23
forum: Outdated Tutorials &amp; Tips
---

### Post by redcharlie on 2010-08-23
In case anyone else needs TOra on ubuntu.

**First, install Oracle client**.  Download the rpms for Oracle instant client, convert them to .deb with alien, and install with dpkg.  You will need two Oracle rpms, the basic and the odbc.  I also always get the sqlplus rpm as it is useful.  Don't get the basic lite as it is not sufficient for use with either odbc or sqlplus.

See: [http://www.gena01.com/forum/gena01-blog/oracle-instant-client-11g-on-ubuntu/](http://www.gena01.com/forum/gena01-blog/oracle-instant-client-11g-on-ubuntu/)

**Second, set all necessary environment vars**.  Determine the actual install path of the oracle instant client (should be something like "/usr/lib/oracle/11.2/client" below) and set the value of ORACLE_HOME to that.

Example (from [http://froebe.net/blog/2008/10/22/installing-oracle-instant-client-and-dbdoracle-on-ubuntu-linux-804-server-jeos/](http://froebe.net/blog/2008/10/22/installing-oracle-instant-client-and-dbdoracle-on-ubuntu-linux-804-server-jeos/))
 export ORACLE_HOME=/usr/lib/oracle/11.2/client
 export TNS_ADMIN=${ORACLE_HOME}
 export PATH=${ORACLE_HOME}/bin:${PATH}
 export CLASSPATH=${ORACLE_HOME}/classes:${CLASSPATH}
 export LD_LIBRARY_PATH=${ORACLE_HOME}/lib:${LD_LIBRARY_PATH}
 export SQLPATH=${ORACLE_HOME}/bin

Put this in some file that you will source before running TOra, like /etc/profile, or ~/.bash_profile, etc.

**Third, fix libpq.so**
TOra 2.1.2 requires libpq.so.4
My Jaunty install has /usr/lib/libpq.so.5.1, with a symlink for libpq.so.5 pointing to libpq.so.5.1
So, I just made another symlink, libpq.so.4, which also points to libpq.so.5.1   Seems to work, I've tested it by connecting to my local postgres install.

**Finally, get TOra**.  Download TOra 2.1.2 rpm from sourceforge.  ( I got the 32bit rpm for redhat el5) and convert it to .deb with alien.  Install with dpkg, and voila, I had a working TOra install!

If Tora complains about missing .so libraries on startup, make sure your Oracle home, path, classpath, etc are correct.  And if it's whining about needing older versions of stuff you have (like libpq.so) try the symlink trick to see if the newer .so libraries will work.

Hope this works for you.
-charlie

---

