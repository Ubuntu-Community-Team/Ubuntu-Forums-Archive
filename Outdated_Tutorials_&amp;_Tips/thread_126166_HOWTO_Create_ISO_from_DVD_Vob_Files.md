---
title: "HOWTO: Create ISO from DVD Vob Files"
date: 2006-02-05
forum: Outdated Tutorials &amp; Tips
---

### Post by kverde on 2006-02-05
How to make a dvd iso from a /directory/ with VIDEO_TS and AUDIO_TS directories:

mkisofs -dvd-video -udf -o dvd.iso /directory/

All filesnames must be in capital letters.  If you are using FAT32, you need to add shortname=mixed to the filesystem.

---

### Post by krusbjorn on 2006-02-07
Thanks a lot, I needed this.

---

### Post by rado_london on 2006-02-08
It gives me that error:
```
rado@linux:~$ mkisofs -dvd-video -udf -o dvd.iso /media/cdrom/
INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.
mkisofs: Unable to make a DVD-Video image.
```

How can I avoid this?

---

### Post by fletch331360 on 2006-02-11
i get the same error. anyone know how to fix this?
> 
rado@linux:~$ mkisofs -dvd-video -udf -o dvd.iso /media/cdrom/
INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.
mkisofs: Unable to make a DVD-Video image.

thanks

---

### Post by terry98 on 2006-02-11
i think that error is because you're trying to make the dvd iso in a read-only directory (/media/), try moving the directtory containing the VIDEO_TS and AUDIO_TS to a folder writable, like /home/"your user"/

---

### Post by johnswb on 2008-10-19
one word -- AWESOME!

---

### Post by naknak987 on 2008-10-26
I get this error. 

```
naknak987@naknak987-desktop:~/Desktop$ mkisofs -dvd-video -udf -o dvd.iso /dvd/
I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: No such file or directory. Invalid node - '/dvd/'.

```

I would very much like this to work, and now I feel like I'm just a step away. :(

EDIT: I'm a dork. I figured it out, This worked for me. mkisofs -dvd-video -udf -o dvd.iso /home/naknak987/Desktop/dvd/

---

### Post by jameshoo on 2008-11-15
:popcorn: Now I can watch Bob Marley!!!
:) Thanks  you

---

### Post by fballem on 2008-11-15
thanks!

---

### Post by binbash on 2008-12-02
Thanks, i was looking for this command

---

### Post by st4rk3 on 2009-01-29
Can anyone help me with this,

I want to make the dvd form in the same folder it came from, it is sending it to my home folder but there isn't enough space for it.... its a dvd9. Anyhelp would be appreciated.

---

### Post by pumpkins2go on 2011-05-21
For a GUI method you could use Shrinkta, AKA DVD Movie Backup. It's there in the Ubuntu software center.

Set it to open a file instead of a DVD disc, browse for the folder containing VIDEO_TS and AUDIO_TS, click "open". Then on the next screen click "backup". It will produce an .iso image of the files. This must then be burnt as an image (NOT a data DVD). Nearly all burning apps. are able to do this.

---

### Post by pumpkins2go on 2011-05-21
sorry, posted above again by mistake

---

