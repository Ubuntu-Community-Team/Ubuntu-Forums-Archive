---
title: "Communicating with a Daemon in CPP"
date: 2009-12-16
forum: Programming Talk
---

### Post by agoessling on 2009-12-16
I have written a daemon in CPP that listens to the serial port and alters a mysql database when necessary.  This works fine, but now I need to communicate to the daemon after it has been started.  There is an event that happens on average at most once a week that the daemon needs to know about.  Hopefully I would be able to communicate to the daemon through php script running on apache on the same machine.  I have been reading up about handling signals on linux (very dense), and I have a very rudimentary understanding.  What I'm confused about is how to actually send a signal without knowing about the daemon's PID.  That made me question if a signal is the right way to do this in the first place.  The daemon doesn't need to know any information other than the event occured.  Any ideas on how to communicate such an event to a deamon?

Thanks,
Andy

---

### Post by lykwydchykyn on 2009-12-16
I'm no expert on this, and not sure if I can answer your question as to the best way to do it, but I do know that a lot of daemons create PID files under /var/run to store their process ids, presumably so that scripts and other control tools can send them signals without explicitly entering a PID.

---

### Post by Barriehie on 2009-12-17
Along the lines of what **lykwydchykyn** said I've got a daemon that launches at boot time and the first part of the script is:
```

echo $$ > /var/run/picsdaemond.pid

```
this puts the PID in the file picsdaemond.pid

You could maybe do something like:
```

#!/bin/bash
echo $$ > /var/run/*MyDaemonName.pid*  # CamelCase for readability!
...
launch your cpp app.
...

```

HTH
Barrie

---

### Post by PmDematagoda on 2009-12-17
> **agoessling said:**
> I have written a daemon in CPP that listens to the serial port and alters a mysql database when necessary.  This works fine, but now I need to communicate to the daemon after it has been started.  There is an event that happens on average at most once a week that the daemon needs to know about.  Hopefully I would be able to communicate to the daemon through php script running on apache on the same machine.  I have been reading up about handling signals on linux (very dense), and I have a very rudimentary understanding.  What I'm confused about is how to actually send a signal without knowing about the daemon's PID.  That made me question if a signal is the right way to do this in the first place.  The daemon doesn't need to know any information other than the event occured.  Any ideas on how to communicate such an event to a deamon?

Thanks,
Andy

You have a few choices:-

1) Have the daemon open a message queue and listen for any signals when a client sends a message to the queue. When you get a message, process it(or not if you don't want data) and do what you need.

2) Use a named pipe(FIFO) and have the client put any messages it wants into it(you would need to poll the pipe).

3) Use DBus with the daemon as a client receiving the signal from a "server". Or perhaps the daemon as a server with the client calling method calls on the server's DBUs API when it wants to inform the server of an event.

4) Use the signals as suggested before.

Personally, I think the signals would be easier to implement. :)

---

### Post by dwhitney67 on 2009-12-17
Easiest is to use a signal.  Your external app can try to use the pkill command.

With pkill, you will need to know the name of the app that is running, and obviously the signal you want to send.  For example:
```

pkill -SIGUSR1 MyDaemon

```

---

