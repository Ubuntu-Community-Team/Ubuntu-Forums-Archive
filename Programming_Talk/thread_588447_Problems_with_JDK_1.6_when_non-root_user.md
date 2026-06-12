---
title: "Problems with JDK 1.6 when non-root user"
date: 2007-10-23
forum: Programming Talk
---

### Post by pitm@ster on 2007-10-23
Hi.

When I try to run Java (even simply java -version) as a non-root user I am presented with a dump error.  I am not sure why it is happening.  Running as root makes everything seem OK so far.  JDK 1.5 works fine as any user.

We are running Ubuntu Server 7.10.  I tried both the Sun download the the apt-get method for installing the JDK and get the same results.

Any help would be appreciated.

Here is the error.  There is also a dump log, but its not very useful either.

```

#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x1d683039, pid=10211, tid=3048614800
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0_03-b05 mixed mode, sharing)
# Problematic frame:
# C  0x1d683039
#
# An error report file with more information is saved as /tmp/hs_err_pid10211.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted

```

---

