---
title: "Starting Jack fail"
date: 2012-11-27
forum: New to Ubuntu
---

### Post by esse2k on 2012-11-27
Hello!

I fail when trying to start the Jack audio server/client. I have no idea whats wrong ive enabled realtime threading and tried many different settings.. what i get is these error messages:

23:35:23.254 Patchbay deactivated.
23:35:23.260 Statistics reset.
23:35:23.289 ALSA connection change.
23:35:23.327 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
23:35:23.699 D-BUS: JACK server could not be started. Sorry
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
23:35:23.850 ALSA connection graph change.
Tue Nov 27 23:35:23 2012: Starting jack server...
Tue Nov 27 23:35:23 2012: JACK server starting in realtime mode with priority 10
Tue Nov 27 23:35:23 2012: control device hw:0
Tue Nov 27 23:35:23 2012: control device hw:0
Tue Nov 27 23:35:23 2012: [1m[31mERROR: Failed to acquire device name : Audio0 error : Cannot allocate memory[0m
Tue Nov 27 23:35:23 2012: [1m[31mERROR: Audio device plughw:0 cannot be acquired...[0m
Tue Nov 27 23:35:23 2012: [1m[31mERROR: Cannot initialize driver[0m
Tue Nov 27 23:35:23 2012: [1m[31mERROR: JackServer::Open() failed with -1[0m
Tue Nov 27 23:35:23 2012: [1m[31mERROR: Failed to open server[0m
Tue Nov 27 23:35:25 2012: Saving settings to "/home/esse2k/.config/jack/conf.xml" ...
23:35:26.039 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started

---

