---
title: "OpenCV and OpenGL"
date: 2007-11-05
forum: Programming Talk
---

### Post by Zacharias on 2007-11-05
hi guys

i want to use opencv and opengl on my c and c++ programmes. How can i install them to my gutsy gibbon ?

Thanks for your help

---

### Post by smartbei on 2007-11-05
For OpenCV, l suggest going to [http://sourceforge.net/project/showfiles.php?group_id=22870](http://sourceforge.net/project/showfiles.php?group_id=22870) and downloading the version for Linux.

I haven't used OpenCV on Linux yet, but I have somewhat extensively on Windows so I can't really help you with the installation. As for OpenGL, you should probably take a look at this thread:
[http://ubuntuforums.org/showthread.php?t=90890](http://ubuntuforums.org/showthread.php?t=90890)

Just out of interest, what are you working on?

---

### Post by hod139 on 2007-11-05
There is an opencv package in ubuntu (libcv-dev).  As long as you are running a recent version of ubuntu, it is up to date.  The most recent openCV release is 1.0, which is in the repository.  No need to install anything manually.

---

### Post by smartbei on 2007-11-05
Nice, didn't see that. BTW is there a way to search using aptitude from the command line through the package descriptions, and not just the package names?

---

### Post by hod139 on 2007-11-05
"apt-cache search" searches descriptions.

```

apt-cache search opencv

```returns
```

libcv-dev - development files for libcv
libcv0.9-0c2 - computer vision library
libcvaux-dev - development files for libcvaux
libcvaux0.9-0c2a - computer vision extension library
libhighgui-dev - development files for libhighgui
libhighgui0.9-0c2 - computer vision GUI library
opencv-doc - OpenCV documentation and examples

```

**EDIT:** My laptop is running dapper, which is why the packages are so old

---

### Post by Zacharias on 2007-11-06
thanks your all answers, now i am setting up some packages that i found by the apt-get chache opencv.

and smartbei i am interested in cognitive science and security, i took a project about kind of image processing.

---

