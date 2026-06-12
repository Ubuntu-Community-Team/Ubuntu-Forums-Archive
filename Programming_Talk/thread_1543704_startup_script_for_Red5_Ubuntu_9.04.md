---
title: "startup script for Red5 Ubuntu 9.04"
date: 2010-08-01
forum: Programming Talk
---

### Post by tapas_mishra on 2010-08-01
I am creating startup script for Red5 on Ubuntu.
Red5 is installed in /opt/red5

Following is a working script  on a CentOS Box on which Red5 is running
```

*#==========Start init script ========== *
 [I]#!/bin/sh
    

    PROG=red5
    RED5_HOME=/opt/red5/dist
    DAEMON=$RED5_HOME/$PROG.sh
    PIDFILE=/var/run/$PROG.pid

    # Source function library
    . /etc/rc.d/init.d/functions

    [ -r /etc/sysconfig/red5 ] && . /etc/sysconfig/red5

    RETVAL=0

    case "$1" in
    start)
    echo -n $"Starting $PROG: "
    cd $RED5_HOME
    $DAEMON >/dev/null 2>/dev/null &
    RETVAL=$?
    if [ $RETVAL -eq 0 ]; then
    echo $! > $PIDFILE
    touch /var/lock/subsys/$PROG

    fi
    [ $RETVAL -eq 0 ] && success $"$PROG startup" || failure $"$PROG startup"
    echo
    ;;
    stop)
    echo -n $"Shutting down $PROG: "
    killproc -p $PIDFILE
    RETVAL=$?
 echo
    [ $RETVAL -eq 0 ] && rm -f /var/lock/subsys/$PROG
    ;;
    restart)
    $0 stop
    $0 start
    ;;
    status)
    status $PROG -p $PIDFILE
    RETVAL=$?
    ;;
    *)
    echo $"Usage: $0 {start|stop|restart|status}"
    RETVAL=1
    esac

    exit $RETVAL
[/I]
``` What do I need to replace for Ubuntu in the above script.
As I did not find  rc.d/functions on Ubuntu .
Also /etc/init.d/functions  did not existed.
I would like to be able to use them with service as Red hat distributions do.
I checked /lib/lsb/init-functions.

---

