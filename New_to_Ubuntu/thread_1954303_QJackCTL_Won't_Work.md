---
title: "QJackCTL Won't Work"
date: 2012-04-07
forum: New to Ubuntu
---

### Post by doppel.ganger on 2012-04-07
2 Windows popped up saying that "the JACK server couldn't be started" and "couldn't connect to Jack server as client." This is what was in the messages panel:

```
20:39:14.618 Patchbay deactivated.
20:39:14.634 Statistics reset.
20:39:14.672 ALSA connection change.
20:39:14.751 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
20:39:14.798 ALSA connection graph change.
20:39:21.415 D-BUS: JACK server could not be started. Sorry
Sat Apr  7 20:39:21 2012: Starting jack server...
Sat Apr  7 20:39:21 2012: JACK server starting in realtime mode with priority 10
Sat Apr  7 20:39:21 2012: [1m[31mERROR: Cannot lock down 82241434 byte memory area (Cannot allocate memory)[0m
Sat Apr  7 20:39:21 2012: control device hw:0
Sat Apr  7 20:39:21 2012: control device hw:0
Sat Apr  7 20:39:21 2012: [1m[31mERROR: Failed to acquire device name : Audio0 error : Cannot allocate memory[0m
Sat Apr  7 20:39:21 2012: [1m[31mERROR: Audio device hw:0 cannot be acquired...[0m
Sat Apr  7 20:39:21 2012: [1m[31mERROR: Cannot initialize driver[0m
Sat Apr  7 20:39:21 2012: [1m[31mERROR: JackServer::Open() failed with -1[0m
Sat Apr  7 20:39:21 2012: [1m[31mERROR: Failed to open server[0m
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Sat Apr  7 20:39:23 2012: Saving settings to "/home/thomas/.config/jack/conf.xml" ...
20:39:27.435 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
```

---

### Post by bradleypariah on 2012-04-07
I know this may not be super helpful, but when I experienced this error, I clicked "setup" and then just played with stuff.
I turned real time on/off, chose different interface options, etc.
Jack can be a little picky, but I've never had it absolutely refuse to work.
I trust that if you just change a couple things around it'll eventually start up.

Conquer-and-divide is what's audio troubleshooting is all about, right?

Change something, try to start the engine again.
Change something else, try to start it again.

Take a screenshot of your OG setup in case you bork it so much you can't remember where you started ;)

I wish I could help more, but from one audio guy to another, I believe you will make it work.

---

