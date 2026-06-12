---
title: "php error: php5-gd undefined symbol: gdFontCacheShutdown"
date: 2011-01-25
forum: Packaging and Compiling Programs
---

### Post by flibitboat on 2011-01-25
Hello everyone,

So I am having this problem and have been having it for weeks, trying to ask almighty google if it can help me with this problem but I just cant seem to figure it out :(  I am starting to run out of ideas as to what to try.  First of all here is the error:

[INDENT]PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626/gd.so' - /usr/lib/php5/20090626/gd.so: undefined symbol: gdFontCacheShutdown in Unknown on line 0[/INDENT]

I am trying to build a barcode creator using php and I need gd to draw the barcode.  I have tried uninstalling php but to no avail :(  I have no Idea what gdFontCacheShutdown is or why it is needed but if anyone could help me I would really appreciate it :) thanks!!

---

### Post by anglican on 2011-01-31
> **flibitboat said:**
> Hello everyone,

So I am having this problem and have been having it for weeks, trying to ask almighty google if it can help me with this problem but I just cant seem to figure it out :(  I am starting to run out of ideas as to what to try.  First of all here is the error:

[INDENT]PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626/gd.so' - /usr/lib/php5/20090626/gd.so: undefined symbol: gdFontCacheShutdown in Unknown on line 0[/INDENT]

I am trying to build a barcode creator using php and I need gd to draw the barcode.  I have tried uninstalling php but to no avail :(  I have no Idea what gdFontCacheShutdown is or why it is needed but if anyone could help me I would really appreciate it :) thanks!!What does ```
dpkg -L php5-gd
``` show?

H

---

### Post by c4am95 on 2011-07-28
i need to bump this. i'm getting the same error. i have php5-gd, i have the gd libraries, but still php has an issue loading that gd module. i get the same undefined symbol error. any ideas?

---

### Post by c4am95 on 2011-07-28
oh, and when i run dpkg, i get the following output:


/.
/usr
/usr/lib
/usr/lib/php5
/usr/lib/php5/20090626+lfs
/usr/lib/php5/20090626+lfs/gd.so
/usr/share
/usr/share/doc
/etc
/etc/php5
/etc/php5/conf.d
/etc/php5/conf.d/gd.ini
/usr/share/doc/php5-gd

---

### Post by SevenMachines on 2011-07-29
Do you have libgd2-xpm installed?

```
$ dpkg -L libgd2-xpm | grep /usr/lib
/usr/lib
/usr/lib/libgd.so.2.0.0
/usr/lib/libgd.so.2

$ nm -D /usr/lib/libgd.so.2 | grep gdFontCacheShutdown
0000000000019160 T gdFontCacheShutdown
```

Should be but just a thought...

---

### Post by c4am95 on 2011-07-29
yup. installed and working. i get the same output, and other applications using libgd2 work just fine.

---

### Post by c4am95 on 2011-07-29
uh oh. i just checked the file in the php directory and there seems to be a problem.

```
nm -D /usr/lib/php5/20090626+lfs/gd.so | grep gdFontCacheShutdown
         U gdFontCacheShutdown

```

---

### Post by SevenMachines on 2011-07-29
Think thats fine ( i get it here ). The symbols in libgd. What version are you using, maybe a bug?

---

### Post by c4am95 on 2011-07-29
i have 2.0.36~rc1~dfsg-3.1ubuntu1 installed. maybe you're right about the bug. i wonder if i should try rolling it back? i don't know.

---

### Post by SevenMachines on 2011-07-29
Was just trying the lucid live cd ubuntu-10.04.3-desktop-amd64 and i still dont get any problem, not really sure whats going on...

---

### Post by c4am95 on 2011-07-29
ok i think i figured it out. for some reason there were copies of the libgd.so files in /usr/local/lib. when i removed those, the gd module loaded just fine. that's interesting.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=470483]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=470483")

---

### Post by SevenMachines on 2011-07-29
Yep that'll explain it, if i'd thought then it would show up in

```
$ ldd /usr/lib/php5/20090626/gd.so | grep gd
    libgd.so.2 => /usr/lib/libgd.so.2 (0x00007f2079f1a000)

```

---

