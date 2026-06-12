---
title: "Ubuntu Software Center"
date: 2012-10-17
forum: New to Ubuntu
---

### Post by SWGraphics291 on 2012-10-17
Anyone know where Ubuntu Software Center is located. Like usr/share/..../....../

---

### Post by Cheesemill on 2012-10-17
To list all of the files installed by a specific package you can install Synaptic.

My guess for the binary is /usr/bin/software-center (I'm not near a Ubuntu desktop at the minute).

As you've asked a similar question several times recently I'll also point you towards the 'which' command.
If you know the name of a program you can find out where its main binary file is by doing:
```
rob@arch:~$ which firefox
/usr/bin/firefox
```

A bit of light reading for you on where things live in the Linux filesystem:
[http://www.thegeekstuff.com/2010/09/...tem-structure/]("http://www.thegeekstuff.com/2010/09/linux-file-system-structure/")
[http://www.tuxradar.com/content/take...ilesystem-tour]("http://www.tuxradar.com/content/take-linux-filesystem-tour")
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

---

### Post by SWGraphics291 on 2012-10-17
Thanks, your guess is correct, thanks again.

---

