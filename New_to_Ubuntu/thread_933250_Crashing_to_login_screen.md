---
title: "Crashing to login screen"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by psychomichael on 2008-09-29
This happened twice today. I was browsing in Firefox and running BitTorrent in the background while editing a photo with GIMP and the screen went black and went to my login screen. This usually happens once a week at least, but this is the first time it happened twice in just a few minutes.

I have 2.5GB of RAM and am using a dual-core processor, so that shouldn't be a problem.

At 9:16 and 9:20, See this: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0

Here's my whole syslog:
Sep 29 07:36:47 darkmage syslogd 1.4.1#21ubuntu3: restart.
Sep 29 07:36:47 darkmage anacron[15259]: Job `cron.daily' terminated
Sep 29 07:45:01 darkmage anacron[15259]: Job `cron.monthly' started
Sep 29 07:45:01 darkmage anacron[15448]: Updated timestamp for job `cron.monthly' to 2008-09-29
Sep 29 07:49:04 darkmage anacron[15259]: Job `cron.monthly' terminated
Sep 29 07:49:04 darkmage anacron[15259]: Normal exit (2 jobs run)
Sep 29 07:59:10 darkmage -- MARK --
Sep 29 08:17:01 darkmage /USR/SBIN/CRON[26073]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 29 08:39:11 darkmage -- MARK --
Sep 29 08:59:11 darkmage -- MARK --
Sep 29 09:16:51 darkmage gdm[12485]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Sep 29 09:17:01 darkmage /USR/SBIN/CRON[26622]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 29 09:17:01 darkmage gdm[26597]: WARNING: Login sound requested on non-local display or the play software cannot be run or the sound does not exist. 
Sep 29 09:17:03 darkmage hcid[5514]: Default passkey agent (:1.74, /org/bluez/passkey) registered
Sep 29 09:17:03 darkmage hcid[5514]: Default authorization agent (:1.74, /org/bluez/auth) registered
Sep 29 09:17:04 darkmage NetworkManager: <info>  Updating allowed wireless network lists. 
Sep 29 09:17:04 darkmage NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Sep 29 09:20:52 darkmage gdm[26597]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Sep 29 09:21:01 darkmage gdm[27021]: WARNING: Login sound requested on non-local display or the play software cannot be run or the sound does not exist. 
Sep 29 09:21:02 darkmage hcid[5514]: Default passkey agent (:1.86, /org/bluez/passkey) registered
Sep 29 09:21:02 darkmage hcid[5514]: Default authorization agent (:1.86, /org/bluez/auth) registered
Sep 29 09:21:03 darkmage NetworkManager: <info>  Updating allowed wireless network lists. 
Sep 29 09:21:03 darkmage NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Sep 29 09:39:12 darkmage -- MARK --

---

### Post by psychomichael on 2008-09-29
Also...maybe unrelated, but unresolved:
[http://ubuntuforums.org/showthread.php?t=923720](http://ubuntuforums.org/showthread.php?t=923720)

Now I have NO sound whatsoever...and I noticed that it was noted in the syslog above at 9:17:01

---

