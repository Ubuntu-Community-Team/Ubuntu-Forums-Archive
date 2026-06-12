---
title: "Erase RW CD"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by Johnathannn on 2008-06-29
Is there anyway I can erase a RW CD when there's stuff already on it (in Ubuntu 8.04)?

---

### Post by Joeb454 on 2008-06-29
I think Brasero can do this. Usually when you try and write more stuff to it, it will prompt you to either insert a new disc or erase the current disc :)

---

### Post by spiderbatdad on 2008-06-29
```
cdrecord dev=/dev/cdrom blank=fast

```

---

### Post by Johnathannn on 2008-06-29
That command didn't work (it said the SPCI Driver coulnd't be detected or something) and I don't want to use Brasero lol...any other options!? :)

---

### Post by Johnathannn on 2008-06-29
So when I type in that command, I get this...

johnathannn@Johnathannn-lappyyy:~$ cdrecord dev=/dev/cdrom blank=fast
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.Error trying to open /dev/cdrom exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrom exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrom exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrom exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrom exclusively (Device or resource busy)... giving up.
wodim: Device or resource busy. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.

---

### Post by sonofusion82 on 2008-06-29
you will need to unmount the device first.
try:

umount /dev/cdrom

then try the cdrecord command again

---

### Post by Johnathannn on 2008-06-29
I know how to Unmount the CD without using the Terminal, but is there anyway to use the command said earlier without the Terminal (in a GUI of some sort)? BY THE WAY, the last comment worked perfectly before using the other command said earlier, THANKS!

---

### Post by Johnathannn on 2008-06-29
So basically, can I perform this action "umount /dev/cdrom" without typing it in the terminal?

---

### Post by sonofusion82 on 2008-06-30
in KDE/Kubuntu, I can just right click ->Safely Remove on the CD icon in /media
but I am not sure about Gnome/Ubuntu..

---

### Post by cariboo on 2008-06-30
I know you said you did want to use Brasero, but it is pretty easy to do it, just click Tools-->Erase, or if you've got K3b or Gnomebaker installed, it is the same command.

Jim

---

### Post by hyper_ch on 2008-06-30
there was a few times where I had problems deleting a rw with k3b/brasero... gnomebreaker however did it... so you might want to try that.

---

