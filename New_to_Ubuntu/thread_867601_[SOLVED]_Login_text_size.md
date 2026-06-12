---
title: "[SOLVED] Login text size"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by alienexplorers on 2008-07-23
In the login screen my text is so large it is out of the boxes.  I know there is a file somewhere that you can add a line to adjust the font size.  If anyone knows where this file is please let me know.

---

### Post by /usr/bin/hacked? on 2008-07-23
[http://ubuntuforums.org/showthread.php?t=786963&highlight=96+dpi](http://ubuntuforums.org/showthread.php?t=786963&highlight=96+dpi)
As said by nick_h:
> Re: Huge login screen font
Quote:
[QUOTE]I do not know where to put a .dpi option in the gdm.conf file.

Can anyone help with this?
In your /etc/gdm/gdm.conf file you will see a section like the following:
Code:

```
[server-Standard]
name=Standard server
command=/usr/bin/X -br -audit 0 -dpi 96
```

You can add a dpi option here (96 dpi in my example).[/QUOTE]

---

