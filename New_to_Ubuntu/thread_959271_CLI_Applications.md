---
title: "CLI Applications"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by MrWES on 2008-10-26
OK...I've started exploring the power of CLI applications. I just spent the last few minutes playing around with abcde: A Better CD Extractor-- very powerful and pretty easy to use once I setup the abcde.conf file. Now I'm looking for some command line applications to rip dvd's and convert to avi. Any suggestions?

Thanks,
Bill

---

### Post by billgoldberg on 2008-10-26
> **MrWES said:**
> OK...I've started exploring the power of CLI applications. I just spent the last few minutes playing around with abcde: A Better CD Extractor-- very powerful and pretty easy to use once I setup the abcde.conf file. Now I'm looking for some command line applications to rip dvd's and convert to avi. Any suggestions?

Thanks,
Bill

mencoder, ffmpeg

---

### Post by neurostu on 2008-10-26
a great way to wrip cd's is to run the command:
```

cat /dev/dvdrom > /home/$USER/dvdfile.iso

```

This will rip the DVD into an ISO.  Make sure that /dev/dvdrom is your dvdrom or this won't work.

---

### Post by andrew.46 on 2008-11-08
Hi MrWes:

> **MrWES said:**
> OK...I've started exploring the power of CLI applications. I just spent the last few minutes playing around with abcde: A Better CD Extractor-- very powerful and pretty easy to use once I setup the abcde.conf file. Now I'm looking for some command line applications to rip dvd's and convert to avi. Any suggestions?

Rather than avi you could do worse than try this guide:

[http://andrews-corner.org/matrix.html](http://andrews-corner.org/matrix.html)

which is written for MPlayer, MEncoder, Matroska and NeroAacENC (soon to return to Ogg Vorbis). 

  Andrew

---

### Post by stephanvaningen on 2008-11-08
> **neurostu said:**
> a great way to wrip cd's is to run the command:
```

cat /dev/dvdrom > /home/$USER/dvdfile.iso

```

This will rip the DVD into an ISO.  Make sure that /dev/dvdrom is your dvdrom or this won't work.

Tried that, but get error on both tries:
```
stephan@living-vib:~$ cat /dev/scd0 > ~/iso/ra2a.iso
cat: /dev/scd0: Input/output error
stephan@living-vib:~$ cat /dev/scd0 > ~/iso/dre2006-disc2.iso
cat: /dev/scd0: Input/output error
stephan@living-vib:~$ 

```

---

### Post by neurostu on 2008-11-08
are you sure that scd0 is your cdrom drive? you can usually use cdrom0 or cdrom

---

### Post by bodhi.zazen on 2008-11-08
> **neurostu said:**
> are you sure that scd0 is your cdrom drive? you can usually use cdrom0 or cdrom

Yes, many distros changed to /dev/scdx

The symbolic links, however, still use /media/cdrom

```
grep scd0 /etc/fstab
[COLOR=green]/dev/scd0[/COLOR]       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

ls -l /media

[COLOR=cyan]lrwxrwxrwx 1 root 999    6 2008-05-28 06:36 cdrom -> cdrom0[/COLOR]
drwxr-xr-x 2 root 999 4096 2008-05-28 06:36 cdrom0
```

---

### Post by Dr Small on 2008-11-08
> **stephanvaningen said:**
> Tried that, but get error on both tries:
```
stephan@living-vib:~$ cat /dev/scd0 > ~/iso/ra2a.iso
cat: /dev/scd0: Input/output error
stephan@living-vib:~$ cat /dev/scd0 > ~/iso/dre2006-disc2.iso
cat: /dev/scd0: Input/output error
stephan@living-vib:~$ 

```
Try:
```
dd if=/dev/cdrom of=filename.iso
```

---

### Post by bodhi.zazen on 2008-11-08
I like these links as well :

[http://www.terminally-incoherent.com/blog/2007/05/21/a-day-without-x/](http://www.terminally-incoherent.com/blog/2007/05/21/a-day-without-x/)

[http://pjvenda.blogspot.com/2007/05/using-linux-without-x.html](http://pjvenda.blogspot.com/2007/05/using-linux-without-x.html)

---

