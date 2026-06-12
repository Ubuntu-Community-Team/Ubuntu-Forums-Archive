---
title: "ndiswrapper help w/compaq f750us"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by richardd2137 on 2008-04-26
Ok I followed all the instructions from [http://ubuntuforums.org/showthread.php?t=749481]("http://ubuntuforums.org/showthread.php?t=749481") and but then I get to the part where ndiswrapper is involved I get this messgae when I try to do this...
"richardd@*****:~/Desktop/wifi/WINXP_2K$ ndiswrapper -i net5211.inf
couldn't open net5211.inf: _**No such file or directory at /usr/sbin/ndiswrapper line 219**._
richardd@*****:~/Desktop/wifi/WINXP_2K$ "
Any help or suggestions?

---

### Post by Patricrawley on 2009-03-13
Try copying the driver you are trying to install to your desktop. Also make sure you run that with sudo otherwise it won't install.

---

### Post by lkraemer on 2009-03-14
From your post it looks like you are at the following:

/home/richard/Desktop/wifi/WINXP_2K/

and you are trying to install driver net5211.inf located there.
if you use 
```

ls -alt

```
you should see a listing which contains net5211.inf


In a Terminal window you can use:
```

pwd

```
(Print Working Directory) to show your location.  One usually is either
at the SOURCE SUBDIRECTORY or DESTINATION SUBDIRECTORY when copying
files/folders until they get enough experience with Linux.

If you copy all the files to a subdirectory in Linux, then
you can use:

```

locate net5211.inf 

```
to see the proper path.

Try:
```

ndiswrapper -i /proper/path/to/net5211.inf

```

lkraemer

---

