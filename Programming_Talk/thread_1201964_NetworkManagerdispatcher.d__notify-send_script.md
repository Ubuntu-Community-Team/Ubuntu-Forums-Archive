---
title: "NetworkManager/dispatcher.d / notify-send script"
date: 2009-07-01
forum: Programming Talk
---

### Post by Hal.9000 on 2009-07-01
I have been trying to make a script to report my internet ip address using notify-send (part of the libnotify-bin package). This is what I have so far.
```
#!/bin/sh -e
# A script that should show my external ip addresss whenever networkmanager makes a new connection

cd /tmp
wget -t 1 -T 5 http://www.whatismyip.com/automation/n09230945.asp -O notify-newip
if [ "${?}" = "0" ]
then
        touch notify-oldip
        OLDIP=`cat notify-oldip`
        NEWIP=`cat notify-newip`
        if [ "${NEWIP}" != "${OLDIP}" ]
        then
                notify-send -t 2500 'New Internet IP Address' ${NEWIP}
                mv notify-newip notify-oldip
        fi
fi
```

So if I run this script manually I see the little notification bubble and it seems to work fine, but when I place it in /etc/NetworkManager/dispatcher.d/ it doesn't seem to get executed when I connect to a new wireless network.

I'm a bit of a noob at writing bash scripts so let me know if I've done something stupid.

Thanks

---

### Post by kerry_s on 2009-07-01
just a guess, but when you put it in /etc/NetworkManager/dispatcher.d/ it's running as root, root does not have a display. try exporting the display to show on. 

export DISPLAY=:0.0

i think, might be:

export DISPLAY=localhost:0.0

i can't remember, google it.

---

### Post by Hal.9000 on 2009-07-02
Apparently this should be possible but I can't get it to work.
If anybody is interested look [here]("http://ubuntuforums.org/showthread.php?t=775170").

---

### Post by spet on 2010-05-15
Sorry for resurrecting this old thread, but I've found the solution, and its (somewhat) elegant.

notify-send will work if the correct DISPLAY value is exported, and to do that I use fgconsole to get the tty number of the active display. I then use ps to get the X or Xorg command, which contains the display.

A complete (but not exactly useful) script could look like this:
```
#!/bin/sh -e

# If the display variable is unset, find the correct display number
# and set the variable.
if [ -z "$DISPLAY" ]; then
    console=`fgconsole`
    dispnum=`ps t tty$console | sed -n -re 's,.*/X(org)? .*:([0-9]+).*,\2,p'`
    export DISPLAY=":$dispnum"
fi

notify-send -i info "Network action" "$1: $2"
```
Happy scripting! :)

---

