---
title: "packages names are needed"
date: 2014-11-17
forum: New to Ubuntu
---

### Post by engineer2 on 2014-11-17
Hello
I'm using ubuntu 12.04LTS x64 and i need these packages but i don't know what its exact names for ubuntu 
can anyone give me the names or tell me how i can figure them out?

these are the packages:
libavcodec.55
libavfilter.4
libswresample.0
libavformat.55
libavutil.52
libswscale.2
libpostproc.52
libavdevice.55
libavcodec.55
libavfilter.4
libswresample.0
libavformat.55
libavutil.52
libswscale.2
libpostproc.52
libavdevice.55

---

### Post by vasa1 on 2014-11-17
Try **apt-cache search**:```
08:58 PM ~ $ apt-cache search libavdevice
libavdevice-dev - Development files for libavdevice
libavdevice-extra-53 - Libav device handling library (transitional package)
libavdevice53 - Libav device handling library
08:58 PM ~ $ apt-cache search libpostproc
libpostproc-dev - FFmpeg derived postprocessing library - development headers
libpostproc52 - FFmpeg derived postprocessing library
08:59 PM ~ $ 
```

---

### Post by engineer2 on 2014-11-24
Hello

i'm using Ubuntu 12.04 LTS X64 and i have an application that needs packages that i couldn't find with apt-get or apt-cache search and i did apt-get update many times. i really need these packages  :

libavcodec.55 
libavformat.55
 libavdevice.55
 libavcodec.55

i used previous version like .52 .53 but it did not work and this is the error i receive:

[http://s17.postimg.org/mmvzeq7jj/20141120_201607.jpg](http://s17.postimg.org/mmvzeq7jj/20141120_201607.jpg)

---

### Post by carlwsnyder on 2014-11-24
I believe the packages you are looking for are in the ubuntu-restricted-extras meta-package.  These are packages with proprietary restrictions.

---

### Post by buzzingrobot on 2014-11-24
I don't believe those are available in the repos for 12.04. Perhaps a PPA is available?

---

### Post by engineer2 on 2014-11-24
so what should i do ?

---

### Post by vasa1 on 2014-11-24
> **engineer2 said:**
> so what should i do ?
Is this thread not a continuation of [http://ubuntuforums.org/showthread.php?t=2253118&p=13168883#post13168883](http://ubuntuforums.org/showthread.php?t=2253118&p=13168883#post13168883) ?

---

### Post by nerdtron on 2014-11-24
Man this will be hard. Running a .exe program in Linux and trying to solve compatibility problems.
What is this software? Did it ever worked before in Linux?
Have you tried alternatives to this software?

---

### Post by coffeecat on 2014-11-24
> **vasa1 said:**
> Is this thread not a continuation of [http://ubuntuforums.org/showthread.php?t=2253118&p=13168883#post13168883](http://ubuntuforums.org/showthread.php?t=2253118&p=13168883#post13168883) ?

Indeed. Threads merged.

@engineer2, please do not post duplicate threads for the same issue.

**Edit:** I have removed the img tags from your giant image in post #3 making it a hyperlink. You are very welcome to post images but please be considerate of those using mobile devices to view the forum and those with limited bandwidth. If you wish to use an offsite image hosting service, please limit the size of your images. Better still, use the inbuilt forum utility to upload images and attach clickable thumbnails to your post. Click on the Manage Attachments button below the advanced editor to use this utility.

---

### Post by buzzingrobot on 2014-11-24
> **engineer2 said:**
> so what should i do ?

Your choices are really limited to building the packages yourself from source or locating them in a PPA or other third-party location.  That assumes, of course, that those versions are compatible with 12.04 and have dependencies that can be satisfied.

Or, find an older version of the app you want to run that works with the packages released for 12.04.

---

