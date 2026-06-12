---
title: "listen port on denyhost"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by tomzzv3 on 2008-10-01
If i change the port on the ssh do i also have to change the listening port in denyhosts also?

---

### Post by bodhi.zazen on 2008-10-01
Short answer : No

Long answer: Not the last time I used denyhost, what port are you asking about ? I do not recall a listen port in denyhost, only a listen service (sshd), can you post the relevant line form your config file ?

Longer answer : IMO you do not really need denyhost as long as you have secured ssh and are using keys. Disable password logins.

[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

Longest Answer : [[all variants] Intrusion Detection - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=919472")

---

### Post by tomzzv3 on 2008-10-01
i mean that if i change the port from 22 to 5000 do i have to change something in the denyhosts configuration file so that it listens on to connection attempts on port 5000

---

### Post by bodhi.zazen on 2008-10-01
Not that I am aware of, I believe denyhosts monitors your logs and I do not think denyhosts is "listening" on any port (ie I do not think deny hosts is a "server").

---

### Post by SanskritFritz on 2008-10-02
[The DenyHosts FAQ says:]("http://denyhosts.sourceforge.net/faq.html")

How does DenyHosts work?

DenyHosts processes the **sshd server** **log** (typically, this is /var/log/secure, /var/log/auth.log, etc) and determines which hosts have unsuccessfully attempted to gain access to the ssh server.

---

