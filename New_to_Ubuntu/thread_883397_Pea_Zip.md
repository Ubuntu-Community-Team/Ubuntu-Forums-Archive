---
title: "Pea Zip"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by at2smithjason on 2008-08-07
The other day i downloaded PeaZip from Sourceforge and I got it all installed.  But I dont know how it works.  Can I just download a .rar file as I would have when I used Winblows and it will work like that, or will i need to use command line prompts?  If I need cmd line prompts can someone please show me how to extract the files to my desktop.  Also are there places where I can go to "personalize" my desktop?

---

### Post by iaculallad on 2008-08-07
PeaZip once installed is located on Applications->System Tools->PeaZip. It has a GUI interface.

---

### Post by at2smithjason on 2008-08-08
I have tried to open it like that, and it wont open.  Can I still do it from the command line, or just open up the rar file?

---

### Post by iaculallad on 2008-08-08
> **at2smithjason said:**
> I have tried to open it like that, and it wont open.  Can I still do it from the command line, or just open up the rar file?

You could execute peazip in your terminal:

```
peazip
```

Or to check in peazip application exist, do:

```
which peazip
```

---

### Post by at2smithjason on 2008-08-08
> **iaculallad said:**
> You could execute peazip in your terminal:

```
peazip
```

Or to check in peazip application exist, do:

```
which peazip
```

```
jason@jason-laptop:~$ peazip
peazip: error while loading shared libraries: libglib-1.2.so.0: cannot open shared object file: No such file or directory
jason@jason-laptop:~$ 
jason@jason-laptop:~$ 
```

Thats what I get.  Maybe I installed the wrong copy of it?

---

### Post by iaculallad on 2008-08-08
Try uninstalling your current peazip and download the deb file in this [location]("http://downloads.sourceforge.net/peazip/peazip_2.1.bin.LINUX.GTK2.i586-1.deb").

---

### Post by at2smithjason on 2008-08-08
Thanks, its working now.

---

