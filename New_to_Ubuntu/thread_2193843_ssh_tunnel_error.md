---
title: "ssh tunnel error"
date: 2013-12-14
forum: New to Ubuntu
---

### Post by micahpage on 2013-12-14
I just logged into my server maybe a few days ago or so. Then recently i tried logging into it again today, and i get this error:
```
metulburr@arch ~ $ ssh username@www.myserver.com -p 12345
ssh_exchange_identification: read: Connection reset by peer
metulburr@arch ~ $ 


```

the server is running ubuntu 12.0.4.3

I am not sure as to what it might be as logging in 3 days ago was successful, and today is not?
I deleted ```
~/.ssh/known_hosts
``` on my desktop, but still get the error. I tried ssh'ing into anothers computer and successfully logged in. They tried logging into my server and get the same ```
ssh_exchange_identification: read: Connection reset by peer
```

The server last update was probably a month or so ago. With multiple times being ssh into since then.

---

### Post by DuckHook on 2013-12-15
I'm no ssh expert and completely out of my depth on this one, but how did you set up ssh on the server? Did you disable password and use RSA keys? Please describe network topography. How many NICs on server? How many servers?

This error could be due to any number of things: a failing NIC, IP conflict with another host, firewall interference, port conflict with another service, and since you are presumably tunneling through any number of ISPs, it could be something interfering in between.

What does your server tell you? Auth.log might give some clues.

Also, post output of:```
ssh username@www.myserver.com -p 12345 -vv
```...if that produces no worthwhile info, elevate to -vvv and -vvvv. You will likely want to sanitize output before posting. Last but not least, this is an Absolute Beginners forum and your problem is far far outside of its scope. You should ask one of the mods to move your thread to "Networks and Wireless" where a network guru can properly assess your issues.

As mentioned, this is way beyond me and I am only pointing out how you can provide more useful working info for those who know how to help you.

---

### Post by micahpage on 2013-12-15
I may of incorrectly stated tunneling, as it is direct ssh to one server. It is a home server. Single tower. It is password login. On a network with 5-6 other devices (desktops/laptops/xbox/tablets). None of these inet addresses look to be the same, they all are unique, as well with ports port-forwarded. If i recall correctly, i didnt even start the firewall on the server.  The server is still running as it still hosting the website. [www.metulburr.com]("http://www.metulburr.com")

```
metulburr@arch ~ $ ssh metulburr@www.metulburr.com -p 12345 -vvvv
OpenSSH_6.4, OpenSSL 1.0.1e 11 Feb 2013
debug1: Reading configuration data /etc/ssh/ssh_config
debug2: ssh_connect: needpriv 0
debug1: Connecting to www.metulburr.com [69.204.234.42] port 12345.
debug1: Connection established.
debug1: identity file /home/metulburr/.ssh/id_rsa type -1
debug1: identity file /home/metulburr/.ssh/id_rsa-cert type -1
debug1: identity file /home/metulburr/.ssh/id_dsa type -1
debug1: identity file /home/metulburr/.ssh/id_dsa-cert type -1
debug1: identity file /home/metulburr/.ssh/id_ecdsa type -1
debug1: identity file /home/metulburr/.ssh/id_ecdsa-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.4
ssh_exchange_identification: read: Connection reset by peer
metulburr@arch ~ $ 


```


> Last but not least, this is an Absolute Beginners forum and your  problem is far far outside of its scope. You should ask one of the mods  to move your thread to "Networks and Wireless" where a network guru can  properly assess your issues.

oh, i didnt think this was outside the scope of beginners.

---

### Post by Lars Noodén on 2013-12-15
That looks more or less normal up until the connection reset.  What about on the server side of things?  Can you log in at a console and do a one-off sshd session?

```

sudo service ssh stop
sudo /usr/sbin/sshd -d

```

Then you can try logging in from a second machine to see what the server side of things is doing.  Then you can resume regular ssh service.
```

sudo service ssh start

```

---

### Post by DuckHook on 2013-12-15
<burp>

---

### Post by micahpage on 2013-12-15
This is the output from that command while  trying to ssh into it:

```
[COLOR=#000000]debug1: sshd version OpenSSH_5.9p1 Debian-5ubuntu1.1[/COLOR]debug1: read PEM private key done: type RSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: private host key: #0 type 1 RSA
debug1: read PEM private key done: type DSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: private host key: #1 type 2 DSA
debug1: read PEM private key done: type ECDSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.ECDSA-256
debug1: Checking blacklist file /etc/ssh/blacklist.ECDSA-256
debug1: private host key: #2 type 3 ECDSA
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug1: rexec_argv[1]='-d'
Set /proc/self/oom_score_adj from 0 to -1000
debug1: Bind to port 56798 on 0.0.0.0.
Server listening on 0.0.0.0 port 12345.
debug1: Bind to port 12345 on ::.
Server listening on :: port 12345.
[COLOR=#000000]debug1: Server will not fork when running in debugging mode.
[/COLOR][COLOR=#000000]debug1: rexec start in 5 out 5 newsock 5 pipe -1 sock 8
[/COLOR][COLOR=#000000]debug1: inetd sockets after dupping: 3, 3 [/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]debug1: Connection refused by tcp wrapper[/COLOR]
```

---

### Post by micahpage on 2013-12-15
ok after googling this error or tcp connection i found that the results is /etc/host.deny or /etc/host.allow

allow had nothing in it, while deny had my ip address and my brothers ip. Every time i comment them out, i save and go back later to find that they are re-entered under my comment. So i am not sure what that is about? I also added:
```
ALL: ALL
```
to allow... in which seems regardless of what is in deny, is allowing me access to ssh into the server. Did an update of ssh do this? Also what was it by default before updating? Was it ALL or was it specifcally set to something?

EDIT:
thanks [**[COLOR=#DD4814][B]Lars Noodén**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=168643") and [**[COLOR=#000000]DuckHook[/COLOR]**]("http://ubuntuforums.org/member.php?u=1256508")

---

### Post by Lars Noodén on 2013-12-16
TCP Wrappers are also called tcpd, if you want to look around for more HowTos and such.  But the manual page for [hosts_access](http://manpages.ubuntu.com/manpages/trusty/en/man5/hosts_access.5.html) will have the details.  The settings in hosts.allow override those in hosts.deny.  You can also let in all hosts to just sshd in hosts.allow if there are other services you want to keep closed:

```

sshd: ALL

```

I'm not sure how hosts.deny is getting automatically updated on your machine.  Neither /etc/hosts.allow and /etc/hosts.deny are going to be updated automatically by other applications or updates, at least in my experience.  By default both are empty in Ubuntu.  Is this on a VPS where you can set defaults for various system files using Puppet or something similar?

---

