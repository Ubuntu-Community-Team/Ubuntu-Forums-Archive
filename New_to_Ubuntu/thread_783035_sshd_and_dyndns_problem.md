---
title: "sshd and dyndns problem"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by dynamethod on 2008-05-05
Hey there, today i setup an account with dyndns for two reasons

one was to set up my webserver with apache, which ived done successfully

the other was so i can resolve the hostname at work and log on via ssh(or log on via ssh and use the hostname as a parameter if possible)

so far i can only log in via ssh locally via localhost, but cant from external IP

heres my sshd_config:

```
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 60010
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
ListenAddress 192.168.1.100
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel VERBOSE

# Authentication:
LoginGraceTime 20
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding no
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

MaxAuthTries 5

```

as you can see im using port 60010, though i initially tried the default port 22 which wouldnt work either, help much appreciated

Just tried via localhost now, now i cant connect locally either :S


and no portforwarding is not the issue, that im absolutly sure of

---

### Post by fahadsadah on 2008-05-05
Please try changing ListenAddress to 127.0.0.1 (localhost).
Thank you.

---

### Post by dynamethod on 2008-05-05
Yes that works, but that only lets me log in locally

if i try "ssh <mydnshostname.etc.etc> -p 60010" it refuses the connection

---

### Post by fahadsadah on 2008-05-05
Are you sure port-forwarding is not the issue?

---

### Post by Monicker on 2008-05-05
So, sshd seems to be at least listening.  I would change it back to the 192.168.x.x address, and attempt another connection from externally.  Then check /var/log/messages and /var/log/auth.log to see if ssh is generating any messages about why the connection failed.

You mentioned you were sure port forwarding is not an issue.  How did you verify this?  It wouldn't hurt to run wireshark or tcpdump to make sure that you can see the forwarded packets reaching the machine.

---

### Post by dynamethod on 2008-05-05
Im sure im sure, i have a webserver setup whcih i had to port forward to access it remotely, which i can and works fine


its just ssh im struggling with

---

### Post by fahadsadah on 2008-05-05
What is the DynDNS hostname?
I have an idea.

---

### Post by dynamethod on 2008-05-05
Ive changed the port this time to 2222, and the ListenAddress back to 192.168.1.100
then restarted ssh

here is the output of cat /var/log/auth.log | grep sshd | tail

```
May  6 05:19:48 darksun sshd[8177]: Server listening on 192.168.1.100 port 2222.

```

---

### Post by dynamethod on 2008-05-05
my dyndns address: edit

---

### Post by fahadsadah on 2008-05-05
I seem to be able to connect...
Perhaps DynDNS are blocking local connections?

---

### Post by dynamethod on 2008-05-05
they just redirect connections to my machine which runs apache, i update via ddclient, so if someone can view my page, then that means that they cant be blocking local connections

---

### Post by Monicker on 2008-05-05
Disregard previous.  I had forgotten to specify port 2222 for the connection.

Doh!

I also get a password prompt.

---

### Post by fahadsadah on 2008-05-05
It responded to my attempt, and gave me an enter password prompt...

---

### Post by dynamethod on 2008-05-05
aahh! excellent, thank you guys very much then, it must be a local thing, thats cool, that means i can log in remotely in that case, thanks again :)

---

### Post by fahadsadah on 2008-05-05
You're most welcome.

---

### Post by fahadsadah on 2008-05-05
Please mark this thread as solved

---

### Post by lespaul_rentals on 2008-05-05
Try setting the Listen Address to 0.0.0.0

---

### Post by dynamethod on 2008-05-05
> **lespaul_rentals said:**
> Try setting the Listen Address to 0.0.0.0

what would that accomplish? and btw what happend to the "mark thread as solved" that used to drop down from clicking on thread tools??

---

