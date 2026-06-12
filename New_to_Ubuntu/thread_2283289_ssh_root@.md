---
title: "ssh root@"
date: 2015-06-20
forum: New to Ubuntu
---

### Post by mlnease on 2015-06-20
Hello,

I'm following a tutorial for 'Initial Server Setup' preparatory to configuring WordPress.  One step is ```
ssh root@[my IP address]
``` which is meant to return ```
The authenticity of host '69.55.55.20 (69.55.55.20)' can't be established. ECDSA key fingerprint is [...]. Are you sure you want to continue connecting (yes/no)?
``` Instead it returns ```
ssh: connect to host [my IP address] port 22: Connection refused
```

Can anyone please tell me what I'm doing wrong?

Thanks in advance.

---

### Post by CharlesA on 2015-06-20
Do you have openssh-server installed on the machine you are trying to connect to?

Also: It is usually unwise to log in as root. A better way to do it is to ssh in as a not root user and then use su or sudo to gain root privileges.

If you are going to run an SSH server, it is also a good idea to disable password authentication and use keys instead. See here:
[https://help.ubuntu.com/lts/serverguide/openssh-server.html](https://help.ubuntu.com/lts/serverguide/openssh-server.html)

---

### Post by QIII on 2015-06-20
I'd go so far as to suggest that you ditch the tutorial if it's telling you to ssh as root.  Really, really bad idea.

---

### Post by ajgreeny on 2015-06-20
I am pretty certain that the default /etc/ssh/sshd_config file for the server setup does not allow root connections, but I don't have the server on this machine so can't check.

Definitely not a good idea though, even if it were possible!

---

### Post by mlnease on 2015-06-20
Thanks Charles, I'll have a look and forget about logging on as root.  Actually it was only a one-time root login in the tutorial put I do prefer to err on the side of caution.

---

### Post by mlnease on 2015-06-20
Thanks QIII--I'll take your advice.  Honestly I haven't even figured out yet what it means to 'run an SSH server'--guess I'll look for another tutorial.  I'm just trying to get WordPress up and running on my xubuntu box.

---

### Post by mlnease on 2015-06-20
Thanks ajgreeny--wow, three moderator replies in a matter of minutes.  I'll take that as a Red Alert and back the truck up.

---

### Post by SeijiSensei on 2015-06-20
You cannot log in directly as root by any mechanism on Ubuntu.  You have to log in with a personal identity and execute root commands with sudo.

However you can configure SSH for the root user on the remote machine to accept your personal public key.  I leave this as an exercise ;)

---

### Post by mlnease on 2015-06-20
&#24863;&#35613;&#12398;&#20808;&#29983;,

I will &#33258;&#23429;&#12391;&#32244;&#32722;!

By the way, I did log in as root but don't think I'll do so again.

---

### Post by CharlesA on 2015-06-20
> **SeijiSensei said:**
> You cannot log in directly as root by any mechanism on Ubuntu.  You have to log in with a personal identity and execute root commands with sudo.

However you can configure SSH for the root user on the remote machine to accept your personal public key.  I leave this as an exercise ;)

Thanks for that. Debian Jessie also disallows login as root without a public key, so it makes sense that Ubuntu would handle it similarly.

---

### Post by mastablasta on 2015-06-22
I believe Debian Jessie doesn't have sudo installed by default (at least not the net install version).

you don't actually need SSH order to install wordpress. ssh is only needed if you do not use desktop and have a headless server (but you said you are using xubuntu)

ssh server should be installed, port 22 should be open (though many suggest to move to another port).

just for reference why everyone jumped on so fast - within 6 hours of opening the server to web I started getting automated hacking attempts on user root and then they tried with various passwords.

so the key here is to use keys, and don't forget to add fail to ban. 

after you get wordpress up and running - make sure you install wordfence plugin and probably sucuri plugin as well & disable aministrator. again within hours after opening the site to the web - they tried to hack it. since then steady attempts are made at the server who is blocking and blacklisting the IPs. before I had those plugins installed I got hacked. luckily the damage wasn't too big and I managed to recover the site. but it took a lot of time to recover.

make sure you have some good backups (there is a plugin for that as well, I use Updraft).

---

### Post by mlnease on 2015-06-22
Wow--all very interesting and useful, thanks.

---

