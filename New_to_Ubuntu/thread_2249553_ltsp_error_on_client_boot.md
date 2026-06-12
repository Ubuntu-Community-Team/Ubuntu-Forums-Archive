---
title: "ltsp error on client boot"
date: 2014-10-23
forum: New to Ubuntu
---

### Post by aor2 on 2014-10-23
Hi I have installed ltsp server on ubuntu 14.04.1 but i have encounter error when client try to boot..here is the error::

I follow the instruction in this link _[https://help.ubuntu.com/community/UbuntuLTSP/FatClients](https://help.ubuntu.com/community/UbuntuLTSP/FatClients)_

please help...

[IMG]http://imageshack.com/a/img538/7566/LoSn5w.png[/IMG]

after that here is the error
[IMG]http://imagizer.imageshack.us/a/img537/2978/Qm9wg2.png[/IMG]


Thanks in advance....

---

### Post by aor2 on 2014-10-23
Hi,

Can somebody share me some answer with this error?

THanks....

---

### Post by laurent6 on 2014-11-05
Hi,

Try to add lts.conf in 
[COLOR=#000000][FONT=Arial][I]/var/lib/tftpboot/ltsp/i386/
whith something like that : 

[/I][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]*################*[/FONT][/COLOR][COLOR=#000000][FONT=Arial][I]
[/I][/FONT][/COLOR][COLOR=#000000][FONT=Arial]*# Section défaut, elle est *[/FONT][/COLOR][COLOR=#000000][FONT=Arial][I]
[/I][/FONT][/COLOR][COLOR=#000000][FONT=Arial]*# commune à tous les clients*[/FONT][/COLOR][COLOR=#000000][FONT=Arial][I]
[/I][/FONT][/COLOR][COLOR=#000000][FONT=Arial]*################*[/FONT][/COLOR][COLOR=#000000][FONT=Arial][I]
[/I][/FONT][/COLOR][COLOR=#000000][FONT=Arial]*[default]*[/FONT][/COLOR][COLOR=#000000][FONT=Arial][I]
[/I][/FONT][/COLOR][COLOR=#000000][FONT=Arial]*    SERVER=192.168.0.1*[/FONT][/COLOR][COLOR=#000000][FONT=Arial][I]
[/I][/FONT][/COLOR][COLOR=#000000][FONT=Arial]*    X_COLOR_DEPTH=16*[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]*    LDM_DIRECTX = True*[/FONT][/COLOR][COLOR=#000000][FONT=Arial][I]
[/I][/FONT][/COLOR][COLOR=#000000][FONT=Arial]*    LOCALDEV=True*[/FONT][/COLOR][COLOR=#000000][FONT=Arial][I]
[/I][/FONT][/COLOR][COLOR=#000000][FONT=Arial]*    SOUND=True*[/FONT][/COLOR][COLOR=#000000][FONT=Arial][I]
[/I][/FONT][/COLOR][COLOR=#000000][FONT=Arial]*    NBD_SWAP=True*[/FONT][/COLOR][COLOR=#000000][FONT=Arial][I]
[/I][/FONT][/COLOR][COLOR=#000000][FONT=Arial]*    SYSLOG_HOST=server*[/FONT][/COLOR][COLOR=#000000][FONT=Arial][I]
[/I][/FONT][/COLOR][COLOR=#000000][FONT=Arial]*    XKBLAYOUT=fr*[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]*    SCREEN_02=shell*[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][I]    SCREEN_07=ldm

Of course change setup for your needs.

And don't forget to restart server (just in case some update with NBD server doesn't match)

[/I][/FONT][/COLOR]

[COLOR=#000000][FONT=Arial][I]

[/I][/FONT][/COLOR]

---

