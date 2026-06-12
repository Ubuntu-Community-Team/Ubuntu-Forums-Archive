---
title: "SSH fails with 'Port 22: Connection refused'"
date: 2013-01-28
forum: New to Ubuntu
---

### Post by mworkman12 on 2013-01-28
I have setup 4 Ubuntu machines: 1 client and 3 nodes.  I have successfully ssh-copy-id from the client to 2 of the nodes.  The third node keeps giving me the Port 22 error.  I even deleted the failing node and then cloned it from one of the working nodes.



I am using Ubuntu 12.04.1 on Virtual Box.  No modifications to SSH or SSHD were made.  ps ax | grep ssh gives:

root@Ubuntu-VirtualBox:/var/log# ps ax | grep ssh
  781 ?        Ss     0:00 /usr/sbin/sshd -D
 1409 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session gnome-session --session=ubuntu
 2207 pts/2    S+     0:00 grep --color=auto ssh
root@Ubuntu-VirtualBox:/var/log# 

so the ssh server seems to be running.  Firewall is disabled.  I'm not seeing anything in /var/log/auth.log.

Any help would be appreciated.

Thanks.

---

### Post by ghost1227 on 2013-01-28
Given that you're logged in as root, I'm going to assume you're trying to SSH as root as well. By default on Ubuntu (and most other distros) this is disabled as a security measure. To enable it, edit /etc/ssh/sshd_config and find this:

```
#PermitRootLogin yes
```

Uncomment it and restart sshd. On my installation, it's at line 42.

---

### Post by prodigy_ on 2013-01-28
On the server you can check if the SSH service is listening on port 22 with ```
netstat -atun|grep ':22'
``` command. On the client you can telnet the server to see whether the port is open: ```
telnet ssh.ser.ver.ip 22
```

---

