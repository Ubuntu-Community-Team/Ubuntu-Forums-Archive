---
title: "Make a service"
date: 2008-12-05
forum: Programming Talk
---

### Post by hosseinyounesi on 2008-12-05
Hi,
Take a look at this script
[PHP]#!/bin/bash
#
# chkconfig: 35 90 12
# description: Foo server
#

# Get function from functions library
. /etc/rc.d/init.d/functions

# Start the service FOO
start() {
        initlog -c "echo -n Starting FOO server: "
        /path/myfile &
        ### Create the lock file ###
        #touch /var/lock/subsys/FOO
        success $"FOO server startup"
        echo
}

# Restart the service FOO
stop() {
        initlog -c "echo -n Stopping FOO server: "
        killproc myfile
        ### Now, delete the lock file ###
        rm -f /var/lock/subsys/FOO
        echo
}

### main logic ###
case "$1" in
  start)
        start
        ;;
  stop)
        stop
        ;;
  status)
        status FOO
        ;;
  restart|reload|condrestart)
        stop
        start
        ;;
  *)
        echo $"Usage: $0 {start|stop|restart|reload|status}"
        exit 1
esac

exit 0[/PHP]

It worked on fedora, but not on ubuntu ?!
/etc/rc.d/init.d/functions Does not exists !!! ?
And if I'm wrong doing the services entirely or there other ways, PLEASE tell me.

---

### Post by dwhitney67 on 2008-12-05
Ubuntu is a different beast from Fedora.  I believe the 'functions' you seek are located in /lib/lsb/init-functions.

When you source the functions file, I suppose you could check the return status ($?) and if it is not zero, then attempt to source the other file.  Now whether this would work on another flavour of Linux distro is unknown.

P.S.  Fedora use /etc/redhat-release to identify the system; Ubuntu uses /etc/lsb-release.

---

### Post by hosseinyounesi on 2008-12-06
Thanks,
I got it.

---

