---
title: "/usr/bin/ld: cannot find -llibopencv_highgui.so"
date: 2013-01-16
forum: Packaging and Compiling Programs
---

### Post by oujeboland on 2013-01-16
OMG i'm almost crazy , i did whatever i could  but it happens again.
my lib files are on /usr/local/lib and i insertet the path and lib files caption as u c at the image below , but as u c i get error and the build is not successful ! 
[IMG]https://sites.google.com/site/myuploadedimages/_/rsrc/1358374528944/home/opencvforum/tutorials1/Screenshot%20from%202013-01-17%2001%3A27%3A48b.png[/IMG]

---

### Post by wwwmoderation on 2013-01-16
I have the same problem like this also and i dont know what will i do next:(


Cheers
[http://onlinemoderationservices.com](http://onlinemoderationservices.com)

---

### Post by steeldriver on 2013-01-16
I don't know how your IDE handles these things, but by convention the '-l' expands to 'lib' i.e. to link libopencv_highgui.so you would specify that as 
**-lopencv_highgui** not **-l[COLOR=Red]lib[/COLOR]opencv_highgui[COLOR=Red].so[/COLOR]**

---

### Post by oujeboland on 2013-01-17
> **steeldriver said:**
> I don't know how your IDE handles these things, but by convention the '-l' expands to 'lib' i.e. to link libopencv_highgui.so you would specify that as 
**-lopencv_highgui.so** not **-l[COLOR=Red]lib[/COLOR]opencv_highgui.so**

the lib prefix is in the main filename in the new version of the opencv , so files are named like this: libopencv_highgui.so libopencv_flann.so

---

### Post by MadCow108 on 2013-01-17
all libraries on unix systems start with lib and end with .so (+ possible versioning suffixes like .so.1) or .a (static library)
so you don't have to specify it, the compiler it will fill it in
libopencv_highgui.so -> -lopencv_highgui
etc.
in your ide you probably just have to remove the lib and the .so from your settings

---

### Post by oujeboland on 2013-01-21
you both were right . i didn't understand at first.
is there any  thanks button !

---

