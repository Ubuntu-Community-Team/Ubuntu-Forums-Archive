---
title: "How to start jack? please tell me."
date: 2012-12-29
forum: New to Ubuntu
---

### Post by Hazim on 2012-12-29
When I tried to start Jack audio controller, it give this message[COLOR=#999999],
[/COLOR]  
[COLOR=#999999]11:49:30.735 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]11:49:30.742 Statistics reset.[/COLOR]
 [COLOR=#cccc99]11:49:30.753 ALSA connection change.[/COLOR]
 [COLOR=#999999]11:49:30.780 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 [COLOR=#ff0000]11:49:53.071 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Sat Dec 29 11:49:52 2012: Starting jack server...
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 Sat Dec 29 11:49:52 2012: JACK server starting in non-realtime mode
 Sat Dec 29 11:49:52 2012: [1m[31mERROR: Cannot lock down 82274202 byte memory area (Cannot allocate memory)[0m
 Sat Dec 29 11:49:53 2012: control device hw:0
 Sat Dec 29 11:49:53 2012: control device hw:0
 Sat Dec 29 11:49:53 2012: [1m[31mERROR: Failed to acquire device name : Audio0 error : Method "RequestRelease" with signature "i" on interface "org.freedesktop.ReserveDevice1" doesn't exist
 [0m
 Sat Dec 29 11:49:53 2012: [1m[31mERROR: Audio device hw:0 cannot be acquired...[0m
 Sat Dec 29 11:49:53 2012: [1m[31mERROR: Cannot initialize driver[0m
 Sat Dec 29 11:49:53 2012: [1m[31mERROR: JackServer::Open failed with -1[0m
 Sat Dec 29 11:49:53 2012: [1m[31mERROR: Failed to open server[0m
 Sat Dec 29 11:49:54 2012: Saving settings to "/home/hazim/.config/jack/conf.xml" ...
 [COLOR=#ff0000]11:50:02.434 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 [COLOR=#ff0000]11:50:15.770 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 Sat Dec 29 11:50:15 2012: Starting jack server...
 Sat Dec 29 11:50:15 2012: JACK server starting in realtime mode with priority 25
 Sat Dec 29 11:50:15 2012: [1m[31mERROR: Cannot lock down 82274202 byte memory area (Cannot allocate memory)[0m
 Sat Dec 29 11:50:15 2012: control device hw:0
 Sat Dec 29 11:50:15 2012: control device hw:0
 Sat Dec 29 11:50:15 2012: [1m[31mERROR: Failed to acquire device name : Audio0 error : Method "RequestRelease" with signature "i" on interface "org.freedesktop.ReserveDevice1" doesn't exist
 [0m
 Sat Dec 29 11:50:15 2012: [1m[31mERROR: Audio device hw:0 cannot be acquired...[0m
 Sat Dec 29 11:50:15 2012: [1m[31mERROR: Cannot initialize driver[0m
 Sat Dec 29 11:50:15 2012: [1m[31mERROR: JackServer::Open failed with -1[0m
 Sat Dec 29 11:50:15 2012: [1m[31mERROR: Failed to open server[0m
 Sat Dec 29 11:50:17 2012: Saving settings to "/home/hazim/.config/jack/conf.xml" ...
 [COLOR=#ff0000]11:50:19.792 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
  

but when I logout and login back, with no application running, it start properly. When I start other application such as firefox, it give me this error. How to actually start Jack?:confused:

---

