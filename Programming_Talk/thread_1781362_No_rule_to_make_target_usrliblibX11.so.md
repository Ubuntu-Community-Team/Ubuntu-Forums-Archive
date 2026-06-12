---
title: "No rule to make target /usr/lib/libX11.so"
date: 2011-06-13
forum: Programming Talk
---

### Post by Amablue on 2011-06-13
I'm writing a program using the library SFML, which requires libX11. I just recently upgraded to ubuntu 11.04 from an older version, and ever since I did I can't compile my program. I get the following error:

```
    make[3]: *** No rule to make target `/usr/lib/libX11.so', needed by `lib/libsfml-window.so.2.0.0'.  Stop.
```

I thought maybe that when I upgraded Ubuntu that package was uninstalled for some reason, but according to Synaptic, I have libX11-dev (I'm just assuming that's what I should be looking for, but I'm probably wrong).

Running `apt-get install libx11-dev` gives this output:

```
    sudo apt-get install libx11-dev
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    libx11-dev is already the newest version.
      g++-4.4 libstdc++6-4.4-dev
    Use 'apt-get autoremove' to remove them.
    0 upgraded, 0 newly installed, 0 to remove and 32 not upgraded.
```

and running with the --reinstall flag gives this:

```
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    The following packages were automatically installed and are no longer required:
      g++-4.4 libstdc++6-4.4-dev
    Use 'apt-get autoremove' to remove them.
    0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 32 not upgraded.
    Need to get 0 B/3,104 kB of archives.
    After this operation, 0 B of additional disk space will be used.
    (Reading database ... 279595 files and directories currently installed.)
    Preparing to replace libx11-dev 2:1.4.2-1ubuntu3 (using .../libx11-dev_2%3a1.4.2-1ubuntu3_i386.deb) ...
    Unpacking replacement libx11-dev ...
    Processing triggers for man-db ...
    Setting up libx11-dev (2:1.4.2-1ubuntu3) ...

```

---

### Post by dwhitney67 on 2011-06-13
Have you checked to see if the file (symbolic link) /usr/lib/libX11.so exists?

---

### Post by Amablue on 2011-06-13
It does not. 

There is a folder called X11 in /usr/lib/, but there is no libX11.so anywhere as far as I can tell.

---

### Post by dwhitney67 on 2011-06-13
> **Amablue said:**
> It does not. 

There is a folder called X11 in /usr/lib/, but there is no libX11.so anywhere as far as I can tell.

Try installing it:
```

sudo apt-get install libx11-6

```

---

### Post by Amablue on 2011-06-13
Doing that didn't make any difference. Neither did adding --reinstall. There is still no libx11.so in my /usr/lib/ folder. 

```
~$ ls /usr/lib/ |grep -i x11
libgdkglext-x11-1.0.so.0
libgdkglext-x11-1.0.so.0.0.0
libgdk-x11-2.0.so.0
libgdk-x11-2.0.so.0.2400.4
libgtkglext-x11-1.0.so.0
libgtkglext-x11-1.0.so.0.0.0
libgtk-x11-2.0.so.0
libgtk-x11-2.0.so.0.2400.4
libva-x11.so.1
libva-x11.so.1.0.8
X11
```

---

### Post by gmargo on 2011-06-13
libX11.so comes from the **libx11-dev** package.
But as you can see from the below link, it does not live in /usr/lib/.

[http://packages.ubuntu.com/search?searchon=contents&keywords=libX11.so&mode=exactfilename&suite=natty&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=libX11.so&mode=exactfilename&suite=natty&arch=any)

It lives in one of these places (32-bit, 64-bit):
/usr/lib/i386-linux-gnu/libX11.so
/usr/lib/x86_64-linux-gnu/libX11.so

You can get the compile/link arguments from pkg-config:
```

$ pkg-config --libs x11
-L/usr/lib/x86_64-linux-gnu -lX11

```

---

### Post by Amablue on 2011-06-13
Did it formally live in /usr/lib/ or something? (or if not, what would have changed to cause this error to appear now but not before?)

(for the record, I haven't tried it yet, I'll try that as soon as I get home tonight)

---

### Post by gmargo on 2011-06-14
> 
Did it formally live in /usr/lib/ or something?
Good question.  

In fact, on 10.10 Maverick and 10.04 Lucid, it does live in /usr/lib/.  It seems to have moved to the architecture specific directory as of 11.04 Natty.

Since you recently upgraded to Natty, was your SFML library built on Maverick or earlier? I think you need to reconfigure and rebuild the SFML library so that it's Natty compatible.

---

