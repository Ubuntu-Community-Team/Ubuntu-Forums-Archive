---
title: "libhal and libtiff4"
date: 2015-06-26
forum: New to Ubuntu
---

### Post by kalvin4 on 2015-06-26
So I have an issue that looks like this :
```

kalvin@kalvin-computer:~$ /opt/cxoffice/bin/cxdiag
[MissingLibHal]
"Level"="Suggest"
"Title"="Missing 32bit libhal.so.1 library"
"Description"="This may be needed for Windows applications to automatically detect CD-ROM and USB key insertion."


[MissingLibTiff]
"Level"="Suggest"
"Title"="Missing 32bit libtiff.so.4 library"
"Description"="This is needed by some applications that need to manipulate TIFF images in their user interface."


[Properties]
"display.depth"="24"


[Properties]
"opengl.vendor"="ATI Technologies Inc."


[Properties]
"opengl.version"="4.4.13374 Compatibility Profile Context 15.20.1013"


[Properties]
"opengl.renderer"="AMD Radeon HD 6250 Graphics"

```

There was three errors of missing libs but was able to fix one of them following advice found here. I tried re installing the libraries but to no avail. I dont know what to do , My best guess is that the libraries are there but there is no link to connect them to where they need to be but I really have no idea. Please someone help thank you.

---

### Post by dino99 on 2015-06-27
Would you mind to tell us which ubuntu is ran ? you seems have installed a very old one; hal and the likes have been removed many years ago.

---

### Post by kalvin4 on 2015-06-27
Yes I installed 15.04 but when I run > /opt/cxoffice/bin/cxdiag
 Those were the libraries that I was told were missing.
This all started when I used WINE to try to install an estimating program on my computer that does not function properly. Trying to fix this problem has led me to this point.
I am trying to install and run a program called craftsman national estimator.

---

### Post by kalvin4 on 2015-06-27
This program " National Estimator " when installed says theres a problem initializing the ARViewer object when trying to access another part of the program and after I close that error window another one pops up telling me " Report Source is not a valid object " . I am led to believe that if I can somehow fix the library errors, that will also fix the software errors. IDK this is my first time using Ubuntu/Linux ..

---

### Post by dino99 on 2015-06-27
maybe add 'hal' from wincfg (wine config, libs tab)
sometime some wine's app works only if you set wine Os as 'xp' or 'some other OS'; needs to try a few settings

---

### Post by kalvin4 on 2015-06-27
I will try your suggestions and let you know thanks... Day2 of the battle...

---

### Post by kalvin4 on 2015-06-27
ok so after running winecfg I had a window pop up telling me that some files were missing and it can look for and download them for me. I clicked yes and afterwards this is what now shows on my screen
> kalvin@kalvin-computer:~$ /opt/cxoffice/bin/cxdiag[MissingLibTiff]
"Level"="Suggest"
"Title"="Missing 32bit libtiff.so.4 library"
"Description"="This is needed by some applications that need to manipulate TIFF images in their user interface."


[Properties]
"display.depth"="24"


[Properties]
"opengl.vendor"="ATI Technologies Inc."


[Properties]
"opengl.version"="4.4.13374 Compatibility Profile Context 15.20.1013"


[Properties]
"opengl.renderer"="AMD Radeon HD 6250 Graphics"


kalvin@kalvin-computer:~$ winecfg
fixme:ole:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}



The good news is that this solved the lihal missing library issue. I am still faced with the libtiff4 32bit library missing problem and cant seem to figure out how exactly to fix this.

---

