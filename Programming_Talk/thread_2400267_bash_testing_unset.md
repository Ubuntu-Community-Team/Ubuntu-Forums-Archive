---
title: "bash testing unset"
date: 2018-09-04
forum: Programming Talk
---

### Post by VMC on 2018-09-04
I have no idea if this belongs here or newbe, but:

I had a rather seemingly bazaar bash test:
 ```
if [ -d /etc/X11/xinit/xinitrc.d ] ; then for f in /etc/X11/xinit/xinitrc.d/?*.sh ; do
  [ -x "$f" ] && . "$f"
 done
 unset f
fi
exec startlxqt
```
Bazaar in that my config-monitor won't work without it. The test I know is weather or not the files are executable. Then does the  "unset f" make them un-executable?
I guess my question is what does "unset f" do. The "f" is relating to the files that are checked, but what gets unset?

I did google and found [this]("https://unix.stackexchange.com/questions/382391/what-does-unset-do"), but not sure of outcome.

---

### Post by TheFu on 2018-09-04
if this is bash, then unset removes the variable from having any value and removes it from the variable. It is as if it was never used previously. Basically, it is null.  This should work similarly across all Bourne Shell-like shells.

[https://www.tldp.org/LDP/abs/html/internal.html#UNS](https://www.tldp.org/LDP/abs/html/internal.html#UNS)

But from the incomplete script above, we don't know if bash is being used at all.  That segment appears to just look for files (.sh extensions only) in the specific directory and if those files have execute permissions, run them assuming a  Bourne Shell compatible method. Honestly, I wouldn't bother with the unset at all. I don't think it is needed, if there is a loop.  On my system, that directory is empty.

---

### Post by steeldriver on 2018-09-04
The only situation in which I can imagine it making any difference is if you are exporting f, and the variable happens to have some significance in your lxqt environment

---

### Post by VMC on 2018-09-04
Thanks for response. The script above is complete in and of itself, but it references two other scripts that for some reason are needed. It all has to do with lxqt-monitor-settings failing to execute. I'll put them here for clairty, but I think it hinges on the the "dbus-update-activation-environment". So if the two files referenced are executable (-x) then something gets unset. I still don't fully understand it.

"[COLOR=#000000][FONT=&amp]/etc/X11/xinit/xinitrc.d" files:[/FONT][/COLOR]
```
#!/bin/sh
systemctl --user import-environment DISPLAY XAUTHORITY

if command -v dbus-update-activation-environment >/dev/null 2>&1; then
        dbus-update-activation-environment DISPLAY XAUTHORITY
fi
===
#!/bin/sh
case "${DESKTOP_SESSION-}" in
  gnome*) # Done by gnome-settings-daemon
  ;;
  *)
    # Extra check in case DESKTOP_SESSION is not set correctly
    if [ -z "${GNOME_DESKTOP_SESSION_ID-}" ]; then
      GTK_MODULES="${GTK_MODULES:+$GTK_MODULES:}canberra-gtk-module"
      export GTK_MODULES
    fi
  ;;
esac
```

As I said its partly **bash unset** understanding, and part "**lxqt-monitor-settings**" failing , with a ".xinitrc" fix.

---

### Post by TheFu on 2018-09-04
```
#!/bin/shsystemctl --user import-environment DISPLAY XAUTHORITY
```
That line is clearly wrong.
```

#!/bin/sh
systemctl --user import-environment DISPLAY XAUTHORITY
```
is probably correct.  That is **Not** bash. That is Bourne shell and on most Ubuntu systems, it is really "dash."

The **unset f** is unimportant. Seriously.  Unimportant.  You can remove it. The f variable is set just above it and used a few times.  THAT is the entire purpose.

I didn't think that lxqt was going to be released until the fall Lubuntu.  I tried to use it with 18.04 back in June and it wouldn't load at all.  I chalked  it up to being less than alpha ready code.  Maybe I'm wrong.

---

### Post by VMC on 2018-09-04
TheFu, I made a mistake on the one you pointed out. I edited correctly now. Thanks.

Also Lubuntu works well as of right now, with some issues relating to using getty auto-login.
This post is from another LXQT install that I could not understand the "unset" usage. (I still don't).

So the real change is in the statement:
```
[ -x "$f" ] && . "$f"
```
Am I correct. I'll change it to see.

---

### Post by TheFu on 2018-09-05
if whatever is stored in $f exists AND is executable, then run that script (the file stored in $f).

This is identical:
```
[ -x "$f" ] && source "$f"
```

. (dot) and source mean exactly the same thing in Bourne shell derivatives.

---

