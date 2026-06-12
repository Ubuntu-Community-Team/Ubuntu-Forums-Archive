---
title: "Google Earth Never Launches"
date: 2011-10-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by willygatti on 2011-10-01
I installed Google Earth successfully with both Google's deb package, and the Google Earth deb package from Ubuntu Software Center on 64 Bit Ubuntu 11.10 Beta 2, but whenever I try to launch it from the dash nothing happens.  When I try to launch Google Earth from the terminal, I get the following error message:

```
./googleearth-bin: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```

How do I get Google Earth working properly in Ubuntu 11.10?

---

### Post by effenberg0x0 on 2011-10-01
Run the following command:


[07:31 ][al:AL-DESK:/$ cd /usr/lib
[07:31 ][al:AL-DESK:/usr/lib] ls -la libGL*
-rw-r--r-- 1 root root     654 2011-09-29 12:03 libGL.la
lrwxrwxrwx 1 root root      10 2011-09-29 12:03 libGL.so -> libGL.so.1
lrwxrwxrwx 1 root root      15 2011-09-29 12:03 libGL.so.1 -> libGL.so.280.13
-rwxr-xr-x 1 root root 1025968 2011-09-29 12:03 libGL.so.280.13

[07:31 ][al:AL-DESK:/] cd /usr/lib32
 [07:31 ][al:AL-DESK:/] ls -la libGL*
-rw-r--r-- 1 root root    656 2011-09-29 12:03 libGL.la
lrwxrwxrwx 1 root root     15 2011-09-29 19:07 libGL.so -> mesa/libGL.so.1
lrwxrwxrwx 1 root root     15 2011-09-29 12:03 libGL.so.1 -> libGL.so.280.13
-rwxr-xr-x 1 root root 794628 2011-09-29 12:03 libGL.so.280.13
lrwxrwxrwx 1 root root     11 2011-09-29 19:07 libGLU.so -> libGLU.so.1
lrwxrwxrwx 1 root root     20 2011-09-29 19:07 libGLU.so.1 -> libGLU.so.1.3.071100
-rw-r--r-- 1 root root 460448 2011-08-10 05:28 libGLU.so.1.3.071100

You'll notice your output differs from mine because there are broken links. Post your command results. If that is the case, we can help you fix the wrong / missing links.

Regards,
Effenberg

---

### Post by willygatti on 2011-10-01
After entering the command: ```
ls -la libGL
``` I get the  error message: ```
ls: cannot access libGL: No such file or directory
```.

---

### Post by OpSecShellshock on 2011-10-01
I think you need to put the * at the end of the command.

---

### Post by willygatti on 2011-10-01
After entering the ls -la libGL* command from /usr/lib, the terminal gives me the output:

```
lrwxrwxrwx 1 root root     18 2011-09-29 20:22 libGLEWmx.so.1.5 -> libGLEWmx.so.1.5.2
-rw-r--r-- 1 root root 292752 2011-08-04 18:57 libGLEWmx.so.1.5.2
lrwxrwxrwx 1 root root     16 2011-09-29 20:22 libGLEW.so.1.5 -> libGLEW.so.1.5.2
-rw-r--r-- 1 root root 337808 2011-08-04 18:57 libGLEW.so.1.5.2
```

After entering the same ls -la libGL* command from /usr/lib32, the terminal gives me the output:

```
lrwxrwxrwx 1 root root     15 2011-09-29 18:07 libGL.so -> mesa/libGL.so.1
lrwxrwxrwx 1 root root     11 2011-09-29 18:07 libGLU.so -> libGLU.so.1
lrwxrwxrwx 1 root root     20 2011-09-29 18:07 libGLU.so.1 -> libGLU.so.1.3.071100
-rw-r--r-- 1 root root 460448 2011-08-10 04:28 libGLU.so.1.3.071100
```

---

### Post by mc4man on 2011-10-01
> **willygatti said:**
> After entering the ls -la libGL* command from /usr/lib, the terminal gives me the output:
...
That's exactly what I show in a fresh 64 bit install of yesterday.
google earth works fine here,  from dash, launcher icon & terminal
(from a terminal I'd use this instead
google-earth

Installed google-earth-stable_current_amd_64 downloaded [from this site ]("http://www.google.com/earth/index.html")with dpkg
(also needed to install lsb-core with deps inc. ia32-libs & ttf-mscorefonts to get decent menus

If you got all of that maybe try deleting the .googleearth folder in your home folder

---

### Post by ronacc on 2011-10-01
installed the 64 bit G-E as mc4man said on my uptodate oneric with GS starts and runs fine , only complaint is that even though I did install the ttf-mscorefonts the menus still look like something you wouldn't want to step in .

---

### Post by kseise on 2011-10-01
Are you using an AMD/ATI card with the proprietary drivers?  If so, you need to install the fglrx-glx-ia32 package.  I saw something about the nvidia-glx-ia32 libraries on the Debian forums.  I guess the Nvidia package pulls in the right packages while the AMD one doesn't.  Google Earth is a 32 bit program and needs the ia32 libraries.

---

### Post by willygatti on 2011-10-01
I don't have a .googleearth folder in my home folder, and my graphics drivers are from Intel.

---

### Post by mc4man on 2011-10-01
> **ronacc said:**
>  only complaint is that even though I did install the ttf-mscorefonts the menus still look like something you wouldn't want to step in .It seems they get better once you restart

.googlearth is a hidden folder
I have nvidia here so can't comment about intel..

---

### Post by willygatti on 2011-10-03
Even when I view the hidden files, there is still no .googleearth folder in my home folder.

---

