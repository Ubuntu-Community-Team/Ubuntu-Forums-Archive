---
title: "Can't get service to start with systemd - fails with (code=exited, status=210/CHROOT)"
date: 2017-09-18
forum: New to Ubuntu
---

### Post by christianhau on 2017-09-18
Hi!

I am running the home automation software HomeSeer on a Ubuntu Server 17.04. What I am attempting is to get HomeSeer started automatically on boot. For this I am trying to use systemd. The problem is that it fails and I would love any pointers on why :)

[COLOR=#000000][FONT=verdana]This is exactly what I have done.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]My setup:[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]homeseer.service created with following command:
[/FONT][/COLOR]```
sudo nano /etc/systemd/system/homeseer.service
```[COLOR=#000000][FONT=verdana]

[/FONT][/COLOR][COLOR=#000000][FONT=verdana]Content of homeseer.service:
[/FONT][/COLOR]```
[Unit]Description=HomeSeer  HS3 Home Automation Server
After=network.target


[Service]
WorkingDirectory=/home/christian/HomeSeer
ExecStart=/usr/bin/mono /home/christian/HomeSeer/HSConsole.exe --log
Restart=on-failure
TimeoutStopSec=90


[Install]

WantedBy=multi-user.target
```[COLOR=#000000][FONT=verdana]

[/FONT][/COLOR][COLOR=#000000][FONT=verdana]Enabling the service went ok with following command:
[/FONT][/COLOR]```
systemctl enable homeseer.service
```[COLOR=#000000][FONT=verdana]

I can then start the service with which starts HomeSeer and everything works:
[/FONT][/COLOR]```
systemctl start homeseer.service
```[COLOR=#000000][FONT=verdana]

But when I boot up the system HomeSeer doesn't start up and the following is the output of "systemctl status homeseer.service":
[/FONT][/COLOR]```
christian@homeseer:/$ systemctl status homeseer.service&#9679; homeseer.service - HomeSeer
   Loaded: loaded (/etc/systemd/system/homeseer.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Tue 2017-09-19 06:25:06 CEST; 7h left
  Process: 1610 ExecStart=/usr/bin/mono /home/christian/HomeSeer/HSConsole.exe --log (code=exited, status=210/CHROOT)
 Main PID: 1610 (code=exited, status=210/CHROOT)
      CPU: 0


Sep 19 06:25:06 homeseer systemd[1]: homeseer.service: Failed with result 'exit-code'.
Sep 19 06:25:06 homeseer systemd[1]: homeseer.service: Service hold-off time over, scheduling restart.
Sep 19 06:25:06 homeseer systemd[1]: Stopped HomeSeer.
Sep 19 06:25:06 homeseer systemd[1]: homeseer.service: Start request repeated too quickly.
Sep 19 06:25:06 homeseer systemd[1]: Failed to start HomeSeer.
Sep 19 06:25:06 homeseer systemd[1]: homeseer.service: Unit entered failed state.
Sep 19 06:25:06 homeseer systemd[1]: homeseer.service: Failed with result 'exit-code'.



```[COLOR=#000000][FONT=verdana]

[/FONT][/COLOR]

---

