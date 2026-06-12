---
title: "Quiet athlon tips - coolbit"
date: 2005-04-30
forum: Outdated Tutorials &amp; Tips
---

### Post by johnkenyon on 2005-04-30
Hi all,

This is my first post as I have just moved over to ubuntu from yoper. I miss the raw speed of yoper but you guys really have a lot more info for getting started. I'm getting to like gnome too (other than the lack of a menu editor).

There is an Athlon Powersaving HOWTO over here -
[http://www.daniel.nofftz.net/linux/](http://www.daniel.nofftz.net/linux/)

I have added this to my startup and it makes a substantial difference to the noise level (as I have a temperature controlled fan for my cpu).

Any comments about the script would be appreciated. Watch the line wraps as usual.
```

$ cat /etc/init.d/coolbit
#!/bin/sh
#
# Added by john (not finished yet ...)
# NOTE: This is  only for KT266/266A/333,KM266/266A/333, ...: (needs definitively acpi enabled)
# See http://www.daniel.nofftz.net/linux/ for other chipsets

PATH=/sbin:/bin:/usr/sbin:/usr/bin

echo " * Shut the damn CPU up as it is too loud. Not quite as quiet as coolbit"
case "$1" in
    start|restart|status)
        setpci -v -H1 -s 0:0.0 92=$(printf %x $((0x$(setpci -H1 -s 0:0.0 92) | 0x80))) 2>&1 >/dev/null
        setpci -v -H1 -s 0:0.0 95=$(printf %x $((0x$(setpci -H1 -s 0:0.0 95) | 0x02))) 2>&1 >/dev/null
        ;;
    stop)
        setpci -v -H1 -s 0:0.0 92=$(printf %x $((0x$(setpci -H1 -s 0:0.0 92) & 0x7f))) 2>&1 >/dev/null
        setpci -v -H1 -s 0:0.0 95=$(printf %x $((0x$(setpci -H1 -s 0:0.0 95) & 0xfd))) 2>&1 >/dev/null
        ;;
    force-reload)
        ;;

    *)
        echo $"Usage: $0 {start|stop|restart|status|force_reload}"
        exit 3
        ;;
esac

```

It is then sym linked in /etc/rcS.d for startup.

Cheers,
John

---

### Post by Professor X on 2005-04-30
> I'm getting to like gnome too (other than the lack of a menu editor). 

You can get a menu editor for gnome.  See [this](http://www.ubuntuforums.org/showthread.php?t=21390) post.

Nice tip btw.

---

### Post by johnkenyon on 2005-04-30
In reply to my own post-

I found this in universe which does exactly the same thing. This would probably be a better approach than my original script.

**Enable powersaving mode for Athlon/Duron processors**
athcool is a small utility for enabling/disabling Powersaving mode
for AMD Athlon/Duron processors.

athcool 0.3.8-2

[http://members.jcom.home.ne.jp/jacobi/linux/softwares.html](http://members.jcom.home.ne.jp/jacobi/linux/softwares.html)

Cheers,
John

---

### Post by tdell on 2005-04-30
Excellent!!! I have been looking for something like this since removing Windows from my computer. I am now saving that 6C again. 
Many thanks.

Tom

---

