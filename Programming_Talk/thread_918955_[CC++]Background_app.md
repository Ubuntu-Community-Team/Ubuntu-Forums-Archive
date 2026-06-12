---
title: "[C\C++]Background app"
date: 2008-09-13
forum: Programming Talk
---

### Post by StOoZ on 2008-09-13
I would like to write an application , that runs in the linux background , and monitors some stuff (files in my computer) , I know a script language will be better for this task , but still , I perfer C\C++ for educational purposes.
anyhow , my questions are :
1) if i'll create an executable file , and place it in /etc/init.d/
it will automatically launch on every boot and keep running until something stops it?

2) if the answer for the above question is 'yes' then , what is the use of creating deamons?? ([http://www.netzmafia.de/skripten/unix/linux-daemon-howto.html]("http://www.netzmafia.de/skripten/unix/linux-daemon-howto.html") )

thanks,

---

### Post by kknd on 2008-09-13
You can make an application that runs forever, it can be a simple for(;;){}; if you want, but the steps in the howto you posted are some tips to enhance the security and etc, since daemons are usually executes with extra privileges.

---

### Post by lian1238 on 2008-09-13
> **kknd said:**
> You can make an application that runs forever, it can be a simple for(;;){}; if you want, but the steps in the howto you posted are some tips to enhance the security and etc, since daemons are usually executes with extra privileges.
Then you can put it in the startup programs.

---

### Post by StOoZ on 2008-09-13
I see , start-up programs , or in the etc/init.d/ right?

---

### Post by dwhitney67 on 2008-09-13
StOoZ

In /etc/init.d you should create/install a script that will launch your application (daemon if you will).  This script generally accepts at a minimum two possible command-line args:  start and stop.

If 'start' is passed to the script, then you start your application.  Conversely, if 'stop' is passed, then you gracefully stop the application.

Now, to get this script into action, you will need to create the necessary symbolic links in various /etc/rcN.d, where N typically is 0, 3, 5, 6.

An alternative is to invoke your C/C++ application (not the script) from within /etc/rc.local.  Bear in mind that you will not be able to shut down the application gracefully when the system shuts down if you go with this alternative.

As for your C/C++ application, it should be installed in either /usr/bin or maybe /usr/local/bin, or if you wish to forgo standards, then install it wherever you wish.

The link you provided concerning daemon development is nice, but the author left out some elements, namely those that involve catching system signals (to abort, restart, etc).  Nevertheless, it is a good guide to get you going.

P.S.  A typical script in /etc/init.d has the following structure:
```
#!/bin/sh

case "$1" in
    start)
            # start the application
            ;;

    stop)
            # stop the application
            ;;

    restart)
            # restart the application
            ;;

    *)
            echo "Usage: $0 start|stop|restart" >&2
            exit 1
            ;;
esac
```

---

### Post by kknd on 2008-09-13
Besides security, you will have to deal with things like: can I have multiple instances of the daemon running(doesn't makes sense at all)? How will you be able to stop your daemon (or how will your daemon receive messages from the system)?

---

