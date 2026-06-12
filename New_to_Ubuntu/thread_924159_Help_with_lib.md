---
title: "Help with lib"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by kraici on 2008-09-19
When trying to compile wine i get this error:

```

/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
winegcc: gcc failed
make[2]: *** [winex11.drv.so] Error 2
make[2]: Leaving directory `/home/cynthia/wine-1.1.4/dlls/winex11.drv'
make[1]: *** [winex11.drv] Error 2
make[1]: Leaving directory `/home/cynthia/wine-1.1.4/dlls'
make: *** [dlls] Error 2

```

How do i fix this? I will greatly appreciate help.
Thank you in advance.

---

### Post by iaculallad on 2008-09-19
For the error message:

> /usr/bin/ld: cannot find -lXext

It means you will have to install 'libxext-dev'

```
sudo apt-get install libxext-dev
```

About the file:

```
ian@gutsy-gibbon:~$ apt-cache search libxext-dev
libxext-dev - X11 miscellaneous extensions library (development headers)
ian@gutsy-gibbon:~$ apt-cache policy libxext-dev
libxext-dev:
  Installed: (none)
  Candidate: 2:1.0.3-2build1
  Version table:
     2:1.0.3-2build1 0
        500 http://archive.ubuntu.com gutsy/main Packages
ian@gutsy-gibbon:~$ 

```

---

### Post by Titan8990 on 2008-09-19
Unless you absolutely need the latest version of WINE you can save yourself a headache and just install it from the repositories:

sudo apt-get install wine

---

