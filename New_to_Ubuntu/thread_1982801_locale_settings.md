---
title: "locale settings"
date: 2012-05-19
forum: New to Ubuntu
---

### Post by spillage2 on 2012-05-19
Hi All,

This is really driving me mad as I cannot resolve it:

(process:3324): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
  using Gstreamer version: 0.10.28, Python binding version: 0.10.18
Traceback (most recent call last):
  File "/usr/bin/soundconverter", line 108, in <module>
    locale.setlocale(locale.LC_ALL,"")
  File "/usr/lib/python2.6/locale.py", line 513, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting
mark@mark-desktop:~$ 

I have ran sudo dpkg-reconfigure locales and install locales-all. 

Have now run out ideas and searches on google...

Cheers,

Mark.

---

### Post by Silent Warrior on 2012-05-19
I'm not sure if it'll solve anything, but if it were me, I'd open rc.local and check my locale settings in that file. (Edit, save, reboot will probably be necessary.) I typically use sudo nano, but gedit as root works just as well.
```
Near the top of the file you should find a line saying

LOCALE=

Adjust this to your language code (either en or en_UK, I expect - I'm sv myself, so you shouldn't take my word for it). Then save and reboot.
```
And, well, if you don't get any scary messages during boot, you're fine. If you already have a variation of 'en' in that line, DO NOTHING WHATSOEVER TO THAT FILE. It'll bother your neighbour's hamster if you do something crazy. Maybe you're experienced enough to know this, but it bears repeating.

You know, I think I've seen this once or twice when I dared running Arch (awesome fun - for the two-three weeks AT MOST until I did something I shouldn't have), but I can't understand how this would happen in Ubuntu... Did every update apply correctly?

---

### Post by spillage2 on 2012-05-20
Ok thanks for the reply.

Not sure whats going on but have 3 rc.local files going on and I dont know why.

#! /bin/sh
### BEGIN INIT INFO
# Provides:          rc.local
# Required-Start:    $remote_fs $syslog $all
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:
# Short-Description: Run /etc/rc.local if it exist
### END INIT INFO


PATH=/sbin:/usr/sbin:/bin:/usr/bin

. /lib/init/vars.sh
. /lib/lsb/init-functions

do_start() {
    if [ -x /etc/rc.local ]; then
            [ "$VERBOSE" != no ] && log_begin_msg "Running local boot scripts (/etc/rc.local)"
        /etc/rc.local
        ES=$?
        [ "$VERBOSE" != no ] && log_end_msg $ES
        return $ES
    fi
}

case "$1" in
    start)
    do_start
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac

---------------------------------------------------------------

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0

---------------------------------------------------------------------------
and this one.

update-rc.d rc.local start 99 2 3 4 5 .

Sure there is something wrong here...????

---

### Post by Silent Warrior on 2012-05-20
Having a few different rc.local seems normal - I think I have some numbered .1, .2, .3... Anyway. Those are actually nothing like the rc.local I hoped you'd find. Did you open /etc/rc.local, not some rc.local in your home folder?

---

