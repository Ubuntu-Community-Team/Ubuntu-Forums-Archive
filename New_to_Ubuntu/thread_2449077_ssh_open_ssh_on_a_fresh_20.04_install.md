---
title: "ssh open ssh on a fresh 20.04 install"
date: 2020-08-19
forum: New to Ubuntu
---

### Post by vormsty on 2020-08-19
Hello,
I tryed to install open ssh.
I receive an error message that there is already an application listen for port 22.
So, I remove open ssh (sudo apt-get --purge openssh-server)
If I execute the command: lsof -i | grep sshd I see a deamon is listening on port 22 ???
If I execute the ssh client and try to log in (ssh xxx@ip) I receive an access denied all the time.

How can I enable ssh connection ?

Many thanks for your help.
Best regards
Thierry

---

### Post by SeijiSensei on 2020-08-19
Purging the package won't stop a running daemon.  You could run "sudo killall sshd" then reinstall, but I doubt that's the problem.

Run the ssh client with "-vvv" like this

```
ssh -vvv user@host
```

You'll get very detailed debugging information that should help you diagnose the problem.

---

### Post by vormsty on 2020-08-20
Hello,
Thanks for your reply.
After the command "sudo killall sshd"
If I run the command "lsof -i | grep sshd" the result is:


```
root@Nuc-I9:/etc/ssh# sudo killall sshd
root@Nuc-I9:/etc/ssh# lsof -i | grep sshd
sshd      945591            root    3u  IPv4 3919243      0t0  TCP *:ssh (LISTEN)
sshd      945591            root    4u  IPv6 3919244      0t0  TCP *:ssh (LISTEN)
root@Nuc-I9:/etc/ssh# 
```

If I re install the openssh-servr with the command: sudo apt-get install openssh-server
the result is:
```
Job for ssh.service failed because the control process exited with error code.
See "systemctl status ssh.service" and "journalctl -xe" for details.
invoke-rc.d: initscript ssh, action "start" failed.
&#9679; ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/lib/systemd/system/ssh.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Thu 2020-08-20 11:55:34 EDT; 4ms ago
       Docs: man:sshd(8)
             man:sshd_config(5)
    Process: 946492 ExecStartPre=/usr/sbin/sshd -t (code=exited, status=0/SUCCESS)
    Process: 946493 ExecStart=/usr/sbin/sshd -D $SSHD_OPTS (code=exited, status=255/EXCEPTION)
   Main PID: 946493 (code=exited, status=255/EXCEPTION)

Aug 20 11:55:34 Nuc-I9 systemd[1]: Starting OpenBSD Secure Shell server...
Aug 20 11:55:34 Nuc-I9 sshd[946493]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.
Aug 20 11:55:34 Nuc-I9 sshd[946493]: error: Bind to port 22 on :: failed: Address already in use.
Aug 20 11:55:34 Nuc-I9 sshd[946493]: fatal: Cannot bind any address.
Aug 20 11:55:34 Nuc-I9 systemd[1]: ssh.service: Main process exited, code=exited, status=255/EXCEPTION
Aug 20 11:55:34 Nuc-I9 systemd[1]: ssh.service: Failed with result 'exit-code'.
Aug 20 11:55:34 Nuc-I9 systemd[1]: Failed to start OpenBSD Secure Shell server.
dpkg: erreur de traitement du paquet openssh-server (--configure)*:
 installed openssh-server package post-installation script subprocess returned error exit status 1
Traitement des actions différées («*triggers*») pour systemd (245.4-4ubuntu3.2)*...
Traitement des actions différées («*triggers*») pour man-db (2.9.1-1)*...
Traitement des actions différées («*triggers*») pour ufw (0.36-6)*...
Des erreurs ont été rencontrées pendant l'exécution*:
 openssh-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

What can I do ?

Many thanks for your help and best regards
Thierry

---

### Post by SeijiSensei on 2020-08-20
Try rebooting, then reinstall openssh-server.

---

### Post by vormsty on 2020-08-20
I do that and it's ok many thanks !
best regards
Thierry

---

### Post by SeijiSensei on 2020-08-20
Good. Please go to Thread Tools at the top of this page and choose [SOLVED].

---

