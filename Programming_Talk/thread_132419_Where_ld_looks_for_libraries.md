---
title: "Where ld looks for libraries"
date: 2006-02-18
forum: Programming Talk
---

### Post by jackrabbit123 on 2006-02-18
I'm trying to compile Qt and it is built with Xrender support.  configure can find it but when I am compiling, specifically linking, ld reports that it can't find -lXrender.  I have libXrender.so in /usr/lib which I thought was always checked regardless of what's in the the -L fields.  It also includes the directory, -L/usr/X11R6/lib.  I'm using breezy as my build system and libXrender is installed by both checking the dirs and according to adept.  Does anyone know how I can get the linker to see Xrender?  BTW libX11-dev package has also been installed using adept.
Thanks,
Chris

---

### Post by hod139 on 2006-02-18
/lib and /usr/lib should be in the default search path.  /usr/X11R6/lib is not in the default search path.

Adept should have run the ldconfig command (updates the list of available libraries to LD) after installing the libraries, but maybe it didn't.  You can run it manually though:
```
 sudo ldconfig
```

You can add search paths to the dynamic linker by editing /etc/ld.so.conf and adding the additional directories to search.  For example, if you wanted to add /usr/X11R6/lib
```

sudo gedit /etc/ld.so.conf

```
 Add ```
/usr/X11R6/lib
```.  Save and exit gedit. Next run
```
 sudo ldconfig
```


If this doesn't help, could you paste the error message from g++.

---

### Post by jackrabbit123 on 2006-02-19
The error message says:
```
can't find -lXrender
```
and then displays the make error messages.
I tried running ```
ldconfig -v | grep Xrender
``` and that shows that its loading the .so and I also tried explicitly putting /usr/lib as an '-L' option.
Any other ideas?
Chris

---

### Post by hod139 on 2006-02-19
The command you wanted to run was:
```

ldconfig -p | grep Xrender

```

>  and then displays the make error messages.
Can you paste this error message.

Are the permissions on /usr/lib/libXrender.so.1 set up correctly, can a normal user read?

---

### Post by hod139 on 2006-02-21
Got it.  Install the libxrender-dev package.
```
sudo apt-get install libxrender-dev
```

I'm guessing you don't have a /usr/lib/libXrender.so file, only /usr/lib/libXrender.so.* where * is a a version number.  To link against shared objects you need the plain .so file.

Sorry I didn't think of that first.

---

### Post by jackrabbit123 on 2006-02-25
That did it.  Thanks.

---

