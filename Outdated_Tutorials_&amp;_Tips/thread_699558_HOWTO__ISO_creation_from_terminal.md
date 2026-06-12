---
title: "HOWTO:  ISO creation from terminal"
date: 2008-02-17
forum: Outdated Tutorials &amp; Tips
---

### Post by Martje_001 on 2008-02-17
Hi,
I was looking for this (for a BASH script I wanted to write), and I found out how to do it. Now I want to share it ;)

**1.** Create ISO-file from folder
```
mkisofs -r -o /isofile.iso /folder
```
where */isofile.iso* is the relative or absolute path to the iso-file you want to create and */folder* the absolute or relative path to the folder you want to backup.

**2.** Create ISO-file from file(s)
```
mkisofs -r -o /isofile.iso /mybigfile
```

or if you want to backup multipi files (like you .mp3 collection):
```
mkisofs -r -o /isofile.iso *.mp3
```

**3.** Create ISO-file from a cd/dvd-drive
```
dd if=/dev/cdrom0 of=isofile.iso
```
where */dev/cdrom0* is your cd/dvd-drive and *isofile.iso* your iso-file you want to create.

*Note: An absolute path is like '/home/yn/myfile.iso', a relative path is like 'myfile.iso'*

---

### Post by Goll on 2008-12-25
Thanks very much for this.
If I could- I would press the thank you button, but I'm not seeing one. :)

Thanks to you!

---

### Post by Martje_001 on 2008-12-25
February 17th, 2008, the button wasn't there yet :P

---

### Post by oookkkooo on 2009-08-01
Still no button so thank you :-)

---

### Post by binbash on 2009-08-01
Thanks, simple but useful one.

---

### Post by boopathisivakumar on 2011-05-10
thank you lot ...

---

### Post by geazzy on 2011-05-10
nice tutorial :)

---

