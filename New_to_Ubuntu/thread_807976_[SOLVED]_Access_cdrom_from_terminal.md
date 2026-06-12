---
title: "[SOLVED] Access cdrom from terminal"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by Kevbert on 2008-05-26
This is probably easy... How do I access a cdrom using terminal ?

---

### Post by Chr0mis on 2008-05-26
Cd to the media directory: 
cd /media/
list the dirs: 
ls
go to the cdrom dir: 
cd cdrom


Of just go to the cdrom dir straight away: 
cd /media/cdrom 


:)

---

### Post by mbarak on 2008-05-26
if the CD is already mounted, just change to the cd directory:
```
cd /media/cdrom#
```
where # is a number starting at 0 depending on which CD-drive you are using
(ex: the first drive is 0, the 2nd is 1 etc)

if the cd isn't mounted do this:
```
mount /media/cdrom#
```
and then change to the cd-rom directory using the command above

*another way to access the first cdrom (or the only one) you can use this directory instead:
/media/cdrom
its the same as
/media/cdrom0

---

### Post by Kevbert on 2008-05-26
Now thats what I thought...
I've got a Duke Nukem cdrom.  I put the CD in the drive and Sound Juicer comes up (which is set to default for music CDs).  I select ignore and close Sound Juicer.  I can't use Nautilus as it sees the CD as a music CD.  If I use terminal I go to the Media folder and cdrom is displayed in light blue and cdrom0 is dark blue.  If I select either directory and then list the files with 'ls' nothing is displayed...

---

### Post by mbarak on 2008-05-26
/media/cdrom and /media/cdrom0 are the same things
try to mount the cdrom before seeing its contents
```
mount /media/cdrom
```

mounting the cd makes the contents accessible to the system by making it a part of the filesystem (i.e. a directory under / ) so all programs see what's there as if it was just another directory

---

### Post by Kevbert on 2008-05-27
> **mbarak said:**
> /media/cdrom and /media/cdrom0 are the same things
try to mount the cdrom before seeing its contents
```
mount /media/cdrom
```

mounting the cd makes the contents accessible to the system by making it a part of the filesystem (i.e. a directory under / ) so all programs see what's there as if it was just another directory

Thanks.  I was under the impression that as soon as you get the cdrom icon on the desktop you could view the contents of the CD.  The disk label (Atomic15) is displayed.  If thats correct then surely this is a bug ?  It doesn't seem to work the same as a floppy disk (for example).  Mounting the CD via terminal works, so thanks again.

---

### Post by Phillip138 on 2013-02-02
Similar question: how would you access a usb from the terminal?

---

### Post by Impavidus on 2013-02-03
In exactly the same way: /media/some_identifier. This identifier is the label of the usb drive.

---

### Post by oldos2er on 2013-02-03
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

