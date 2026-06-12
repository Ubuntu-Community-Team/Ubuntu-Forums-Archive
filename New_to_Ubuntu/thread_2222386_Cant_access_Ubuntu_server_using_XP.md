---
title: "Cant access Ubuntu server using XP"
date: 2014-05-06
forum: New to Ubuntu
---

### Post by erj001 on 2014-05-06
[COLOR=#000000][FONT=verdana]Good morning,[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]I am installing a new server for my company (v14.04 server) and I choosed to use sharings without login (no user/password)
I made several tests and reached a setup I consider fine. I was able to access all the sharings with full permissions with SAMBA.

[/FONT][/COLOR]After that, I started to make several tests, installing and uninstalling some packages, for learning purposes. As this server will play only as NAS, I decided to restart it only with the necessary options.

[FONT=verdana, sans-serif][SIZE=2][COLOR=#000000]I saved the already approved smb.conf and reinstaled the system (reformating the HD). I wanted a clean instalation.[/COLOR][/SIZE][/FONT]

After the instalation was finished, I restored smb.conf and restarted samba. When I tried to connect to server, XP requested user/password. I am sure that the configuration is the same of the first time, and the server only requires the login when I access from MY computer, all the other computer on the network can access shares without login.

[FONT=verdana, sans-serif][SIZE=2][COLOR=#000000]Does anyone have an idea how to fix it?
[/COLOR][/SIZE][/FONT]
Thanks

[COLOR=#000000][FONT=verdana]My smb.conf:[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana][global][/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]    workgroup = MEUGRUPO[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]    server string = Samba Server %v[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]    map to guest = Bad User[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]    security = server    [/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]    encrypt passwords = yes[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]#============================ Share Definitions ==============================[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana][F][/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]    path = /home/f/[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]    comment = unidade f[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]    browseable = yes[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]    public = yes[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]    writable = yes[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]    vfs object = recycle[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]    recycle:repository = lixeira[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]    recycle:keeptree = yes[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]    recycle:versions = yes[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana][G][/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]    path = /home/g/[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]    comment = unidade g[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]    browseable = yes[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]    public = yes[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]    writable = yes[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]    vfs object = recycle[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]    recycle:repository = lixeira[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]    recycle:keeptree = yes[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]    recycle:versions = yes[/FONT][/COLOR]

---

