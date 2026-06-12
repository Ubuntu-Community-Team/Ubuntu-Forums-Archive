---
title: "Switching to Pipewire on Ubuntu 22.04"
date: 2023-01-30
forum: New to Ubuntu
---

### Post by nm2 on 2023-01-30
I read Ubuntu 22.10 has switched to Pipewire as default, Is there any easy way of doing this on Ubuntu 22.04? Is it worth doing early or should I wait until the next LTS release to use Pipewire?

---

### Post by #&amp;thj^% on 2023-01-30
You might be using it now, check:
```
systemctl --user status pipewire
```

---

### Post by Bashing-om on 2023-01-30
Hello nm2 - Welcome to the forums :D

I did the convert on my 22.04 with no issues:
> 
<snip>
sysop@x2204mini:~$ pactl info
Server Name: PulseAudio (on PipeWire 0.3.48)
<snip>


As per the tutorial:
[https://ubuntuhandbook.org/index.php/2022/04/pipewire-replace-pulseaudio-ubuntu-2204/](https://ubuntuhandbook.org/index.php/2022/04/pipewire-replace-pulseaudio-ubuntu-2204/)

[INDENT]Ubuntu - together we do
[/INDENT]

---

### Post by #&amp;thj^% on 2023-01-30
> **Bashing-om said:**
> Hello nm2 - Welcome to the forums :D

I did the convert on my 22.04 with no issues:


As per the tutorial:
[https://ubuntuhandbook.org/index.php/2022/04/pipewire-replace-pulseaudio-ubuntu-2204/](https://ubuntuhandbook.org/index.php/2022/04/pipewire-replace-pulseaudio-ubuntu-2204/)

[INDENT]Ubuntu - together we do
[/INDENT]
+1
That's a good one to follow. :)

---

### Post by nm2 on 2023-01-30
It says it is active

> 
&#9679; pipewire.service - PipeWire Multimedia Service
     Loaded: loaded (/usr/lib/systemd/user/pipewire.service; enabled; vendor preset: enabled)
     Active: active (running) since Mon 2023-01-30 14:49:01 EST; 5h 51min ago
TriggeredBy: &#9679; pipewire.socket
   Main PID: 1760 (pipewire)
      Tasks: 2 (limit: 38342)
     Memory: 1.5M
        CPU: 59ms
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/pipewire.service
             &#9492;&#9472;1760 /usr/bin/pipewire

Jan 30 14:49:01 MS-7C56 systemd[1753]: Started PipeWire Multimedia Service.

---

### Post by nm2 on 2023-01-30
> **Bashing-om said:**
> 
As per the tutorial:
[https://ubuntuhandbook.org/index.php/2022/04/pipewire-replace-pulseaudio-ubuntu-2204/](https://ubuntuhandbook.org/index.php/2022/04/pipewire-replace-pulseaudio-ubuntu-2204/)
[INDENT]Ubuntu - together we do
[/INDENT]


Thanks I'll try this.

---

