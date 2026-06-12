---
title: "uhh oh... I messed something up again"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by collinge on 2008-08-16
I am having a problem with my Logictech Quickcam E3560 and I tried to add a .tar file into my repository... now when I try to do updates I get an error message :

```
 E: Type 'http://downloads.sourceforge.net/qce-ga/qc-usb-0.6.6.tar.gz?modtime=1162648367&big_mirror=0deb' is not known on line 58 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
 
```

... Now what... and do you have any idea about my webcam.

---

### Post by Redache on 2008-08-16
First you need to edit your sources list and remove the line that points to the Tar file you added. To do this type

```
sudo gedit /etc/apt/sources.list
```

It references Line 58 as the problematic line, so it's more than likely the last one, easiest way is to click on find and look for "sourceforge" then delete the offending line.

then do a
```
 sudo apt-get update
```

and your repo's should now work.

I can't help you with the webcam though, sorry.

---

### Post by Yuki_Nagato on 2008-08-16
Can you visit this link in a browser?

The repository might be broken.

---

