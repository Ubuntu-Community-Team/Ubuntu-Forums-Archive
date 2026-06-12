---
title: "add a &quot;beep&quot; sound when shutdown"
date: 2023-03-30
forum: New to Ubuntu
---

### Post by joeythedream on 2023-03-30
Hiya,

Just wonder how to add a beep sound when my machine is shutdown ?

My system : RPi4B with ubuntu server 22.04 with LXTE

Thanks

---

### Post by TheFu on 2023-03-30
Does a r-pi even have a speaker?  If not, forgetaboutit.

---

### Post by MAFoElffen on 2023-03-30
I used to do this with Ubuntu 12.04 LTS (play the "Apple" startup sound at boot and at shutdown)... Let's see if the same file structure is there, or if it has to be implemented differently.

Yes. Same file structure exists... Write a script to play your sound. Must have "full path" to the file you want to play. Put that script in folders '/etc/rc0.d' to play at shutdown, and in '/etc/rc6.d' to play at reboot. Make them executable.

Sample script:
```

#!/bin/bash
## play shutdown sound
/usr/bin/paplay /usr/share/sounds/ubuntu/ringtones/Harmonics.ogg

```
Choose whatever you want played...

On startup sounds, I just add a startup application task in the gui menu at "Startup Applications"...

Have fun.

---

### Post by TheFu on 2023-03-30
Pulse on my systems demand to be tied to a user session to work.  

I wanted to play music using the audio hardware connected directly to that PC, but it refused. Just adding my userid to the "audio" group didn't help.  Took a bit of looking around before I came to a "DISPLAY=:0" environment variable to trick Pulse into playing anything. This works over a remote connection, regardless of whether there is any user logged into the console.

Looked for a way to setup Pulse to run as a system  daemon and came across all sorts of warnings against it on the Pulse project website.  [https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/SystemWide/](https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/SystemWide/)

But if the hardware doesn't have any speaker, all this is useless.  [https://raspberrytips.com/raspberry-pi-speaker/](https://raspberrytips.com/raspberry-pi-speaker/) says there isn't any speaker built-in.  If you have external speakers connected, go wild.  I use this analog connection for one of my r-pi media player systems. Works well enough for stereo and even the old "surround sound" from the mid-1990s TV shows. It can't do 5.1 output, clearly, which is important for FPS games, unless you don't mind a 10 yr old girl sneaking up behind you with a knife because you don't know which direction she is coming from. This actually happened to a friend - and the girl was his daughter! She couldn't stop laughing. ;)

Linux has a "beep" command which will sound a tone at a frequency for a duration, if requested. Not exactly high-fi, but it is what other things like the BIOS uses to create their 'beeps' for troubleshooting on regular PCs.

---

### Post by MAFoElffen on 2023-03-31
With Ubuntu 12.04 LTS, I used to use mpg123. It doesn't need a session to play something. It is stil in the repo's, but you have to install it (not a default app)..

---

### Post by TheFu on 2023-03-31
12.04 is pre-pulse, pre-systemd.  It was 100% ALSA and OSS - completely different world back then.

---

### Post by joeythedream on 2023-03-31
Hi Elffen, thanks a lot, you are great. 

> **MAFoElffen said:**
> I used to do this with Ubuntu 12.04 LTS (play the "Apple" startup sound at boot and at shutdown)... Let's see if the same file structure is there, or if it has to be implemented differently.

Yes. Same file structure exists... Write a script to play your sound. Must have "full path" to the file you want to play. Put that script in folders '/etc/rc0.d' to play at shutdown, and in '/etc/rc6.d' to play at reboot. Make them executable.

Sample script:
```

#!/bin/bash
## play shutdown sound
/usr/bin/paplay /usr/share/sounds/ubuntu/ringtones/Harmonics.ogg

```
Choose whatever you want played...

On startup sounds, I just add a startup application task in the gui menu at "Startup Applications"...

Have fun.

---

### Post by MAFoElffen on 2023-03-31
I found that ogg123 is part of package vorbis-tools, and will play .ogg sound files from the commandline, so this here will work
```

ogg123 -K 3 -q /usr/share/sounds/ubuntu/ringtones/Ubuntu.ogg

```

---

### Post by MAFoElffen on 2023-04-02
Then if, all you wanted, was to do a system beep / bell, then
```

tput -T "ansi" bel

```

---

### Post by monkeybrain20122 on 2023-04-02
> **MAFoElffen said:**
> I used to do this with Ubuntu 12.04 LTS (play the "Apple" startup sound at boot and at shutdown)... Let's see if the same file structure is there, or if it has to be implemented differently.

Yes. Same file structure exists... Write a script to play your sound. Must have "full path" to the file you want to play. Put that script in folders '/etc/rc0.d' to play at shutdown, and in '/etc/rc6.d' to play at reboot. Make them executable.

Sample script:
```

#!/bin/bash
## play shutdown sound
/usr/bin/paplay /usr/share/sounds/ubuntu/ringtones/Harmonics.ogg

```
Choose whatever you want played...

On startup sounds, I just add a startup application task in the gui menu at "Startup Applications"...

Have fun.

Well I have a startup sound in Ubuntu 22.04, just put this command in startup applications (no script needed)
```

paplay /usr/share/sounds/ubuntu/stereo/desktop-login.ogg
```

I am using unity, for gnome shell you have to create a .desktop file and then  add it to startup applications, I think (GS just makes you do more work for any simple task), using the command above in the Exec= line would work (changing the path to whatever music file)


I have no idea how to make a shut down sound since there is no equivalent to 'startup applications' for shut down.

---

### Post by MAFoElffen on 2023-04-03
On Gnome Sessions, it still has "startup Applications. See attached screenshot.

On shutdown, folder /etc/rc0.d are where the shutdown scripts are, So any executable script in that folder will fire off on shutdown. /etc/rc6.d contains the scripts for reboot.

---

