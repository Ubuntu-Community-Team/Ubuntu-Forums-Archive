---
title: "VLC Not Working"
date: 2012-12-29
forum: New to Ubuntu
---

### Post by Oweirdone on 2012-12-29
The title says it all recently.

I've tried reinstalling it, nothing changed.

It doesn't come up with an error message, I just double clock on the DVD icon to play it, and it does nothing.

Any ideas?

Thanks,

Owe.

---

### Post by gnush on 2012-12-29
Open up a terminal and enter vlc, what does it say?

Optionally, you can run vlc with the verbose option to get more information.

```
$ vlc --verbose
```

---

### Post by rrich1974 on 2012-12-29
[https://help.ubuntu.com/10.04/musicvideophotos/C/video-dvd.html](https://help.ubuntu.com/10.04/musicvideophotos/C/video-dvd.html)
now, take a look on this link. have you installed ubuntu resticted extras? 
read carefully!

---

### Post by Oweirdone on 2012-12-29
Response to

```
vlc
```

```
VLC media player 2.0.3 Twoflower (revision 2.0.2-93-g77aa89e)
[0x9047908] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.

```

Response to

```
vlc --verbose
```

```
VLC media player 2.0.3 Twoflower (revision 2.0.2-93-g77aa89e)
vlc: unknown option or missing mandatory argument `--verbose'
Try `vlc --help' for more information.
```

---

### Post by rrich1974 on 2012-12-29
once again, have you red the link? 
if you want to play a DVD you need some codecs, especially libdvdcss2.

---

### Post by gnush on 2012-12-29
> **Oweirdone said:**
> Response to

I'm sorry if I was ambiguous, I wanted you to open the file after you had opened VLC in the terminal. If there is an error, it will most likely output it in the terminal.

```
$ vlc --verbose *filename*
```

Should probably work fine aswell, unless there's some specific flag in order to open files from the command line.

---

### Post by iMac71 on 2012-12-29
even the following link might be somehow useful:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

