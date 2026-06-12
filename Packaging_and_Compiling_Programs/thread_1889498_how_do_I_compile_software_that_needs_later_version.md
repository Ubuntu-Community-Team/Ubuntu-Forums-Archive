---
title: "how do I compile software that needs later versions of libraries"
date: 2011-12-01
forum: Packaging and Compiling Programs
---

### Post by tanndo on 2011-12-01
Hi,

I'm trying to build the latest version of gnumeric from source on an ubuntu 10.04 box. Need latest stable version and can't find a ppa.

Got stuck at the ./configure stage

Did
  sudo apt-get build-dep gnumeric

and configure got a bit further. 

See full output below but basically looks like it wants later versions of the libraries I have installed.

Is there any way round this ?
```

configure: error: Package requirements (
	libgoffice-0.8	>= 0.8.15
	libgsf-1		>= 1.14.18
	libxml-2.0		>= 2.4.12
 
	gtk+-2.0		>= 2.12.0
) were not met:

Requested 'libgoffice-0.8 >= 0.8.15' but version of libGOffice is 0.8.1
Requested 'libgsf-1 >= 1.14.18' but version of libgsf-1 is 1.14.16

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBSPREADSHEET_CFLAGS
and LIBSPREADSHEET_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


```
Thanks t

---

### Post by oldos2er on 2011-12-01
Moved to Packaging and Compiling Programs.

---

### Post by Bachstelze on 2011-12-01
If you are lucky, those libraries are not needed by other packages you have, so you can 1) uninstall the packages for those libraries, and 2) compile them from source manually. Then you will be able to compile your package.

If you are not lucky, then you can either upgrade to Oneiric, or switch distros altogether. Other methods that are not guaranteed to work are to just install those two packages from Oneiric, or rebuild your Lucid packages from the updated source code.

---

### Post by tanndo on 2011-12-03
Hi,

thanks but I'm not sure what you mean.
Taking 
    libgoffice-0.8 
as an example, how would I know if it is needed by other packages.

How do I know which package libgoffice-0.8 is in so I can uninstall.

And where would I get the latest sources ?

I like the idea of installing from Oneiric, or rebuild your Lucid packages from the updated source code but how would I go about this.

What about just finding source for libgoffice, building it, e.g. in my home directory, i.e. not "installing" system wide then link the lib  (static or dynamic?) with gnumeric (e.g. tweaking makefile manually) ?

I just want to follow best practice and not screw my 10.04 system up :)
Thanks
T

---

### Post by Bachstelze on 2011-12-03
> **tanndo said:**
> 
thanks but I'm not sure what you mean.
Taking 
    libgoffice-0.8 
as an example, how would I know if it is needed by other packages.

Try uninstalling it and see if Apt wants to uninstall other packages.

> How do I know which package libgoffice-0.8 is in so I can uninstall.

One way is

```
dpkg -l | grep libgoffice
```

which will display all the packages you have installed that have libgoffice in their names.

> And where would I get the latest sources ?

[ftp://ftp.gnome.org/pub/gnome/sources/goffice/0.8/](ftp://ftp.gnome.org/pub/gnome/sources/goffice/0.8/)

> I like the idea of installing from Oneiric, or rebuild your Lucid packages from the updated source code but how would I go about this.

To get the Oneiric binary packages, go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/). To build a binary package on Lucid you would get the source package from Oneiric with

```
pull-lp-source goffice oneiric
```

And then build it on your Lucid system wth e.g. debuild.

> What about just finding source for libgoffice, building it, e.g. in my home directory, i.e. not "installing" system wide then link the lib  (static or dynamic?) with gnumeric (e.g. tweaking makefile manually) ?

More complicated...

---

### Post by tanndo on 2011-12-05
Thanks for the detailed reply,

I'm hacking some python at the moment but hopefully will have another
go at compiling gnumeric at the weekend

Thanks
T

---

