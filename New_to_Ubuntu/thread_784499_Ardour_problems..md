---
title: "Ardour problems."
date: 2008-05-06
forum: New to Ubuntu
---

### Post by Periswell on 2008-05-06
hi

As someone somewhere might recall, i made a post earlier asking if there was any other programs in which i could change a midi file into any other typer of music type and someone answered that i should use ardour. so i did what this mate said i should do and downloaded it. when it had finally installed it came up with the error saying that there was something wrong with jack. so, what i did was i went onto synaptic and downloaded everything that came up when i searched jack. i have no midi devices attached to my computer, i just wanted to use ardour to convert some files. still this did not fix my problem and it kept on coming up with the same error message. in terminal it came up with this:

> root@utnubu:/home/joshua# '/usr/lib/ardour2/ardour-2.3'
/usr/lib/ardour2/ardour-2.3: error while loading shared libraries: libardour.so: cannot open shared object file: No such file or directory
root@utnubu:/home/joshua# '/usr/bin/ardour2'
WARNING: Your system has a limit for maximum amount of locked memory!
This might cause Ardour to run out of memory before your system runs out of memory. You can view the memory limit with 'ulimit -l', and it is normally controlled by /etc/security/limits.conf
Ardour/GTK 2.3
   (built using 3029 and GCC version 4.2.3 (Ubuntu 4.2.3-1ubuntu2))
Copyright (C) 1999-2007 Paul Davis
Some portions Copyright (C) Steve Harris, Ari Johnson, Brett Viren, Joel Baker

Ardour comes with ABSOLUTELY NO WARRANTY
not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
This is free software, and you are welcome to redistribute it 
under certain conditions; see the source for copying conditions.
loading default ui configuration file /etc/ardour2/ardour2_ui_default.conf
Loading ui configuration file /etc/ardour2/ardour2_ui_dark.rc
theme_init() called from internal clearlooks engine
loading system configuration file /etc/ardour2/ardour_system.rc
ardour: [INFO]: No H/W specific optimizations in use
ardour: [INFO]: looking for control protocols in /root/.ardour2/surfaces/:/usr/lib/ardour2/surfaces/
ardour: [INFO]: Control surface protocol discovered: "Generic MIDI"
powermate: Opening of powermate failed - No such file or directory
ardour: [INFO]: Control protocol powermate not usable
ardour: [INFO]: Control surface protocol discovered: "Mackie"
JACK COMMAND: /usr/bin/jackd -p 128 -T -d alsa -n 2 -r 48000 -p 1024 -d hw:0,0 
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0,0|hw:0,0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0,0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns



i dont know what the problem is so could someone please help as it is getting very frustrating. all help will be most appreciated.

-josh

---

### Post by quirks on 2008-05-06
I'm not sure, if you want to here this, but I would go for Timidity, as 3rdalbum already pointed out in a previous thread of you ([http://ubuntuforums.org/showpost.php?p=4894654&postcount=4](http://ubuntuforums.org/showpost.php?p=4894654&postcount=4)). It's in the repositories and I have never had problems with it.

---

### Post by Tatty on 2008-05-06
Ardour is available via synaptic, is that how you installed it?  if not i recommend removing your installation and installing through synaptic, and then starting the

Also you should not ever have to log in as root in a ubuntu system unless something goes really wrong. In particular you shouldnt be trying to run ardour as root.  I reccomend you read this [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) and [re-disable your root account]("https://help.ubuntu.com/community/RootSudo#head-c625ac47fd3adc6178d573a652c589bf4ebedab5") for security reasons.

Please post pack after trying this if you are still having problems.

---

