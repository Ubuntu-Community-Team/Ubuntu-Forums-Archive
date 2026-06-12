---
title: "libjpeg error"
date: 2008-12-28
forum: Packaging and Compiling Programs
---

### Post by garethrichardadams on 2008-12-28
Hi,

When compiling a program I get the following error:

checking for libjpeg... no
configure: WARNING: libjpeg not found. disable JPEG support.

Any idea how I can rectify this?

Thanks

Gareth

---

### Post by albinootje on 2008-12-28
> **garethrichardadams said:**
> Hi,

When compiling a program I get the following error:

checking for libjpeg... no
configure: WARNING: libjpeg not found. disable JPEG support.


$ apt-cache search libjp|grep dev
libjpeg62-dev - Development files for the IJG JPEG library

Install that package and try again.

---

### Post by iharrold on 2008-12-29
You can also download the source code and compile/install it.

```
cd {TEMP DOWNLOAD DIR}
wget http://www.ijg.org/files/jpegsrc.v6b.tar.gz
```

{TEMP DOWNLOAD DIR} = a directory you have ownership of and can access... i.e. ~/Libraries

extract the file to the "~/Libraries/" directory.
```
tar -xvzf jpegsrc.v6b.tar.gz -C~/Libraries/
```

Now config the library and make it:

```
./configure --prefix=/usr/local
make
sudo make install-lib
```

Compiling from the source is very useful if you need to cross compile libraries for other architectures.

Also /usr/local/lib and /usr/lib are the default dynamic linked library search paths for the OS when an application is running.  So if "--prefix=" is set to a different location, then you will need to add it to the search path.

```
sudo gedit /etc/ld.so.conf
```

Add the path to the end of the file ld.so.conf[remember one blank line at the end of the file aswell.

Here is my ld.so.conf file for example:
```
include /etc/ld.so.conf.d/*.conf

/Libraries/IA32/lib


```

Then set it up
```
ldconfig
```

you may need to logoff/logon again... but I don't think you do.

Hope this helps!

---

