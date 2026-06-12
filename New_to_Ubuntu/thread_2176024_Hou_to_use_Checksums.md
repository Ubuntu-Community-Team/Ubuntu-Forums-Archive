---
title: "Hou to use Checksums?"
date: 2013-09-22
forum: New to Ubuntu
---

### Post by suomalainen on 2013-09-22
Ubunteros,

I found on:

[http://www.wilderssecurity.com/showthread.php?t=323210](http://www.wilderssecurity.com/showthread.php?t=323210)

A non pae Ubuntu 12.04 iso

There are apparently Checksums associated with it... eg:

md5sum:
e857a7ccde6d6a85b2080d285ee48023 ubuntu-12.04-desktop-i386-nonpae.iso
sha256sum:
047ca71b469a23dce844ba1571a6eae4c64e7e24527449f94d0fb6402676ced1 ubuntu-12.04-desktop-i386-nonpae.iso

But I don't know how to use them.

Would someone mind teaching me?

Thanks,

Suomalainen

---

### Post by VMC on 2013-09-22
From a terminal type md5sum <file>.iso. Example:
```
md5sum gnome-saucy-desktop-amd64.iso
```

edit: ```
 md5sum --help **or**  man md5sum
```

---

### Post by suomalainen on 2013-09-22
Thanks for the terminal commands which yielded

:~/Desktop$ md5sum  ubuntu-12.04-desktop-i386-nonpae.iso
e857a7ccde6d6a85b2080d285ee48023  ubuntu-12.04-desktop-i386-nonpae.iso

To me it looks like two additional lines from the checksum are missing? Or am I missing something?

Thanks

---

### Post by Bashing-om on 2013-09-22
md5sum:
e857a7ccde6d6a85b2080d285ee48023 ubuntu-12.04-desktop-i386-nonpae.iso <-source documentation
e857a7ccde6d6a85b2080d285ee48023 ubuntu-12.04-desktop-i386-nonpae.iso <- command output

Thus the .iso file "ubuntu-12.04-desktop-i386-nonpae.iso" is validated in that it is unchanged on your download as to what is original at the  
source.

sha256sum:
From the manual:
> 
 compute and check SHA256 message digest
DESCRIPTION
       Print  or  check SHA256 (256-bit) checksums.  With no FILE, or when FILE is -,
       read standard input

See:
[https://help.ubuntu.com/community/HowToSHA256SUM](https://help.ubuntu.com/community/HowToSHA256SUM)

different from md5sum check .

[INDENT][INDENT]many paths to an end
[/INDENT][/INDENT]

---

### Post by suomalainen on 2013-09-22
Thanks everyone for the help and clarification on this. Much appreciated!

---

