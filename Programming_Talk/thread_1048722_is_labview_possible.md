---
title: "is labview possible?"
date: 2009-01-23
forum: Programming Talk
---

### Post by octopusfinley on 2009-01-23
Hey there. I've just got a job with a professor, but I need to learn labview pretty quick. So I put in the linux install disk but file browser just comes up with a whole bunch of separated files instead of a concrete installation pathway. Anyway, is this a lost cause? is labview ever going to work with ubuntu (I've got 7.10), and if not, do I have any options in linux at all?
thanks everyone,
Finley

---

### Post by zooooz on 2010-05-06
**Labview works with ubuntu** ( tried it myself for 9.04 up to 10.04. All my experience is with version 7.1 of labview, though.)
There are .rpm packages supplied, that have to be converted to .deb ones with the alien command.
After that, install everything with this:
```
sudo dpkg -i *.deb
```

So far there are only 32bit binaries. Installing them on 10.04 amd64 worked perfectly with this one:
```
sudo dpkg -i --force-architecture *.deb
```

After the install labview will crash at the splash screen:
```
*** glibc detected *** /usr/local/lv71/labview: realloc(): invalid next size: 0x2c5cdfe8 ***

======= Backtrace: =========
/lib32/libc.so.6(+0x6c231)[0xf738c231]
...

```

this can be solved by getting the file spd_readdir.so from [https://wiki.edubuntu.org/LabVIEW]("https://wiki.edubuntu.org/LabVIEW") (too bad the free labview 6.1 registration mentioned there has been discontinued a while ago), saving it to /usr/local/lv71/ and starting labview with this command:
```

LD_PRELOAD=/usr/local/lv71/spd_readdir.so LD_LIBRARY_PATH=/usr/local/lv71/linux /usr/local/lv71/labview

```

I just wrote :
```
#!/bin/sh
LD_PRELOAD=/usr/local/lv71/spd_readdir.so LD_LIBRARY_PATH=/usr/local/lv71/linux /usr/local/lv71/labview
```

into /usr/local/bin/labview, made it executable and am very happy with the results.


(I am aware, that the original post is old, but keeping success stories to oneself doesn't make any sense at all. Maybe someone will profit from this after all.)

---

### Post by meng1usa on 2010-06-23
> **zooooz said:**
> **Labview works with ubuntu** ( tried it myself for 9.04 up to 10.04. All my experience is with version 7.1 of labview, though.)
There are .rpm packages supplied, that have to be converted to .deb ones with the alien command.
After that, install everything with this:
```
sudo dpkg -i *.deb
```

So far there are only 32bit binaries. Installing them on 10.04 amd64 worked perfectly with this one:
```
sudo dpkg -i --force-architecture *.deb
```

After the install labview will crash at the splash screen:
```
*** glibc detected *** /usr/local/lv71/labview: realloc(): invalid next size: 0x2c5cdfe8 ***

======= Backtrace: =========
/lib32/libc.so.6(+0x6c231)[0xf738c231]
...

```

this can be solved by getting the file spd_readdir.so from [https://wiki.edubuntu.org/LabVIEW]("https://wiki.edubuntu.org/LabVIEW") (too bad the free labview 6.1 registration mentioned there has been discontinued a while ago), saving it to /usr/local/lv71/ and starting labview with this command:
```

LD_PRELOAD=/usr/local/lv71/spd_readdir.so LD_LIBRARY_PATH=/usr/local/lv71/linux /usr/local/lv71/labview

```

I just wrote :
```
#!/bin/sh
LD_PRELOAD=/usr/local/lv71/spd_readdir.so LD_LIBRARY_PATH=/usr/local/lv71/linux /usr/local/lv71/labview
```

into /usr/local/bin/labview, made it executable and am very happy with the results.


(I am aware, that the original post is old, but keeping success stories to oneself doesn't make any sense at all. Maybe someone will profit from this after all.)
you are right. it is a great reference for me!
thx a lot!

---

### Post by tommpogg on 2011-07-07
It worked for me!!

Bt since I am running Ubuntu on a 64-bit PC, I had to convert the rpm packages to deb in this way:
```

sudo alien -k --scripts --to-tgz *.rpm
sudo alien -k --scripts *.tgz

```Indeed, it seems that alien cannot directly convert rpm packages built for 32-bit PC

---

