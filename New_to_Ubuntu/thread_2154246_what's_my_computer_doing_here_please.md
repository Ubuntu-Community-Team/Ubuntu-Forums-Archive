---
title: "what's my computer doing here please?"
date: 2013-06-14
forum: New to Ubuntu
---

### Post by donster on 2013-06-14
hi

i have a raspberry pi set up with a couple of cameras. there was a problem with the wifi dropping out and it would not reconnect so i found a cron job online which seems to be working. i was just checking my logs (sudo nano /var/log/syslog) and there are some IP addresses that i do not recognize. i was wondering if anyone could please tell me what my little Pi is up to and what these addresses might be?

[INDENT][FONT=arial]Jun 14 07:20:46 raspberrypi dhclient:[/FONT][/INDENT]
[INDENT][FONT=arial]Jun 14 07:20:46 raspberrypi dhclient: Listening on LPF/wlan0/00:87:24:83:35:c2[/FONT][/INDENT]
[INDENT][FONT=arial]Jun 14 07:20:46 raspberrypi dhclient: Sending on   LPF/wlan0/00:87:24:83:35:c2[/FONT][/INDENT]
[INDENT][FONT=arial]Jun 14 07:20:46 raspberrypi dhclient: Sending on   Socket/fallback[/FONT][/INDENT]
[INDENT][FONT=arial]Jun 14 07:20:46 raspberrypi dhclient: DHCPRELEASE on wlan0 to 192.168.1.1 port 67[/FONT][/INDENT]
[INDENT][FONT=arial]Jun 14 07:20:47 raspberrypi ifplugd(wlan0)[1600]: Link beat lost.[/FONT][/INDENT]
[INDENT][FONT=arial]Jun 14 07:20:47 raspberrypi wpa_supplicant[1686]: wlan0: SME: Trying to authenticate with 89:53:d4:50:c7:90 (SSID='mywirelessnetwork' freq=2442 MHz)[/FONT][/INDENT]
[INDENT][FONT=arial]Jun 14 07:20:47 raspberrypi wpa_supplicant[1686]: wlan0: SME: Authentication request to the driver failed[/FONT][/INDENT]
[INDENT][FONT=arial]Jun 14 07:20:47 raspberrypi wpa_action: removing sendsigs omission pidfile: /run/sendsigs.omit.d/wpasupplicant.wpa_supplicant.wlan0.pid[/FONT][/INDENT]
[INDENT][FONT=arial]Jun 14 07:20:49 raspberrypi ntpd[2240]: Deleting interface #2 wlan0, 192.168.1.11#123, interface stats: received=641, sent=642, dropped=0, active_tim$[/FONT][/INDENT]
[INDENT][FONT=arial]Jun 14 07:20:49 raspberrypi ntpd[2240]: [COLOR=#0000CD]193.190.147.153[/COLOR] interface 192.168.1.11 -> (none)[/FONT][/INDENT]
[INDENT][FONT=arial]Jun 14 07:20:49 raspberrypi ntpd[2240]: [COLOR=#0000CD]212.19.47.108[/COLOR] interface 192.168.1.11 -> (none)[/FONT][/INDENT]
[INDENT][FONT=arial]Jun 14 07:20:49 raspberrypi ntpd[2240]: [COLOR=#0000CD]193.238.80.20[/COLOR] interface 192.168.1.11 -> (none)[/FONT][/INDENT]
[INDENT][FONT=arial]Jun 14 07:20:49 raspberrypi ntpd[2240]: [COLOR=#0000CD]193.224.45.106[/COLOR] interface 192.168.1.11 -> (none)[/FONT][/INDENT]
[INDENT][FONT=arial]Jun 14 07:20:49 raspberrypi ntpd[2240]: peers refreshed[/FONT][/INDENT]
[INDENT][FONT=arial]Jun 14 07:20:49 raspberrypi wpa_supplicant[1686]: wlan0: SME: Trying to authenticate with 89:53:d4:50:c7:90 (SSID='mywirelessnetwork' freq=2442 MHz)[/FONT][/INDENT]
[INDENT][FONT=arial]Jun 14 07:20:49 raspberrypi kernel: [86710.832104] wlan0: authenticate with 89:53:d4:50:c7:90

[/FONT][/INDENT]
[FONT=arial]Thank you or any help.
Don[/FONT]

---

### Post by matt_symes on 2013-06-14
Hi

> [FONT=arial]**ntpd**[2240]: [COLOR=#0000CD]193.190.147.153[/COLOR][/FONT]

ntpd is the network time protocol daemon.

It sets the time on the raspery pi by getting the time from servers on  the internet.

I suspect those ip addresses are time servers but you can double check.

Kind regards

---

### Post by donster on 2013-06-14
great, thanks.

---

### Post by NikTh on 2013-06-14
If the problem solved, please mark the thread as solved (see at my signature). 

Thanks

---

