---
title: "Cannot compile"
date: 2006-08-10
forum: Programming Talk
---

### Post by albinoloverats on 2006-08-10
I seem to be unable to compile anything in Anjuta, which uses a GTK interface.  Even when I first try to create a new project I get the following error:

```
checking for PACKAGE... configure: error: Package requirements (gtk+-2.0 gdk-2.0) were not met:

Package glitz was not found in the pkg-config search path.
Perhaps you should add the directory containing `glitz.pc'
to the PKG_CONFIG_PATH environment variable
Package 'glitz', required by 'cairo', not found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
``` 

I've tried installing various dev packages which relate to GTK/GDK but I still cannot get it to work.

Thanks.

---

### Post by Paerez on 2006-08-10
try installing these two:
```
sudo apt-get install libglitz-glx1-dev libglitz1-dev
```

---

### Post by albinoloverats on 2006-08-11
I just tried that and this is what happened: ](*,)

```
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libglitz1-dev: Depends: xlibmesa-gl-dev but it is not installableor
                          libgl-dev
E: Broken packages

```

---

### Post by Paerez on 2006-08-12
you probably have to add the compiz repositories in order to get those libraries. Try adding them and then trying the command I gave you again.

---

