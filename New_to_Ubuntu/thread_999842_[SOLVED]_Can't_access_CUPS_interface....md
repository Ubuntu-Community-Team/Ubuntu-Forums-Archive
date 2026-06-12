---
title: "[SOLVED] Can't access CUPS interface..."
date: 2008-12-02
forum: New to Ubuntu
---

### Post by akelsall on 2008-12-02
I'm trying to access the CUPS web-based interface and keep getting this error message:

```
can't establish a connection to the server at localhost:631.
```

This worked in the past, but has stopped working after installing the latest version of CUPS (cups-1.3.9). I did try to stop/start cups with no luck. CUPS is running:

```
$ sudo /etc/init.d/cups status
cups: scheduler is running.

```

Any ideas?

Thanks,

Andy

---

### Post by akelsall on 2008-12-03
bump

---

### Post by akelsall on 2008-12-04
Well, I'm making progress. Stumbled upon the following URL (instructions from the URL are provided below), and now I no longer
get the error message ""can't establish a connection to the server at localhost:631." However, as I installed the printer via
the CUPS interface, I guessed at the URI. I still can't print (getting a message of :""Unable to start filter "pstocanonij" -
No such file or directory.", but I'm getting closer.

**[COLOR="DarkGreen"]https://help.ubuntu.com/community/PrintingCupsWebInterface[/COLOR]**

**[COLOR="Blue"]Basically, the steps are:[/COLOR]**

    1. Add "cupsys" to the shadow group. In terminal type:

                sudo adduser cupsys shadow

    2. Add youself to the lpadmin group. In terminal:

             sudo adduser <yourusername> lpadmin

     3. Restart CUPs. This can be done by typing:

              sudo /etc/init.d/cupsys restart

Andy

---

