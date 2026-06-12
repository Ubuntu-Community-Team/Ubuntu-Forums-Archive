---
title: "suddenly cant connect to ssh"
date: 2013-06-01
forum: New to Ubuntu
---

### Post by spilner on 2013-06-01
hi,im running ubuntu server.i can connect to ssh normally today but suddenly it wont let me connect but i still can access via ftp.
i dont touch or modify anything.
i use putty to login and it says "Server unexpectedly closed network connection".
i reboot the server but still out of luck.
can anyone help ?

---

### Post by 2F4U on 2013-06-01
Since you seem to be able to have direct access to the server, can you check whether the SSH service is running? Also, can you check the log files on the server if the SSH service has written any error messages?

---

### Post by HermanAB on 2013-06-01
Debug the problem on the server itself:
$ ssh -vvv user@localhost

---

### Post by spilner on 2013-06-01
i use ssh -vvv root@localhost still not working after reboot :(

---

### Post by spilner on 2013-06-01
2f4u,i already start the ssh but still not working at all :(
can someone help?

---

### Post by Lars Noodén on 2013-06-01
On the server what is the output of these following utilities?  They check to see if sshd is running.

```

service ssh status
pgrep -lf sshd
sudo netstat -ntlp | grep :22

```

On the client, what is the output of [ssh](http://manpages.ubuntu.com/manpages/raring/en/man1/ssh.1.html) when you run it with **-vvv** to a normal user not root?

---

### Post by spilner on 2013-06-01
root@rescue:/# service ssh status
sshd is running.

root@rescue:/# pgrep -lf sshd
4316 /usr/sbin/sshd
4703 sshd: root@pts/1

root@rescue:/# sudo netstat -ntlp | grep :22
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      4316/sshd       
tcp6       0      0 :::22                   :::*                    LISTEN      4316/sshd 

above is the output.
i dont create user yet,only use root.

---

### Post by Lars Noodén on 2013-06-01
Ok.  Those show that the ssh server is running and listening on port 22.  That is as it should be.  

Have you changed the firewall on the server at all?  If so, you have to make sure it is still open on port 22.  

About root, by default Ubuntu does not use root, there will be a real user instead.  Try logging in as that user.  When you looked at the output of **ssh -vvv *ser er*** what error messages did it tell you?

---

### Post by Lars Noodén on 2013-06-01
Edit: double posted due to 502 error

---

### Post by spilner on 2013-06-01
i didnt touch anything about the firewall,it just suddenly happened.

i really dont have other user,just use root for all.

root@rescue:~# ssh -vvv ser er
OpenSSH_6.0p1 OVH-rescue, OpenSSL 1.0.1c 10 May 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
ssh: Could not resolve hostname ser: Name or service not known

---

### Post by Lars Noodén on 2013-06-01
Can you ping the server from the client?

```

ping -c 5 -w 1 server

```

Obviously substitute the address or ip number of the server for "server"

---

### Post by spilner on 2013-06-01
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.010/0.015/0.021/0.006 ms

---

### Post by mennopieters on 2013-06-01
use root for all????? No comment...

About the ssh connection  issue: check DNS settings, hosts and first of all, check your  authentication or daemon logs to look for messages why ssh may not  accept or immediately close the connections. The message "Server  unexpectedly closed network connection" makes me think something is  wrong with client address resolving, or perhaps the validation of credentials may fail.

- Menno

---

