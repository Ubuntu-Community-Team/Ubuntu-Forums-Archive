---
title: "Problem compiling ioDOOM 3"
date: 2012-05-09
forum: Packaging and Compiling Programs
---

### Post by willbe1kenobi on 2012-05-09
I'm not 100% sure that this is the right forum to post in but I am having some trouble compiling the ioDoom 3 source on my 12.04 64 bit Ubuntu.

I have followed all the steps to obtain the code [[COLOR="DeepSkyBlue"][COLOR="RoyalBlue"]here[/COLOR][/COLOR]]("http://wiki.iodoom3.org/Downloading_and_Compiling_under_Linux") but here are the last 6 lines of info the terminal gave me:

/usr/bin/ld: cannot find -lX11
/usr/bin/ld: cannot find -lXext
/usr/bin/ld: cannot find -lXxf86vm
collect2: ld returned 1 exit status
scons: *** [build/debug/core/sys/scons/doom] Error 1
scons: building terminated because of errors.

If some1 could please tell me how I can fix this then i'd be very grateful

---

### Post by kingtaurus on 2012-05-16
> **willbe1kenobi said:**
> I'm not 100% sure that this is the right forum to post in but I am having some trouble compiling the ioDoom 3 source on my 12.04 64 bit Ubuntu.

I have followed all the steps to obtain the code [[COLOR="DeepSkyBlue"][COLOR="RoyalBlue"]here[/COLOR][/COLOR]]("http://wiki.iodoom3.org/Downloading_and_Compiling_under_Linux") but here are the last 6 lines of info the terminal gave me:

/usr/bin/ld: cannot find -lX11
/usr/bin/ld: cannot find -lXext
/usr/bin/ld: cannot find -lXxf86vm
collect2: ld returned 1 exit status
scons: *** [build/debug/core/sys/scons/doom] Error 1
scons: building terminated because of errors.

If some1 could please tell me how I can fix this then i'd be very grateful

The problem that you are getting is one most likely the libraries libX11, libXext, and libXxf86vm are not installed. However the other possibility is that the libraries are in a location that is not expected (i.e. in Ubuntu these libraries are commonly installed in /usr/lib/<arch_dependent_directory>, for example: i386-linux-gnu or x86_64-linux-gnu)

First, please check that the following packages are installed:
```

libx11-dev
libxext-dev
libxxf86vm-dev

```

to guarantee that the packages are installed (it appears that in a 64 bit environment, you may require the 32 bit libraries, libx11-dev:i386 libxext-dev:i386 libxxf86vm-dev:i386):
```

sudo aptitude install libx11-dev libxext-dev libxxf86vm-dev

```

I'm reviewing the build instructions to see if there are overrides that allow for searching in additional paths for these libraries.

Cheers

---

### Post by kingtaurus on 2012-05-16
So I investigated further. You'll have to edit (from within the doom root folder):
```

neo/sys/scons/SConscript.core

```
and change the following:
```

if ( local_dedicated == 0 ):
	local_env.Append( LIBS = [ 'X11', 'Xext', 'Xxf86vm' ] ) # 'Xxf86dga', 
	local_env.Append( LIBPATH = [ '/usr/lib' ] )

```
to
```

if ( local_dedicated == 0 ):
	local_env.Append( LIBS = [ 'X11', 'Xext', 'Xxf86vm' ] ) # 'Xxf86dga', 
	local_env.Append( LIBPATH = [ '/usr/lib', '/usr/lib/i386-linux-gnu' ] )

```

This should direct scons to look at the correct location for the libraries (note: the build is currently incompatible with x86_64 bit libraries).

Cheers

---

### Post by willbe1kenobi on 2012-05-16
> **kingtaurus said:**
> The problem that you are getting is one most likely the libraries libX11, libXext, and libXxf86vm are not installed. However the other possibility is that the libraries are in a location that is not expected (i.e. in Ubuntu these libraries are commonly installed in /usr/lib/<arch_dependent_directory>, for example: i386-linux-gnu or x86_64-linux-gnu)

First, please check that the following packages are installed:
```

libx11-dev
libxext-dev
libxxf86vm-dev

```

to guarantee that the packages are installed (it appears that in a 64 bit environment, you may require the 32 bit libraries, libx11-dev:i386 libxext-dev:i386 libxxf86vm-dev:i386):
```

sudo aptitude install libx11-dev libxext-dev libxxf86vm-dev

```

I'm reviewing the build instructions to see if there are overrides that allow for searching in additional paths for these libraries.

Cheers


> **kingtaurus said:**
> So I investigated further. You'll have to edit (from within the doom root folder):
```

neo/sys/scons/SConscript.core

```
and change the following:
```

if ( local_dedicated == 0 ):
	local_env.Append( LIBS = [ 'X11', 'Xext', 'Xxf86vm' ] ) # 'Xxf86dga', 
	local_env.Append( LIBPATH = [ '/usr/lib' ] )

```
to
```

if ( local_dedicated == 0 ):
	local_env.Append( LIBS = [ 'X11', 'Xext', 'Xxf86vm' ] ) # 'Xxf86dga', 
	local_env.Append( LIBPATH = [ '/usr/lib', '/usr/lib/i386-linux-gnu' ] )

```

This should direct scons to look at the correct location for the libraries (note: the build is currently incompatible with x86_64 bit libraries).

Cheers

Thanks for your assistance in this matter however I have found a way to compile the source without modifying the Sconscipt.core file you mentioned.

All I had to do was just install the 32 bit version of the libraries by typing 'sudo apt-get install libx11-dev:i386 libxext-dev:i386 libxxf86vm-dev:i386 and that worked.

---

