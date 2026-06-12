---
title: "dynamic link loader"
date: 2006-11-27
forum: Programming Talk
---

### Post by DoorGunner on 2006-11-27
Hi

I was compiling snort using this code 
./configure --enable-dynamicplugin --with-mysql
and ended up with this error.
> 
checking for mysql... yes
checking for compress in -lz... yes
checking for dlsym in -ldl... no
checking for dlsym in -lc... no

   ERROR!  programmatic interface to dynamic link loader
   not found.  Cannot use dynamic plugin libraries.


I checked the cvs and this is the coding for this error
> 
AC_ARG_ENABLE(dynamicplugin,
[  --enable-dynamicplugin   Enable Ability to dynamically load preprocessors, detection engine, and rules lib (on by default, use --disable to not use dynamic libraries)],
                use_dynamic="$enableval", use_dynamic=yes)
AM_CONDITIONAL(HAVE_DYNAMIC_PLUGINS, test x$use_dynamic = xyes)
if test x$use_dynamic = xyes; then
    CFLAGS="$CFLAGS -DDYNAMIC_PLUGIN"
    AC_CHECK_LIB(dl, dlsym,, DLLIB="no")
    if test "$DLLIB" != "no"; then
        LIBS="$LIBS -ldl"
    else
        AC_CHECK_LIB(c, dlsym,, DLCLIB="no")
        if test "$DLCLIB" = "no"; then
           echo
           echo "   ERROR!  programmatic interface to dynamic link loader"
           echo "   not found.  Cannot use dynamic plugin libraries."
           echo
           exit 1
        fi
    fi
fi


I also tried to compile with --disable-dynamicplugin
I was able to finish the compile. However, later i did require the plugin in order to access snortrules

What is the dlsym? Where would i find one to use for the compile process? or any suggestion would be helpful.

---

### Post by drphilngood on 2006-11-27
See [here]("http://linux.about.com/library/cmd/blcmdl3_dlsym.htm").

---

### Post by hod139 on 2006-11-27
make sure you have the package build-essential installed, which should install libdl for you.

---

### Post by DoorGunner on 2006-11-28
I reloaded build-essential and did a locate libdl with this return


$locate libdl
/lib/tls/i686/cmov/libdl-2.4.so
/lib/tls/i686/cmov/libdl.so.2
/lib/libdl-2.4.so
/lib/libdl.so.2
/usr/lib/libdl.a
/usr/lib/libdl.so

unfortunately I am still getting the same error. I wonder if it is looking in a the wrong place? maybe i need to copy and file? but were too?

---

### Post by hod139 on 2006-11-28
I'm confused then.  You clearly have libdl, which provides the dynamic loading capabilities.  Just for a test, can you edit configure.ac and change 
```
      AC_CHECK_LIB(dl, dlsym,, DLLIB="no")
```
to 
```
      AC_CHECK_LIB(dl, dlopen,, DLLIB="no")
```  Maybe dlsym is too difficult for automake?

Otherwise, I'm out of ideas.  Are you sure that's the line causing the error?

---

### Post by DoorGunner on 2006-11-28
as you suggested i replaced dlsym with dlopen in the configure.in file. Unfortunately didnt work either. Same error.



--------------------------------
[http://www.howtoforge.com/intrusion_detection_base_snort?](http://www.howtoforge.com/intrusion_detection_base_snort?)
is where i got my orirional instructions for snort. It is based on a fresh load of mysql snort base pcre libpcap. I have all installed at this time. Mysql was origionally loaded with apt-get and has data on it. The only problem here was the repository didnt leave a mysql.h file. SO i went and got one from the mysql. Every thing worked fine until the problem you and I are working on.

I did do a search on the -ldl from the first two lines of my error report. It shows some sparatic locations such as gallery2, printers and /usr/share/hplip/data/ldl so it seems to be here too. 

I did get it to compile with out the dynamicloaders however as i mentioned the snortrules wont work with out it. (my screen is there for base but no data associated with it.
------------------------------------------

maybe your right that automake cant hanle the ldl for some reason. Is there another program rather than automake to try? 

Other than that I may have to put snort aside for a while.

---

### Post by hod139 on 2006-11-28
To be clear, I know automake can handle libdl, I have used it in a project before, just using the dlopen function, instead of dlsym.

I'm not sure why it isn't working for you though.  You can remove the check and see if it still compiles.  Change
```

    AC_CHECK_LIB(dl, dlsym,, DLLIB="no")
    if test "$DLLIB" != "no"; then
        LIBS="$LIBS -ldl"
    else
        AC_CHECK_LIB(c, dlsym,, DLCLIB="no")
        if test "$DLCLIB" = "no"; then
           echo
           echo "   ERROR!  programmatic interface to dynamic link loader"
           echo "   not found.  Cannot use dynamic plugin libraries."
           echo
           exit 1

```
to 
```

        LIBS="$LIBS -ldl"

```
and see what happens.

---

### Post by DoorGunner on 2006-11-28
still no joy. I did find another reference and tried this. 

nm `locate libdl` | grep dlsym 
nm: /lib/tls/i686/cmov/libdl-2.4.so: no symbols
nm: /lib/tls/i686/cmov/libdl.so.2: no symbols
nm: /lib/libdl-2.4.so: no symbols
nm: /lib/libdl.so.2: no symbols
nm: /usr/lib/libdl.so: no symbols
dlsym.o:
00000000 T dlsym
         U __dlsym

Does this mean that I have no symbol dlsym in my library?

---

### Post by hod139 on 2006-11-28
```
objdump -T /usr/lib/libdl.so | grep dlsym
```

---

### Post by DoorGunner on 2006-11-28
objdump -T /usr/lib/libdl.so | grep dlsym
00000f00 g    DF .text  00000096  GLIBC_2.0   dlsym

---

### Post by hod139 on 2006-11-29
> **DoorGunner said:**
> objdump -T /usr/lib/libdl.so | grep dlsym
00000f00 g    DF .text  00000096  GLIBC_2.0   dlsym
So you do have the symbol.  I'm fresh out of ideas though.  I'm not sure why it isn't working.

---

### Post by DoorGunner on 2006-11-29
Thank you for your help

---

