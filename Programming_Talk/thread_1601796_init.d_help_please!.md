---
title: "init.d help please!"
date: 2010-10-20
forum: Programming Talk
---

### Post by kharles on 2010-10-20
i'm having problems with setting up my init.d..
this  is what i have, but what happens when i try to start is it just hangs  (i'm guessing just like what happens when you type "php" with nothing else at command line).
also, when i try at command line to with php blah.php &, it seems to work but if i exit ssh, the process dies?

help would be very much appreciated...

here's my init.d:

```
#!/bin/bash
#
# /etc/rc.d/init.d/wyvern
#
# This shell script takes care of starting and stopping wyvern
#
# Author: Me
#
# chkconfig: 2345 13 87
# description: wyvern

# Source function library.
. /etc/init.d/functions

WYVERN_HOST=`hostname -a`
WYVERN_DIR=/opt/wyvern/server
PIDFILE=$WYVERN_DIR/logs/pid
STARTPIDFILE=$WYVERN_DIR/logs/startpid

if [ -f /etc/sysconfig/wyvern]; then
        . /etc/sysconfig/wyvern
fi


start() {
        echo -n "Starting WYVERN: "
        if [ -f $STARTPIDFILE ]; then
                PID=`cat $STARTPIDFILE`
                echo WYVERN already running: $PID
                exit 2;
        elif [ -f $PIDFILE ]; then
                PID=`cat $PIDFILE`
                echo WYVERN already running: $PID
                exit 2;
        else
                cd $WYVERN_DIR
                daemon php wyvern_socket_server.php
                RETVAL=$?
                echo
                [ $RETVAL -eq 0 ] && touch /var/lock/subsys/wyvern
                return $RETVAL
        fi

}

stop() {
        echo -n "Shutting down WYVERN: "
        echo
        killproc wyvern
        echo
        rm -f /var/lock/subsys/wyvern
        return 0
}

case "$1" in
    start)
        start
        ;;
    stop)
        stop
        ;;
    status)
        status wyvern
        ;;
    restart)
        stop
        start
        ;;
    *)
        echo "Usage:  {start|stop|status|restart}"
        exit 1
        ;;
esac
exit $?
```

---

### Post by kharles on 2010-10-20
any insight about making an init.d script for a php file would be very very appreciates. thanks

---

### Post by spjackson on 2010-10-20
Where is this script  wyvern_socket_server.php ? I would definitely use an absolute path there.

---

### Post by kharles on 2010-10-20
it's inside directory /opt/wyvern/server/
don't think that's the problem...

has anyone had experiences doing an init.d for a php script?  any differences?
script just seems to lock up, as if you just type php with no arguments into command line

---

### Post by kharles on 2010-10-20
i just tried with absolute path for my php script inside init.d...
same results

---

### Post by kharles on 2010-10-22
so now i have the script working, but wanted some other pointers.  in order to get it to work, i had to use nohup instead of daemon to start and to stop i use kill instead of killproc.

i dump the pid into a file, since it is no good to try to do things off the service name (it being php).

is there some way to use status with a pid?  because i don't want to call status php because it could be something else.  (currently calling status with the pid as i am doing does not work as intended.  it looks for a service with the name of the pid value which does not work.)

is there a more elegant way to start and stop as how i'm doing it?

i want to ensure that the socket that my service is using is freed when the service stops.  is there some way to do this in the init.d script?

thanks

current init.d:
```
#!/bin/bash
#
# /etc/rc.d/init.d/wyvern
#
# This shell script takes care of starting and stopping wyvern
#
# Author: Me
#
# chkconfig: 2345 13 87
# description: wyvern

# Source function library.
. /etc/init.d/functions

WYVERN_HOST='hostname -a'
WYVERN_DIR=/opt/wyvern/server
PIDFILE=$WYVERN_DIR/logs/pid
STARTPIDFILE=$WYVERN_DIR/logs/startpid


start() {
        echo -n "Starting WYVERN: "
        if [ -f $STARTPIDFILE ]; then
                PID=`cat $STARTPIDFILE`
                echo WYVERN already running startpid: $PID
                exit 2;
        elif [ -f $PIDFILE ]; then
                PID=`cat $PIDFILE`
                echo WYVERN already running pid: $PID
                exit 2;
        else
                cd $WYVERN_DIR
                nohup php /opt/wyvern/server/wyvern_socket_server.php &
                echo $! > $STARTPIDFILE
                RETVAL=$?
                echo
                [ $RETVAL -eq 0 ] && touch /var/lock/subsys/wyvern
                return $RETVAL
        fi

}

stop() {
        echo -n "Shutting down WYVERN: "
        echo
        kill `cat $STARTPIDFILE`
        rm -f $STARTPIDFILE
        echo
        rm -f /var/lock/subsys/wyvern
        return 0
}

case "$1" in
    start)
        start
        ;;
    stop)
        stop
        ;;
    status)
        status `cat $STARTPIDFILE`
        ;;
    restart)
        stop
        start
        ;;
    *)
        echo "Usage:  {start|stop|status|restart}"
        exit 1
        ;;
esac
exit $?
```

---

### Post by Moozillaaa on 2010-10-22
When you created a symlink for the the init.d file (if you even had to), did you add a start (or stop) parameter for the function?

Maybe it's not necessary in your case, but for some scripts, I think you have to add -s, or -K to the link syntax:
> 
ln -s /etc/init.d/wyvern /etc/rc.d/wyvern    (to start, or -K kill)

Just a guess here...

---

