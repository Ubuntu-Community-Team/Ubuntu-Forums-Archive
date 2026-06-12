---
title: "Bash shell scripting and for loops"
date: 2005-09-26
forum: Programming Talk
---

### Post by xaque on 2005-09-26
I'm trying to write a shell script that detects all USB drives currently attached to the computer and notifies you of where they are mounted. I have this much so far:

```
DISKS_FOUND=`df | awk '/\/dev\/sd/ {print $1 " " $6}'`
```

I then wanted to have a loop of some sort that would parse $DISKS_FOUND and output something like "$I is mounted at $M", where $I would be /dev/sd?, and $M would be it's mount point. Does anyone know how to do this, or possibly a better way of doing it entirely?

Thanks in advance.
Xaque

---

### Post by bkasterm on 2005-09-26
j=0; for i in `df | awk '/\/dev\/hda/ {print $1 " " $6}'`; do if test $j -eq 0 ; then first=$i; j=1 ; else echo $first mounted on $i; j=0; fi ; done

is a way to do this (note used hda in stead of sd, as I don't have any usb drives mounted to test).

Best,
Bart

---

### Post by jerome bettis on 2005-09-26
that's very nice but you can type "mount" to see pretty much the same information.  maybe you could write a simpler script to format the output of that command to your liking.

---

### Post by majikstreet on 2005-09-26
[QUOTE=bkasterm]j=0; for i in `df | awk '/\/dev\/hda/ {print $1 " " $6}'`; do if test $j -eq 0 ; then first=$i; j=1 ; else echo $first mounted on $i; j=0; fi ; done

is a way to do this (note used hda in stead of sd, as I don't have any usb drives mounted to test).

Best,
Bart[/QUOTE]

Btw, on my system my usb drives are on /dev/sdXX
just thought that may help..

---

### Post by xaque on 2005-09-27
[QUOTE=jerome bettis]that's very nice but you can type "mount" to see pretty much the same information.  maybe you could write a simpler script to format the output of that command to your liking.[/QUOTE]

no, I actually need to have the data sorted into those variables for use later in the script (it also copies some files to the drives). the "foo is mounted at bar" message is just for debugging purposes. bkasterm, your code worked well, thanks for the help. now, if I could just figure out why it doesn't work the same way on a mac...

---

### Post by NixMonk on 2005-09-30
Is this what your looking for?

`df | grep /dev/[hs]d | awk '{print$1" is mounted at "$6}'`

---

