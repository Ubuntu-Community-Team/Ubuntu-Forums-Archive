---
title: "running installed snap app in 20,04"
date: 2021-12-21
forum: New to Ubuntu
---

### Post by rburkartjo on 2021-12-21
trying to run the gnome-schedule app
ray@ray-HP-ProBook-640-G1:~$ snap list
Name               Version             Rev    Tracking         Publisher   Notes
bare               1.0                 5      latest/stable    canonical&#10003;  base
core18             20211028            2253   latest/stable    canonical&#10003;  base
core20             20211129            1270   latest/stable    canonical&#10003;  base
gnome-3-34-1804    0+git.3556cb3       77     latest/stable/…  canonical&#10003;  -
gnome-3-38-2004    0+git.cd626d1       87     latest/stable    canonical&#10003;  -
gnome-schedule     0.1                 19     latest/edge      webmenow    devmode
gtk-common-themes  0.1-59-g7bca6ae     1519   latest/stable/…  canonical&#10003;  -
snap-store         3.38.0-66-gbd5b8f7  558    latest/stable/…  canonical&#10003;  -
snapd              2.53.4              14295  latest/stable    canonical&#10003;  snapd
ray@ray-HP-ProBook-640-G1:~$ 
any ideas /tks

---

### Post by deadflowr on 2021-12-21
[s]Is there no icon to launch it?
Or does it require running from a terminal.
Terminal command would probably be
```
snap run gnome-schedule
```[/s]

Revising after looking it over.

I decided to try and install it and it's output was this:
```
snap install gnome-schedule --edge
error: The publisher of snap "gnome-schedule" has indicated that they do not consider this revision
       to be of production quality and that it is only meant for development or testing at this
       point. As a consequence this snap will not refresh automatically and may perform arbitrary
       system changes outside of the security sandbox snaps are generally confined to, which may
       put your system at risk.

       If you understand and want to proceed repeat the command including --devmode; if instead you
       want to install the snap forcing it into strict confinement repeat the command including
       --jailmode.
```

So if there are issues then it makes sense as the app is not even considered worthy by the packager.

On top of that it hasn't been updated in over 2 years now.

---

### Post by rburkartjo on 2021-12-21
yea dead i got the samething. just playing with snap and trying to ruin some snaps/tks

---

### Post by deadflowr on 2021-12-21
> trying to ruin some snaps/tks

Don't know what that means, but okay.
Spelling error?

---

### Post by rburkartjo on 2021-12-21
dead my bad should say run

---

