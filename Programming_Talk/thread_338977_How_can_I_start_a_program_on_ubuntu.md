---
title: "How can I start a program on ubuntu?"
date: 2007-01-15
forum: Programming Talk
---

### Post by clapton on 2007-01-15
Hi ,

I've got a doubt about who is the best way to auto startup a program on ubuntu whithout X.

I use ubuntu on a robot, and I need do load a program on boot of ubuntu, and I've got to know who is the best way, to take everything automatic,

boot
program start
When Press reset button, another boot and another program start....


Thanks

---

### Post by Jussi Kukkonen on 2007-01-15
You'll probably want use an init script. That is what is mostly used for daemons and that's what your program sounds like.

read *man init* and *man update-rc.d*, then ask questions  if this is new to you

---

### Post by Keith Hedger on 2007-01-16
i needed to do a similar thing but on shutdown so i used:
#! /bin/sh

. /lib/lsb/init-functions

case "$1" in
    start)
        ;;
    restart|reload|force-reload)
        ;;
    stop)
	log_begin_msg "Shutting down Hoggy.local..."
	ssh -f hoggy.local shutdown -h now
	sleep 1
	log_end_msg 0
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac

exit 0

which i saved to /etc/init.d/shutdownhoggy
set the permisions to 755 (make executable)
and then made a symlink from /etc/rc0.d/XXX to the file, the order that the scripts are executed depend on the filename and so you should replace  "XXX" with somthing suitable,  the format of the filename is fairly straight foward.
obviously in your case you would want to put your commands in the start/reboot case.
hope this helps

---

