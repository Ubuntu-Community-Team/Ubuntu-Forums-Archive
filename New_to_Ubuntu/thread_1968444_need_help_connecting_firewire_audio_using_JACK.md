---
title: "need help connecting firewire audio using JACK"
date: 2012-04-29
forum: New to Ubuntu
---

### Post by nipra on 2012-04-29
Hi, I'm new to ubuntu and i've just installed ubuntu 12.04LTS. I'm using  a Focusrite saffire pro 14 firewire audio interface. When i start jack  audio connection tool using qjackctl, it says something like "cannot  connect to jack server as client". I think i have messed up with the  settings in the qjackctl setup window. Here's what i get:

12:54:08.012 Patchbay deactivated.
12:54:08.012 Statistics reset.
12:54:08.020 ALSA connection change.
12:54:08.027 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
jack server is not running or cannot be started
12:54:08.034 ALSA connection graph change.
12:55:04.968 D-BUS: JACK server could not be started. Sorry
Sun Apr 29 12:54:39 2012: Starting jack server...
Sun Apr 29 12:54:39 2012: JACK server starting in non-realtime mode
Sun Apr 29 12:54:39 2012: [1m[31mERROR: Cannot lock down 82241434 byte memory area (Cannot allocate memory)[0m
Sun Apr 29 12:54:49 2012: [1m[31mERROR: firewire ERR: Could not start streaming threads[0m
Sun Apr 29 12:54:49 2012: [1m[31mERROR: Cannot start driver[0m
Sun Apr 29 12:54:49 2012: [1m[31mERROR: JackServer::Start() failed with -1[0m
Sun Apr 29 12:54:49 2012: [1m[31mERROR: Failed to start server[0m
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
jack server is not running or cannot be started
12:55:38.693 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started

can someone let me know the recommended settings for my setup??
thanks in advance :)

---

### Post by thecreekninja on 2012-04-29
I am having the same problem.  With alsa jack connects fine, it is when I connect via FFADO it gives me this error.  I am using a presonus firebox which works fine in Natty, but for some reason Precise isn't working.  I am going to have to stick with Natty until this is resolved.

Thanks,

---

### Post by thecreekninja on 2012-05-02
I had to add my user to group audio, I guess there is no gui for this anymore in 12.04.

sudo adduser yourusername audio


restarted my system and now it works

---

### Post by petak23 on 2012-05-10
I have the same problem. I have Ubuntu 12.04 and Phonic Helx Board 12 Firewire MKII. And the jack say:
 p, li { white-space: pre-wrap; }  [COLOR=#990099]17:16:48.658 /usr/bin/jackd -P60 -p128 -dfirewire -dhw:0 -r44100 -p128 -n3[/COLOR]
 Cannot connect to server socket err = AdresÃ¡r alebo sÃºbor neexistuje
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#999999]17:16:48.685 JACK was started with PID=2032.[/COLOR]
 jackdmp 1.9.8
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2011 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK server starting in realtime mode with priority 60
 libffado 2.999.0- built Feb 17 2012 15:54:45
 firewire ERR: FFADO: Error creating virtual device
 Cannot attach audio driver
 JackServer::Open() failed with -1
 Failed to open server
 [COLOR=#999999]17:16:49.000 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#ff0000]17:16:50.825 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = AdresÃ¡r alebo sÃºbor neexistuje
 Cannot connect to server socket
 jack server is not running or cannot be started.


Where is problem???

---

