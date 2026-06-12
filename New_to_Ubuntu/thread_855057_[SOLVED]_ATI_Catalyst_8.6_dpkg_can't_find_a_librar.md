---
title: "[SOLVED] ATI Catalyst 8.6 dpkg can't find a library"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by porchrat on 2008-07-10
Hi all I'm relatively new to Linux and even newer to Ubuntu.  I'm running 8.04 with kernel 2.6.24-19 on a brand new machine.

On to my problem.  I tried recently installing the new 8.6 Catalyst drivers to run a radeon 4850.  Got the instructions from this site [http://wiki.cchtml.com/index.php?title=Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php?title=Ubuntu_Hardy_Installation_Guide")

It seemed to work as the resolution on the screen definately changed, however I couldn't install Catalyst Control Center.

I then decided to try another install that i found at [https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

However now when I try to build the package everything seems to go fine until it prints out this:

```
dpkg-shlibdeps: failure: couldn't find library libGL.so.1 needed by debian/xorg-driver-fglrx/usr/sbin/atieventsd (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: command returned error code 512
```

Any advice on this would be most appreciated.

---

### Post by porchrat on 2008-07-10
OK I think I have managed to narrow down the problem.  I can't remove xorg-driver-fglrx.  If I could just remove it I could do a fresh install.

Gives me this error:

"E: xorg-driver-fglrx: subprocess post-removal script returned error exit status 2"

Anyone have any idea how to fix this?

---

### Post by porchrat on 2008-07-10
Managed to get the drivers installed again by editing the status file of dpkg to ignore the previously installed (and now broken) xorg-driver-fglrx.  Works now only I can't open catalyst control centre.  Will keep trying until I get it though.

---

### Post by porchrat on 2008-07-10
reinstalled the amdcccle from the binary and used

```
"DISPLAY=:0 amdcccle"
```

control centre started straight away.

---

