---
title: "Suspicious things in auth log"
date: 2018-10-17
forum: New to Ubuntu
---

### Post by %7#28K8 on 2018-10-17
Hello, I want to ask on what just happened and what does these means? I was alarmed by auth could not identify password and I think I'm being attacked. Earlier, I keep on encountering webpages not loading incompletely nor properly. After searching about it, I suspect that I have DNS cache poisoning but wasn't too sure. Although I did check my DNS cache and it was 700+. I've also found about the SIGHUP restarting because either something or someone changed the configuration and I don't know about it nor how to do it.

Anyway about the log, I thought the SIGHUP was caused by my putting a Google DNS but the SIGHUPs occured earlier than that and I would like to know what does this mean and what's happening.

I had installed Ubuntu using a USB on a formerly Windows laptop.

```
Oct 18 04:46:38 ubuntu-dynabook-Satellite-L20-253E-W sudo:   ubuntu : TTY=pts/0 ; PWD=/home/ubuntu ; USER=root ; COMMAND=/usr/bin/systemd-resolve --statisticsOct 18 04:46:40 ubuntu-dynabook-Satellite-L20-253E-W sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
Oct 18 04:46:40 ubuntu-dynabook-Satellite-L20-253E-W sudo: pam_unix(sudo:session): session closed for user root
Oct 18 05:11:41 ubuntu-dynabook-Satellite-L20-253E-W dbus-daemon[804]: [system] Failed to activate service 'org.freedesktop.nm_dispatcher': timed out (service_start_timeout=25000ms)
Oct 18 05:11:41 ubuntu-dynabook-Satellite-L20-253E-W dbus-daemon[804]: [system] Failed to activate service 'org.freedesktop.nm_dispatcher': timed out (service_start_timeout=25000ms)
Oct 18 05:13:57 ubuntu-dynabook-Satellite-L20-253E-W sshd[958]: Received SIGHUP; restarting.
Oct 18 05:13:57 ubuntu-dynabook-Satellite-L20-253E-W sshd[958]: Server listening on 0.0.0.0 port 22.
Oct 18 05:13:57 ubuntu-dynabook-Satellite-L20-253E-W sshd[958]: Server listening on :: port 22.
Oct 18 05:17:01 ubuntu-dynabook-Satellite-L20-253E-W CRON[14776]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 18 05:17:01 ubuntu-dynabook-Satellite-L20-253E-W CRON[14776]: pam_unix(cron:session): session closed for user root
Oct 18 05:22:28 ubuntu-dynabook-Satellite-L20-253E-W sshd[958]: Received SIGHUP; restarting.
Oct 18 05:22:28 ubuntu-dynabook-Satellite-L20-253E-W sshd[958]: Server listening on 0.0.0.0 port 22.
Oct 18 05:22:28 ubuntu-dynabook-Satellite-L20-253E-W sshd[958]: Server listening on :: port 22.
Oct 18 06:14:01 ubuntu-dynabook-Satellite-L20-253E-W sshd[958]: Received SIGHUP; restarting.
Oct 18 06:14:01 ubuntu-dynabook-Satellite-L20-253E-W sshd[958]: Server listening on 0.0.0.0 port 22.
Oct 18 06:14:01 ubuntu-dynabook-Satellite-L20-253E-W sshd[958]: Server listening on :: port 22.
Oct 18 06:16:39 ubuntu-dynabook-Satellite-L20-253E-W sudo: pam_unix(sudo:auth): conversation failed
Oct 18 06:16:39 ubuntu-dynabook-Satellite-L20-253E-W sudo: pam_unix(sudo:auth): auth could not identify password for [ubuntu]
Oct 18 06:17:01 ubuntu-dynabook-Satellite-L20-253E-W CRON[17378]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 18 06:17:01 ubuntu-dynabook-Satellite-L20-253E-W CRON[17378]: pam_unix(cron:session): session closed for user root
Oct 18 06:25:01 ubuntu-dynabook-Satellite-L20-253E-W CRON[17686]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 18 06:25:01 ubuntu-dynabook-Satellite-L20-253E-W CRON[17686]: pam_unix(cron:session): session closed for user root
Oct 18 06:27:49 ubuntu-dynabook-Satellite-L20-253E-W sshd[958]: Received SIGHUP; restarting.
Oct 18 06:27:49 ubuntu-dynabook-Satellite-L20-253E-W sshd[958]: Server listening on 0.0.0.0 port 22.
Oct 18 06:27:49 ubuntu-dynabook-Satellite-L20-253E-W sshd[958]: Server listening on :: port 22.
Oct 18 06:27:49 ubuntu-dynabook-Satellite-L20-253E-W sshd[958]: Received SIGHUP; restarting.
Oct 18 06:27:49 ubuntu-dynabook-Satellite-L20-253E-W sshd[958]: Server listening on 0.0.0.0 port 22.
Oct 18 06:27:49 ubuntu-dynabook-Satellite-L20-253E-W sshd[958]: Server listening on :: port 22.
Oct 18 06:42:01 ubuntu-dynabook-Satellite-L20-253E-W sshd[958]: Received SIGHUP; restarting.
Oct 18 06:42:01 ubuntu-dynabook-Satellite-L20-253E-W sshd[958]: Server listening on 0.0.0.0 port 22.
Oct 18 06:42:01 ubuntu-dynabook-Satellite-L20-253E-W sshd[958]: Server listening on :: port 22.
Oct 18 06:55:05 ubuntu-dynabook-Satellite-L20-253E-W sshd[958]: Received SIGHUP; restarting.
Oct 18 06:55:05 ubuntu-dynabook-Satellite-L20-253E-W sshd[958]: Server listening on 0.0.0.0 port 22.
Oct 18 06:55:05 ubuntu-dynabook-Satellite-L20-253E-W sshd[958]: Server listening on :: port 22.
Oct 18 07:08:10 ubuntu-dynabook-Satellite-L20-253E-W sudo: pam_unix(sudo:auth): conversation failed
Oct 18 07:08:10 ubuntu-dynabook-Satellite-L20-253E-W sudo: pam_unix(sudo:auth): auth could not identify password for [ubuntu]
Oct 18 07:16:30 ubuntu-dynabook-Satellite-L20-253E-W sudo: pam_unix(sudo:auth): conversation failed
Oct 18 07:16:30 ubuntu-dynabook-Satellite-L20-253E-W sudo: pam_unix(sudo:auth): auth could not identify password for [ubuntu]
Oct 18 07:17:01 ubuntu-dynabook-Satellite-L20-253E-W CRON[21773]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 18 07:17:01 ubuntu-dynabook-Satellite-L20-253E-W CRON[21773]: pam_unix(cron:session): session closed for user root
Oct 18 07:30:01 ubuntu-dynabook-Satellite-L20-253E-W CRON[22175]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 18 07:30:01 ubuntu-dynabook-Satellite-L20-253E-W CRON[22175]: pam_unix(cron:session): session closed for user root
```

Also here's my last commandline

```
ubuntu   :0           :0               Thu Oct 18 02:01   still logged inreboot   system boot  4.15.0-36-generi Thu Oct 18 01:59   still running
ubuntu   :0           :0               Wed Oct 17 20:07 - down   (04:41)
reboot   system boot  4.15.0-29-generi Wed Oct 17 20:06 - 00:48  (04:42)
ubuntu   :0           :0               Wed Oct 17 20:02 - 20:05  (00:03)
reboot   system boot  4.15.0-29-generi Wed Oct 17 20:00 - 20:05  (00:04)

```

Am I being attacked or hacked?

EDIT: Just found this in the last commandline, didn't see it earlier
```
wtmp begins Wed Oct 17 20:00:59 2018
```

---

### Post by %7#28K8 on 2018-10-18
Hello, I think I made a mistake in my first post and it's title should have been suspicious things in auth log instead of SIGHUP, but anyway, I was alarmed by what I found and would like to know what's happening in my logs.

```
Oct 19 01:24:39 ubuntu-dynabook-Satellite-L20-253E-W pkexec: pam_unix(polkit-1:session): session opened for user root by (uid=1000)Oct 19 01:24:39 ubuntu-dynabook-Satellite-L20-253E-W pkexec[2493]: ubuntu: Executing command [USER=root] [TTY=unknown] [CWD=/home/ubuntu] [COMMAND=/usr/lib/update-notifier/package-system-locked]
Oct 19 02:04:36 ubuntu-dynabook-Satellite-L20-253E-W sshd[1018]: Received SIGHUP; restarting.
Oct 19 02:04:36 ubuntu-dynabook-Satellite-L20-253E-W sshd[1018]: Server listening on 0.0.0.0 port 22.
Oct 19 02:04:36 ubuntu-dynabook-Satellite-L20-253E-W sshd[1018]: Server listening on :: port 22.
Oct 19 02:05:37 ubuntu-dynabook-Satellite-L20-253E-W pkexec: pam_unix(polkit-1:session): session opened for user root by (uid=1000)
Oct 19 02:05:37 ubuntu-dynabook-Satellite-L20-253E-W pkexec[4224]: ubuntu: Executing command [USER=root] [TTY=unknown] [CWD=/home/ubuntu] [COMMAND=/usr/lib/update-notifier/package-system-locked]
Oct 19 02:17:01 ubuntu-dynabook-Satellite-L20-253E-W CRON[4556]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 19 02:17:02 ubuntu-dynabook-Satellite-L20-253E-W CRON[4556]: pam_unix(cron:session): session closed for user root
Oct 19 02:35:23 ubuntu-dynabook-Satellite-L20-253E-W sudo:   ubuntu : TTY=pts/0 ; PWD=/home/ubuntu ; USER=root ; COMMAND=/etc/init.d/dns-clean restart
Oct 19 02:35:23 ubuntu-dynabook-Satellite-L20-253E-W sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
Oct 19 02:35:23 ubuntu-dynabook-Satellite-L20-253E-W sudo: pam_unix(sudo:session): session closed for user root
Oct 19 02:35:31 ubuntu-dynabook-Satellite-L20-253E-W sudo:   ubuntu : TTY=pts/0 ; PWD=/home/ubuntu ; USER=root ; COMMAND=/etc/init.d/networking force-reload
Oct 19 02:35:31 ubuntu-dynabook-Satellite-L20-253E-W sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
Oct 19 02:35:32 ubuntu-dynabook-Satellite-L20-253E-W sudo: pam_unix(sudo:session): session closed for user root
Oct 19 02:35:58 ubuntu-dynabook-Satellite-L20-253E-W sudo:   ubuntu : TTY=pts/0 ; PWD=/home/ubuntu ; USER=root ; COMMAND=/usr/bin/systemd-resolve --statistics
Oct 19 02:35:58 ubuntu-dynabook-Satellite-L20-253E-W sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
Oct 19 02:35:58 ubuntu-dynabook-Satellite-L20-253E-W sudo: pam_unix(sudo:session): session closed for user root
Oct 19 02:36:33 ubuntu-dynabook-Satellite-L20-253E-W sudo: pam_unix(sudo:auth): authentication failure; logname= uid=1000 euid=0 tty=/dev/pts/0 ruser=ubuntu rhost=  user=ubuntu
Oct 19 02:36:38 ubuntu-dynabook-Satellite-L20-253E-W sudo:   ubuntu : TTY=pts/0 ; PWD=/home/ubuntu ; USER=root ; COMMAND=/usr/bin/dpkg --verify
Oct 19 02:36:38 ubuntu-dynabook-Satellite-L20-253E-W sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
Oct 19 02:39:41 ubuntu-dynabook-Satellite-L20-253E-W sshd[1018]: Received SIGHUP; restarting.
Oct 19 02:39:41 ubuntu-dynabook-Satellite-L20-253E-W sshd[1018]: Server listening on 0.0.0.0 port 22.
Oct 19 02:39:41 ubuntu-dynabook-Satellite-L20-253E-W sshd[1018]: Server listening on :: port 22.
Oct 19 02:44:53 ubuntu-dynabook-Satellite-L20-253E-W sudo: pam_unix(sudo:session): session closed for user root
Oct 19 03:17:01 ubuntu-dynabook-Satellite-L20-253E-W CRON[6383]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 19 03:17:01 ubuntu-dynabook-Satellite-L20-253E-W CRON[6383]: pam_unix(cron:session): session closed for user root
Oct 19 04:17:02 ubuntu-dynabook-Satellite-L20-253E-W CRON[7196]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 19 04:17:02 ubuntu-dynabook-Satellite-L20-253E-W CRON[7196]: pam_unix(cron:session): session closed for user root
Oct 19 05:17:01 ubuntu-dynabook-Satellite-L20-253E-W CRON[8705]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 19 05:17:02 ubuntu-dynabook-Satellite-L20-253E-W CRON[8705]: pam_unix(cron:session): session closed for user root
Oct 19 05:47:10 ubuntu-dynabook-Satellite-L20-253E-W sshd[1018]: Received SIGHUP; restarting.
Oct 19 05:47:10 ubuntu-dynabook-Satellite-L20-253E-W sshd[1018]: Server listening on 0.0.0.0 port 22.
Oct 19 05:47:10 ubuntu-dynabook-Satellite-L20-253E-W sshd[1018]: Server listening on :: port 22.
Oct 19 06:17:01 ubuntu-dynabook-Satellite-L20-253E-W CRON[10156]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 19 06:17:01 ubuntu-dynabook-Satellite-L20-253E-W CRON[10156]: pam_unix(cron:session): session closed for user root
Oct 19 06:21:29 ubuntu-dynabook-Satellite-L20-253E-W pkexec: pam_unix(polkit-1:session): session opened for user root by (uid=1000)
Oct 19 06:21:29 ubuntu-dynabook-Satellite-L20-253E-W pkexec[10492]: ubuntu: Executing command [USER=root] [TTY=unknown] [CWD=/home/ubuntu] [COMMAND=/usr/lib/update-notifier/package-system-locked]
Oct 19 06:25:01 ubuntu-dynabook-Satellite-L20-253E-W CRON[10618]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 19 06:25:01 ubuntu-dynabook-Satellite-L20-253E-W CRON[10618]: pam_unix(cron:session): session closed for user root
Oct 19 07:17:01 ubuntu-dynabook-Satellite-L20-253E-W CRON[11573]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 19 07:17:01 ubuntu-dynabook-Satellite-L20-253E-W CRON[11573]: pam_unix(cron:session): session closed for user root
Oct 19 07:30:01 ubuntu-dynabook-Satellite-L20-253E-W CRON[12051]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 19 07:30:01 ubuntu-dynabook-Satellite-L20-253E-W CRON[12051]: pam_unix(cron:session): session closed for user root
Oct 19 08:17:01 ubuntu-dynabook-Satellite-L20-253E-W CRON[13214]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 19 08:17:01 ubuntu-dynabook-Satellite-L20-253E-W CRON[13214]: pam_unix(cron:session): session closed for user root
Oct 19 09:17:02 ubuntu-dynabook-Satellite-L20-253E-W CRON[14312]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 19 09:17:02 ubuntu-dynabook-Satellite-L20-253E-W CRON[14312]: pam_unix(cron:session): session closed for user root
Oct 19 09:31:09 ubuntu-dynabook-Satellite-L20-253E-W sshd[1018]: Received SIGHUP; restarting.
Oct 19 09:31:09 ubuntu-dynabook-Satellite-L20-253E-W sshd[1018]: Server listening on 0.0.0.0 port 22.
Oct 19 09:31:09 ubuntu-dynabook-Satellite-L20-253E-W sshd[1018]: Server listening on :: port 22.
Oct 19 09:46:45 ubuntu-dynabook-Satellite-L20-253E-W polkitd(authority=local): Operator of unix-session:2 FAILED to authenticate to gain authorization for action org.gtk.vfs.file-operations-helper for unix-process:15484:3049892 [/bin/sh -c pkexec /usr/lib/gvfs/gvfsd-admin "$@" --address $DBUS_SESSION_BUS_ADDRESS gvfsd-admin --spawner :1.22 /org/gtk/gvfs/exec_spaw/4] (owned by unix-user:ubuntu)
Oct 19 09:46:45 ubuntu-dynabook-Satellite-L20-253E-W pkexec[15485]: ubuntu: Error executing command as another user: Request dismissed [USER=root] [TTY=unknown] [CWD=/home/ubuntu] [COMMAND=/usr/lib/gvfs/gvfsd-admin --spawner :1.22 /org/gtk/gvfs/exec_spaw/4 --address unix:path=/run/user/1000/bus]
```

Thank you.

---

### Post by oldos2er on 2018-10-18
Threads merged.

---

