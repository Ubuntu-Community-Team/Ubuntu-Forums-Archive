---
title: "How to ssh localhost ."
date: 2015-03-24
forum: New to Ubuntu
---

### Post by noktualek on 2015-03-24
I try to ssh localhost  it always immediately  Terminated .

[IMG]http://upic.me/i/on/2015-03-24_17-09-36immediatelyterminate.png[/IMG]

How do i resolve this problem

---

### Post by Lars Noodén on 2015-03-24
Try connecting as a user other than root. 

Logging remotely as root is generally frowned upon, there is usually a safer way.  And the default for Ubuntu these days is to block root login without keys.

Edit: If you check your /etc/ssh/sshd_config for the line [PermitRootLogin](http://manpages.ubuntu.com/manpages/trusty/en/man5/sshd_config.5.html) you will see that you need to log in as another user.

---

### Post by noktualek on 2015-03-24
I used permitRootLogin Yes  and reboot
[IMG]http://upic.me/i/fm/2015-03-24_18-10-33rootyes.png[/IMG]

Try to another user  but it is same problem
[IMG]http://upic.me/i/hw/2015-03-24_18-05-46sshrefused.png[/IMG]

Can everyone help me ?

I can not used putty to this server it is the same problem as ssh to localhost.

Note. 
Before append this problem i forget root password and used  ubuntu recovery mode to reset root password. after that i can not use putty to ssh this server.

I capture this picture from terminal monitor.

thanks for you help.

---

### Post by Lars Noodén on 2015-03-24
What is the output of the [ssh](http://manpages.ubuntu.com/manpages/trusty/en/man1/ssh.1.html) client if you connect in very, very verbose mode?

```

ssh **-vvv** noktualek@localhost

```

You can put the output between [****code] [/code] tags here and it will get formatted properly.

Note that what you have here won't work because it will try to run the command 'localhost' upon logging in and there probably is not such a command on your machine if you did not write it yourself:

```

[s]ssh **-vvv** noktualek@localhost localhost[/s]

```

---

### Post by noktualek on 2015-03-24
result
```
ssh -vvv noktualek@localhost localhost 

OpenSSH_5.9p1 Debian-5ubuntu1.4, OpenSSL 1.0.1 14 Mar 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/id_rsa type -1
debug1: identity file /root/.ssh/id_rsa-cert type -1
debug3: Incorrect RSA1 identifier
[COLOR=#ff0000]debug3: Could not load "/root/.ssh/id_dsa" as a RSA1 public key[/COLOR]
debug1: identity file /root/.ssh/id_dsa type 2
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: identity file /root/.ssh/id_dsa-cert type -1
debug1: identity file /root/.ssh/id_ecdsa type -1
debug1: identity file /root/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.9p1 Debian-5ubuntu1.4
debug1: match: OpenSSH_5.9p1 Debian-5ubuntu1.4 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1.4
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: [email]ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-dss-cert-v00@openssh.com[/email],ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss,ecdsa-sha2-nistp256
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-ctr hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA 70:ec:b2:10:f9:b5:b7:64:ff:90:50:41:4d:7c:d9:07
```

---

### Post by Lars Noodén on 2015-03-24
That looks like only part of the output, it should get as far as asking for the password at least.  Can you grab the whole thing?  Also, as mentioned, don't try running any special command on the remote machine, let it go through to the shell like this:

```

ssh -vvv noktualek@localhost

```

---

### Post by noktualek on 2015-03-24
1 I try to
> 
# apt-get remove openssh-server
# apt-get install openssh-sever


2 Check /etc/hosts.deny
ALL: 192.168.100.0 localhost 192.168.1.0

3 Check /etc/hosts.deny
not have any thing

But problem is not prove.

[IMG]http://upic.me/i/k0/2015-03-24_19-47-4511.png[/IMG]
[IMG]http://upic.me/i/ko/2015-03-24_19-46-4910.png[/IMG][IMG]http://upic.me/i/8j/2015-03-24_19-45-417.png[/IMG][IMG]http://upic.me/i/rx/2015-03-24_19-45-166.png[/IMG][IMG]http://upic.me/i/j2/2015-03-24_19-44-185.png[/IMG][IMG]http://upic.me/i/k2/2015-03-24_19-43-534.png[/IMG][IMG]http://upic.me/i/k2/2015-03-24_19-43-534.png[/IMG][IMG]http://upic.me/i/3u/2015-03-24_19-43-233.png[/IMG]

[IMG]http://upic.me/i/3u/2015-03-24_19-43-233.png[/IMG][IMG]http://upic.me/i/vz/2015-03-24_19-42-502.png[/IMG][IMG]http://upic.me/i/wb/2015-03-24_19-42-181.png[/IMG]

---

### Post by Lars Noodén on 2015-03-24
> **noktualek said:**
> 2 Check /etc/hosts.deny
ALL: 192.168.100.0 localhost 192.168.1.0

3 Check /etc/hosts.deny
not have any thing

Is #2 there supposed to be /etc/hosts.allow?

---

### Post by noktualek on 2015-03-24
The correct is

2 Check /etc/hosts.allow
ALL: 192.168.100.0 localhost 192.168.1.0

---

### Post by Lars Noodén on 2015-03-24
Ok.  Since you have local access, we can then also watch what the server tries to do.

Set up the server for a single login in very, very verbose mode:

```

service ssh stop
/usr/sbin/sshd -ddd

```

Then try logging in.

Please paste the results here.

Then restore the service to normal.

```

service ssh start

```

---

### Post by noktualek on 2015-03-24
# service ssh stop
# /usr/sbin/sshd -ddd
> debug2: load_server_config: filename /etc/ssh/sshd_configdebug2: load_server_config: done config len = 714
debug2: parse_server_config: config /etc/ssh/sshd_config len 714
debug3: /etc/ssh/sshd_config:5 setting Port 22
debug3: /etc/ssh/sshd_config:9 setting Protocol 2
debug3: /etc/ssh/sshd_config:11 setting HostKey /etc/ssh/ssh_host_rsa_key
debug3: /etc/ssh/sshd_config:12 setting HostKey /etc/ssh/ssh_host_dsa_key
debug3: /etc/ssh/sshd_config:13 setting HostKey /etc/ssh/ssh_host_ecdsa_key
debug3: /etc/ssh/sshd_config:15 setting UsePrivilegeSeparation yes
debug3: /etc/ssh/sshd_config:18 setting KeyRegenerationInterval 3600
debug3: /etc/ssh/sshd_config:19 setting ServerKeyBits 768
debug3: /etc/ssh/sshd_config:22 setting SyslogFacility AUTH
debug3: /etc/ssh/sshd_config:23 setting LogLevel INFO
debug3: /etc/ssh/sshd_config:26 setting LoginGraceTime 120
debug3: /etc/ssh/sshd_config:27 setting PermitRootLogin yes
debug3: /etc/ssh/sshd_config:28 setting StrictModes yes
debug3: /etc/ssh/sshd_config:30 setting RSAAuthentication yes
debug3: /etc/ssh/sshd_config:31 setting PubkeyAuthentication yes
debug3: /etc/ssh/sshd_config:35 setting IgnoreRhosts yes
debug3: /etc/ssh/sshd_config:37 setting RhostsRSAAuthentication no
debug3: /etc/ssh/sshd_config:39 setting HostbasedAuthentication no
debug3: /etc/ssh/sshd_config:44 setting PermitEmptyPasswords no
debug3: /etc/ssh/sshd_config:48 setting ChallengeResponseAuthentication no
debug3: /etc/ssh/sshd_config:63 setting X11Forwarding yes
debug3: /etc/ssh/sshd_config:64 setting X11DisplayOffset 10
debug3: /etc/ssh/sshd_config:65 setting PrintMotd no
debug3: /etc/ssh/sshd_config:66 setting PrintLastLog yes
debug3: /etc/ssh/sshd_config:67 setting TCPKeepAlive yes
debug3: /etc/ssh/sshd_config:74 setting AcceptEnv LANG LC_*
debug3: /etc/ssh/sshd_config:76 setting Subsystem sftp /usr/lib/openssh/sftp-server
debug3: /etc/ssh/sshd_config:87 setting UsePAM no
debug3: /etc/ssh/sshd_config:88 setting AllowUsers noktualek@localhost 
debug1: sshd version OpenSSH_5.9p1 Debian-5ubuntu1.4
debug3: Incorrect RSA1 identifier
debug1: read PEM private key done: type RSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: private host key: #0 type 1 RSA
debug3: Incorrect RSA1 identifier
debug1: read PEM private key done: type DSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: private host key: #1 type 2 DSA
debug3: Incorrect RSA1 identifier
debug1: read PEM private key done: type ECDSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.ECDSA-256
debug1: Checking blacklist file /etc/ssh/blacklist.ECDSA-256
debug1: private host key: #2 type 3 ECDSA
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug1: rexec_argv[1]='-ddd'
debug3: oom_adjust_setup
Set /proc/self/oom_score_adj from 0 to -1000
debug2: fd 3 setting O_NONBLOCK
debug1: Bind to port 22 on 0.0.0.0.
Server listening on 0.0.0.0 port 22.
debug2: fd 4 setting O_NONBLOCK
debug3: sock_set_v6only: set socket 4 IPV6_V6ONLY
debug1: Bind to port 22 on ::.
Server listening on :: port 22.

# service ssh start
> ssh start/running, process 10003

Thanks

---

### Post by Lars Noodén on 2015-03-24
> **noktualek said:**
> 
```

# service ssh stop
# /usr/sbin/sshd -ddd
...
debug2: fd 4 setting O_NONBLOCK
debug3: sock_set_v6only: set socket 4 IPV6_V6ONLY
debug1: Bind to port 22 on ::.
Server listening on :: port 22.

```


Thanks.  The interesting stuff should have happened after "Server listening on :: port 22." when you tried to log in.  Can you stop sshd again, run it with -ddd  and try to log in to that?  Then post what -ddd says once you have tried to log in.

---

### Post by noktualek on 2015-03-24
[IMG]http://upic.me/i/ty/2015-03-24_20-56-10ddd.png[/IMG]

```
debug2: load_server_config: filename /etc/ssh/sshd_configdebug2: load_server_config: done config len = 714
debug2: parse_server_config: config /etc/ssh/sshd_config len 714
debug3: /etc/ssh/sshd_config:5 setting Port 22
debug3: /etc/ssh/sshd_config:9 setting Protocol 2
debug3: /etc/ssh/sshd_config:11 setting HostKey /etc/ssh/ssh_host_rsa_key
debug3: /etc/ssh/sshd_config:12 setting HostKey /etc/ssh/ssh_host_dsa_key
debug3: /etc/ssh/sshd_config:13 setting HostKey /etc/ssh/ssh_host_ecdsa_key
debug3: /etc/ssh/sshd_config:15 setting UsePrivilegeSeparation yes
debug3: /etc/ssh/sshd_config:18 setting KeyRegenerationInterval 3600
debug3: /etc/ssh/sshd_config:19 setting ServerKeyBits 768
debug3: /etc/ssh/sshd_config:22 setting SyslogFacility AUTH
debug3: /etc/ssh/sshd_config:23 setting LogLevel INFO
debug3: /etc/ssh/sshd_config:26 setting LoginGraceTime 120
debug3: /etc/ssh/sshd_config:27 setting PermitRootLogin yes
debug3: /etc/ssh/sshd_config:28 setting StrictModes yes
debug3: /etc/ssh/sshd_config:30 setting RSAAuthentication yes
debug3: /etc/ssh/sshd_config:31 setting PubkeyAuthentication yes
debug3: /etc/ssh/sshd_config:35 setting IgnoreRhosts yes
debug3: /etc/ssh/sshd_config:37 setting RhostsRSAAuthentication no
debug3: /etc/ssh/sshd_config:39 setting HostbasedAuthentication no
debug3: /etc/ssh/sshd_config:44 setting PermitEmptyPasswords no
debug3: /etc/ssh/sshd_config:48 setting ChallengeResponseAuthentication no
debug3: /etc/ssh/sshd_config:63 setting X11Forwarding yes
debug3: /etc/ssh/sshd_config:64 setting X11DisplayOffset 10
debug3: /etc/ssh/sshd_config:65 setting PrintMotd no
debug3: /etc/ssh/sshd_config:66 setting PrintLastLog yes
debug3: /etc/ssh/sshd_config:67 setting TCPKeepAlive yes
debug3: /etc/ssh/sshd_config:74 setting AcceptEnv LANG LC_*
debug3: /etc/ssh/sshd_config:76 setting Subsystem sftp /usr/lib/openssh/sftp-server
debug3: /etc/ssh/sshd_config:87 setting UsePAM no
debug3: /etc/ssh/sshd_config:88 setting AllowUsers noktualek@localhost 
debug1: sshd version OpenSSH_5.9p1 Debian-5ubuntu1.4
debug3: Incorrect RSA1 identifier
debug1: read PEM private key done: type RSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: private host key: #0 type 1 RSA
debug3: Incorrect RSA1 identifier
debug1: read PEM private key done: type DSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: private host key: #1 type 2 DSA
debug3: Incorrect RSA1 identifier
debug1: read PEM private key done: type ECDSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.ECDSA-256
debug1: Checking blacklist file /etc/ssh/blacklist.ECDSA-256
debug1: private host key: #2 type 3 ECDSA
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug1: rexec_argv[1]='-ddd'
debug3: oom_adjust_setup
Set /proc/self/oom_score_adj from 0 to -1000
debug2: fd 3 setting O_NONBLOCK
debug1: Bind to port 22 on 0.0.0.0.
Server listening on 0.0.0.0 port 22.
debug2: fd 4 setting O_NONBLOCK
debug3: sock_set_v6only: set socket 4 IPV6_V6ONLY
debug1: Bind to port 22 on ::.
Server listening on :: port 22.
```

[IMG]http://upic.me/i/mx/2015-03-24_20-58-38status.png[/IMG]

---

### Post by Lars Noodén on 2015-03-24
ok.  Now log in, "sshd -ddd" will let you log in once.  Then post what the rest of what gets added to "note.txt"

---

### Post by noktualek on 2015-03-24
> **Lars Noodén said:**
> ok.  Now log in, "sshd -ddd" will let you log in once.  Then post what the rest of what gets added to "note.txt"
can you explain this ssh-ddd. pleae give some example command. 

thanks for your help

[IMG]http://upic.me/i/ic/2015-03-24_21-18-31ddd2.png[/IMG]

```
debug2: load_server_config: filename /etc/ssh/sshd_configdebug2: load_server_config: done config len = 714
debug2: parse_server_config: config /etc/ssh/sshd_config len 714
debug3: /etc/ssh/sshd_config:5 setting Port 22
debug3: /etc/ssh/sshd_config:9 setting Protocol 2
debug3: /etc/ssh/sshd_config:11 setting HostKey /etc/ssh/ssh_host_rsa_key
debug3: /etc/ssh/sshd_config:12 setting HostKey /etc/ssh/ssh_host_dsa_key
debug3: /etc/ssh/sshd_config:13 setting HostKey /etc/ssh/ssh_host_ecdsa_key
debug3: /etc/ssh/sshd_config:15 setting UsePrivilegeSeparation yes
debug3: /etc/ssh/sshd_config:18 setting KeyRegenerationInterval 3600
debug3: /etc/ssh/sshd_config:19 setting ServerKeyBits 768
debug3: /etc/ssh/sshd_config:22 setting SyslogFacility AUTH
debug3: /etc/ssh/sshd_config:23 setting LogLevel INFO
debug3: /etc/ssh/sshd_config:26 setting LoginGraceTime 120
debug3: /etc/ssh/sshd_config:27 setting PermitRootLogin yes
debug3: /etc/ssh/sshd_config:28 setting StrictModes yes
debug3: /etc/ssh/sshd_config:30 setting RSAAuthentication yes
debug3: /etc/ssh/sshd_config:31 setting PubkeyAuthentication yes
debug3: /etc/ssh/sshd_config:35 setting IgnoreRhosts yes
debug3: /etc/ssh/sshd_config:37 setting RhostsRSAAuthentication no
debug3: /etc/ssh/sshd_config:39 setting HostbasedAuthentication no
debug3: /etc/ssh/sshd_config:44 setting PermitEmptyPasswords no
debug3: /etc/ssh/sshd_config:48 setting ChallengeResponseAuthentication no
debug3: /etc/ssh/sshd_config:63 setting X11Forwarding yes
debug3: /etc/ssh/sshd_config:64 setting X11DisplayOffset 10
debug3: /etc/ssh/sshd_config:65 setting PrintMotd no
debug3: /etc/ssh/sshd_config:66 setting PrintLastLog yes
debug3: /etc/ssh/sshd_config:67 setting TCPKeepAlive yes
debug3: /etc/ssh/sshd_config:74 setting AcceptEnv LANG LC_*
debug3: /etc/ssh/sshd_config:76 setting Subsystem sftp /usr/lib/openssh/sftp-server
debug3: /etc/ssh/sshd_config:87 setting UsePAM no
debug3: /etc/ssh/sshd_config:88 setting AllowUsers noktualek@localhost 
debug1: sshd version OpenSSH_5.9p1 Debian-5ubuntu1.4
debug3: Incorrect RSA1 identifier
debug1: read PEM private key done: type RSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: private host key: #0 type 1 RSA
debug3: Incorrect RSA1 identifier
debug1: read PEM private key done: type DSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: private host key: #1 type 2 DSA
debug3: Incorrect RSA1 identifier
debug1: read PEM private key done: type ECDSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.ECDSA-256
debug1: Checking blacklist file /etc/ssh/blacklist.ECDSA-256
debug1: private host key: #2 type 3 ECDSA
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug1: rexec_argv[1]='-ddd'
debug3: oom_adjust_setup
Set /proc/self/oom_score_adj from 0 to -1000
debug2: fd 3 setting O_NONBLOCK
debug1: Bind to port 22 on 0.0.0.0.
Server listening on 0.0.0.0 port 22.
debug2: fd 4 setting O_NONBLOCK
debug3: sock_set_v6only: set socket 4 IPV6_V6ONLY
debug1: Bind to port 22 on ::.
Server listening on :: port 22.
```

---

### Post by Lars Noodén on 2015-03-24
Yes.  **/usr/bin/sshd** launches [sshd](http://manpages.ubuntu.com/manpages/trusty/en/man8/sshd.8.html) without any options.  It will run as normal based on what is in the configuration file.   

**/usr/bin/sshd -ddd** launches [sshd](http://manpages.ubuntu.com/manpages/trusty/en/man8/sshd.8.html) with whatever is in the configuration file *plus* debugging turned up to level 3.  With any debugging level, sshd only lets you log in once then quits.  It makes it easier to collect a single, complete login session.

However, to be able to do that, you have to first tell Upstart not keep restarting sshd, so you do **service ssh stop** to get Upstart out of the way.

So by running **/usr/bin/sshd -ddd** you can see it start up.  Then we need to finish getting the debugging data by logging in.

---

### Post by noktualek on 2015-03-24
I try
# ssh-keygen -t rsa
# utf allow 22

/etc/hosts.allow
ALL:192.168.100.0 192.168.1.0 localhost

/etc/ssh/sshd_config
Port 22
ListenAddress 0.0.0.0
AllowUsers noktualek@localhost root
PermitRootLogin yes

It will not work . How i try another method.

Thanks

---

### Post by Lars Noodén on 2015-03-24
> **noktualek said:**
> AllowUsers noktualek@localhost root


In /etc/ssh/[sshd_config](http://manpages.ubuntu.com/manpages/trusty/en/man5/sshd_config.5.html), just list the users without the host, like this:

AllowUsers noktualek root

But what was the tail end of the output from sshd in very, very verbose mode?

---

### Post by noktualek on 2015-03-24
[IMG]http://upic.me/i/lq/2015-03-25_07-29-03terminate.png[/IMG]

log.txt
```
OpenSSH_5.9p1 Debian-5ubuntu1.4, OpenSSL 1.0.1 14 Mar 2012debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/id_rsa type -1
debug1: identity file /root/.ssh/id_rsa-cert type -1
debug1: identity file /root/.ssh/id_dsa type -1
debug1: identity file /root/.ssh/id_dsa-cert type -1
debug1: identity file /root/.ssh/id_ecdsa type -1
debug1: identity file /root/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.9p1 Debian-5ubuntu1.4
debug1: match: OpenSSH_5.9p1 Debian-5ubuntu1.4 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1.4
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: [email]ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-dss-cert-v00@openssh.com[/email],ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss,ecdsa-sha2-nistp256
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-ctr hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA b6:5b:f7:7b:71:e2:26:3d:57:0e:97:11:12:ba:2d:61
```

[IMG]http://upic.me/i/n5/2015-03-25_08-28-36failed.png[/IMG]

---

### Post by Lars Noodén on 2015-03-25
In post #22 above you removed your local user's record of which host key your server identifies with.  So it is normal for it to complain that authenticity can't be established.  The way out of that is to check that the fingerprint matches and, if it does, press yes.  

In post #21 above you ran the client ( 'ssh -vvv' ) and got its output.  In number #17 above you captured output from the server ( 'ssh -ddd' ) but only the part before trying to log in.  Can you provide the server output from the login attempt itself?  Edit: the reason for that is to see why the server breaks the connection.

---

### Post by noktualek on 2015-03-25
can you explain what command i will do it for test .

---

### Post by Lars Noodén on 2015-03-25
Yes.  Open two terminals in the same machine, one with root access.  

In the one with root, stop sshd in Upstart and start it manually with debugging turned up to level 3

```

service ssh stop
/usr/sbin/sshd -ddd 2>&1 | tee /tmp/sshd.log

```

Then in the other terminal, try to log in once.

```

ssh -l noktualek localhost

```

Then after trying to log in please post sshd.log, so we can see what it complains about when it fails.

---

### Post by noktualek on 2015-03-25
[IMG]http://upic.me/i/is/2015-03-26_00-57-33tee.png[/IMG]
> debug2: load_server_config: filename /etc/ssh/sshd_configdebug2: load_server_config: done config len = 746
debug2: parse_server_config: config /etc/ssh/sshd_config len 746
debug3: /etc/ssh/sshd_config:5 setting Port 22
debug3: /etc/ssh/sshd_config:8 setting ListenAddress 0.0.0.0
debug3: /etc/ssh/sshd_config:9 setting Protocol 2
debug3: /etc/ssh/sshd_config:11 setting HostKey /etc/ssh/ssh_host_rsa_key
debug3: /etc/ssh/sshd_config:12 setting HostKey /etc/ssh/ssh_host_dsa_key
debug3: /etc/ssh/sshd_config:13 setting HostKey /etc/ssh/ssh_host_ecdsa_key
debug3: /etc/ssh/sshd_config:15 setting UsePrivilegeSeparation yes
debug3: /etc/ssh/sshd_config:18 setting KeyRegenerationInterval 3600
debug3: /etc/ssh/sshd_config:19 setting ServerKeyBits 1024
debug3: /etc/ssh/sshd_config:22 setting SyslogFacility AUTH
debug3: /etc/ssh/sshd_config:23 setting LogLevel INFO
debug3: /etc/ssh/sshd_config:26 setting LoginGraceTime 120
debug3: /etc/ssh/sshd_config:27 setting PermitRootLogin no
debug3: /etc/ssh/sshd_config:28 setting StrictModes yes
debug3: /etc/ssh/sshd_config:30 setting RSAAuthentication yes
debug3: /etc/ssh/sshd_config:31 setting PubkeyAuthentication yes
debug3: /etc/ssh/sshd_config:35 setting IgnoreRhosts yes
debug3: /etc/ssh/sshd_config:37 setting RhostsRSAAuthentication no
debug3: /etc/ssh/sshd_config:39 setting HostbasedAuthentication no
debug3: /etc/ssh/sshd_config:44 setting PermitEmptyPasswords no
debug3: /etc/ssh/sshd_config:48 setting ChallengeResponseAuthentication no
debug3: /etc/ssh/sshd_config:63 setting X11Forwarding yes
debug3: /etc/ssh/sshd_config:64 setting X11DisplayOffset 10
debug3: /etc/ssh/sshd_config:65 setting PrintMotd no
debug3: /etc/ssh/sshd_config:66 setting PrintLastLog yes
debug3: /etc/ssh/sshd_config:67 setting TCPKeepAlive yes
debug3: /etc/ssh/sshd_config:74 setting AcceptEnv LANG LC_*
debug3: /etc/ssh/sshd_config:76 setting Subsystem sftp /usr/lib/openssh/sftp-server
debug3: /etc/ssh/sshd_config:87 setting UsePAM yes
debug3: /etc/ssh/sshd_config:88 setting AllowUsers noktualek root
debug3: /etc/ssh/sshd_config:89 setting MaxAuthTries 20
debug1: sshd version OpenSSH_6.6.1, OpenSSL 1.0.1f 6 Jan 2014
debug3: Incorrect RSA1 identifier
debug1: key_parse_private2: missing begin marker
debug1: read PEM private key done: type RSA
debug3: Incorrect RSA1 identifier
debug3: Could not load "/etc/ssh/ssh_host_rsa_key" as a RSA1 public key
debug1: private host key: #0 type 1 RSA
debug3: Incorrect RSA1 identifier
debug1: key_parse_private2: missing begin marker
debug1: read PEM private key done: type DSA
debug3: Incorrect RSA1 identifier
debug3: Could not load "/etc/ssh/ssh_host_dsa_key" as a RSA1 public key
debug1: private host key: #1 type 2 DSA
debug3: Incorrect RSA1 identifier
debug1: key_parse_private2: missing begin marker
debug1: read PEM private key done: type ECDSA
debug3: Incorrect RSA1 identifier
debug3: Could not load "/etc/ssh/ssh_host_ecdsa_key" as a RSA1 public key
debug1: private host key: #2 type 3 ECDSA
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug1: rexec_argv[1]='-ddd'
debug3: oom_adjust_setup
Set /proc/self/oom_score_adj from 0 to -1000
debug2: fd 3 setting O_NONBLOCK
debug1: Bind to port 22 on 0.0.0.0.
Server listening on 0.0.0.0 port 22.


[IMG]http://upic.me/i/ds/2015-03-26_01-00-00ssh-l.png[/IMG]


Thanks

---

### Post by Lars Noodén on 2015-03-25
Yes.  That's the output from "sshd -ddd" before you tried to log in.  Can you add the rest of the output, the part that came after you tried to log in?  It should be there in that file.

There should be a whole lot after "Server listening on :: port 22".  That second part should be longer than the first part, starting with "debug1: Server will not fork when running in debugging mode."

---

### Post by noktualek on 2015-03-25
[COLOR=#000000]can you explain what command i will do it[/COLOR]

---

### Post by Lars Noodén on 2015-03-25
the same commands as above, but wait until after you have tried logging in before looking at 'sshd.log'.  We need the data that comes after the attempted login.

---

### Post by noktualek on 2015-03-25
[IMG]http://upic.me/i/7x/2015-03-26_01-35-36wait.png[/IMG]

# service ssh stop
Wait 3 minutes
# /usr/sbin/sshd -ddd 2>&1 | tee /home/noktualek/wait_3_minutes.txt

this is wait_3_minutes.txt content
> debug2: load_server_config: filename /etc/ssh/sshd_config
debug2: load_server_config: done config len = 746
debug2: parse_server_config: config /etc/ssh/sshd_config len 746
debug3: /etc/ssh/sshd_config:5 setting Port 22
debug3: /etc/ssh/sshd_config:8 setting ListenAddress 0.0.0.0
debug3: /etc/ssh/sshd_config:9 setting Protocol 2
debug3: /etc/ssh/sshd_config:11 setting HostKey /etc/ssh/ssh_host_rsa_key
debug3: /etc/ssh/sshd_config:12 setting HostKey /etc/ssh/ssh_host_dsa_key
debug3: /etc/ssh/sshd_config:13 setting HostKey /etc/ssh/ssh_host_ecdsa_key
debug3: /etc/ssh/sshd_config:15 setting UsePrivilegeSeparation yes
debug3: /etc/ssh/sshd_config:18 setting KeyRegenerationInterval 3600
debug3: /etc/ssh/sshd_config:19 setting ServerKeyBits 1024
debug3: /etc/ssh/sshd_config:22 setting SyslogFacility AUTH
debug3: /etc/ssh/sshd_config:23 setting LogLevel INFO
debug3: /etc/ssh/sshd_config:26 setting LoginGraceTime 120
debug3: /etc/ssh/sshd_config:27 setting PermitRootLogin no
debug3: /etc/ssh/sshd_config:28 setting StrictModes yes
debug3: /etc/ssh/sshd_config:30 setting RSAAuthentication yes
debug3: /etc/ssh/sshd_config:31 setting PubkeyAuthentication yes
debug3: /etc/ssh/sshd_config:35 setting IgnoreRhosts yes
debug3: /etc/ssh/sshd_config:37 setting RhostsRSAAuthentication no
debug3: /etc/ssh/sshd_config:39 setting HostbasedAuthentication no
debug3: /etc/ssh/sshd_config:44 setting PermitEmptyPasswords no
debug3: /etc/ssh/sshd_config:48 setting ChallengeResponseAuthentication no
debug3: /etc/ssh/sshd_config:63 setting X11Forwarding yes
debug3: /etc/ssh/sshd_config:64 setting X11DisplayOffset 10
debug3: /etc/ssh/sshd_config:65 setting PrintMotd no
debug3: /etc/ssh/sshd_config:66 setting PrintLastLog yes
debug3: /etc/ssh/sshd_config:67 setting TCPKeepAlive yes
debug3: /etc/ssh/sshd_config:74 setting AcceptEnv LANG LC_*
debug3: /etc/ssh/sshd_config:76 setting Subsystem sftp /usr/lib/openssh/sftp-server
debug3: /etc/ssh/sshd_config:87 setting UsePAM yes
debug3: /etc/ssh/sshd_config:88 setting AllowUsers noktualek root
debug3: /etc/ssh/sshd_config:89 setting MaxAuthTries 20
debug1: sshd version OpenSSH_6.6.1, OpenSSL 1.0.1f 6 Jan 2014
[COLOR=#ff0000]debug3: Incorrect RSA1 identifier[/COLOR]
debug1: key_parse_private2:[COLOR=#ff0000] missing begin marker[/COLOR]
debug1: read PEM private key done: type RSA
[COLOR=#ff0000]debug3: Incorrect RSA1 identifier
debug3: Could not load "/etc/ssh/ssh_host_rsa_key" as a RSA1 public key[/COLOR]
debug1: private host key: #0 type 1 RSA
[COLOR=#ff0000]debug3: Incorrect RSA1 identifier[/COLOR]
debug1: key_parse_private2: [COLOR=#ff0000]missing begin marker[/COLOR]
debug1: read PEM private key done: type DSA
[COLOR=#ff0000]debug3: Incorrect RSA1 identifier
debug3: Could not load "/etc/ssh/ssh_host_dsa_key" as a RSA1 public key[/COLOR]
debug1: private host key: #1 type 2 DSA
[COLOR=#ff0000]debug3: Incorrect RSA1 identifier[/COLOR]
[COLOR=#ff0000]debug1: key_parse_private2: missing begin marker[/COLOR]
debug1: read PEM private key done: type ECDSA
[COLOR=#ff0000]debug3: Incorrect RSA1 identifier[/COLOR]
[COLOR=#ff0000]debug3: Could not load "/etc/ssh/ssh_host_ecdsa_key" as a RSA1 public key[/COLOR]
debug1: private host key: #2 type 3 ECDSA
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug1: rexec_argv[1]='-ddd'
debug3: oom_adjust_setup
Set /proc/self/oom_score_adj from 0 to -1000
debug2: fd 3 setting O_NONBLOCK
debug1: Bind to port 22 on 0.0.0.0.
Server listening on 0.0.0.0 port 22.




---

### Post by Lars Noodén on 2015-03-25
> **noktualek said:**
> this is wait_3_minutes.txt content

Yes, but did you post it here before you logged in or after?  It looks like before.

---

### Post by noktualek on 2015-03-25
[COLOR=#000000]# service ssh stop
[/COLOR]# exit  (exit all terminal  )
[COLOR=#000000]Wait 3 minutes
[/COLOR]login terminal again and then
[COLOR=#000000]# /usr/sbin/sshd -ddd 2>&1 | tee /home/noktualek/wait_3_minutes.txt[/COLOR]

[COLOR=#000000]this is wait_3_minutes.txt content
[/COLOR]> debug2: load_server_config: filename /etc/ssh/sshd_configdebug2: load_server_config: done config len = 746
debug2: parse_server_config: config /etc/ssh/sshd_config len 746
debug3: /etc/ssh/sshd_config:5 setting Port 22
debug3: /etc/ssh/sshd_config:8 setting ListenAddress 0.0.0.0
debug3: /etc/ssh/sshd_config:9 setting Protocol 2
debug3: /etc/ssh/sshd_config:11 setting HostKey /etc/ssh/ssh_host_rsa_key
debug3: /etc/ssh/sshd_config:12 setting HostKey /etc/ssh/ssh_host_dsa_key
debug3: /etc/ssh/sshd_config:13 setting HostKey /etc/ssh/ssh_host_ecdsa_key
debug3: /etc/ssh/sshd_config:15 setting UsePrivilegeSeparation yes
debug3: /etc/ssh/sshd_config:18 setting KeyRegenerationInterval 3600
debug3: /etc/ssh/sshd_config:19 setting ServerKeyBits 1024
debug3: /etc/ssh/sshd_config:22 setting SyslogFacility AUTH
debug3: /etc/ssh/sshd_config:23 setting LogLevel INFO
debug3: /etc/ssh/sshd_config:26 setting LoginGraceTime 120
debug3: /etc/ssh/sshd_config:27 setting PermitRootLogin no
debug3: /etc/ssh/sshd_config:28 setting StrictModes yes
debug3: /etc/ssh/sshd_config:30 setting RSAAuthentication yes
debug3: /etc/ssh/sshd_config:31 setting PubkeyAuthentication yes
debug3: /etc/ssh/sshd_config:35 setting IgnoreRhosts yes
debug3: /etc/ssh/sshd_config:37 setting RhostsRSAAuthentication no
debug3: /etc/ssh/sshd_config:39 setting HostbasedAuthentication no
debug3: /etc/ssh/sshd_config:44 setting PermitEmptyPasswords no
debug3: /etc/ssh/sshd_config:48 setting ChallengeResponseAuthentication no
debug3: /etc/ssh/sshd_config:63 setting X11Forwarding yes
debug3: /etc/ssh/sshd_config:64 setting X11DisplayOffset 10
debug3: /etc/ssh/sshd_config:65 setting PrintMotd no
debug3: /etc/ssh/sshd_config:66 setting PrintLastLog yes
debug3: /etc/ssh/sshd_config:67 setting TCPKeepAlive yes
debug3: /etc/ssh/sshd_config:74 setting AcceptEnv LANG LC_*
debug3: /etc/ssh/sshd_config:76 setting Subsystem sftp /usr/lib/openssh/sftp-server
debug3: /etc/ssh/sshd_config:87 setting UsePAM yes
debug3: /etc/ssh/sshd_config:88 setting AllowUsers noktualek root
debug3: /etc/ssh/sshd_config:89 setting MaxAuthTries 20
debug1: sshd version OpenSSH_6.6.1, OpenSSL 1.0.1f 6 Jan 2014
debug3: [COLOR=#ff0000]Incorrect[/COLOR] RSA1 identifier
debug1: key_parse_private2:[COLOR=#ff0000] missing [/COLOR]begin marker
debug1: read PEM private key done: type RSA
debug3:[COLOR=#ff0000] Incorrect[/COLOR] RSA1 identifier
debug3: [COLOR=#ff0000]Could not load[/COLOR] "/etc/ssh/ssh_host_rsa_key" as a RSA1 public key
debug1: private host key: #0 type 1 RSA
debug3:[COLOR=#ff0000] Incorrect[/COLOR] RSA1 identifier
debug1: key_parse_private2: [COLOR=#ff0000]missing [/COLOR]begin marker
debug1: read PEM private key done: type DSA
debug3: [COLOR=#ff0000]Incorrect[/COLOR] RSA1 identifier
debug3: [COLOR=#ff0000]Could not load [/COLOR]"/etc/ssh/ssh_host_dsa_key" as a RSA1 public key
debug1: private host key: #1 type 2 DSA
debug3:[COLOR=#ff0000] Incorrect[/COLOR] RSA1 identifier
debug1: key_parse_private2: [COLOR=#ff0000]missing[/COLOR] begin marker
debug1: read PEM private key done: type ECDSA
debug3:[COLOR=#ff0000] Incorrect[/COLOR] RSA1 identifier
debug3: [COLOR=#ff0000]Could not load[/COLOR] "/etc/ssh/ssh_host_ecdsa_key" as a RSA1 public key
debug1: private host key: #2 type 3 ECDSA
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug1: rexec_argv[1]='-ddd'
debug3: oom_adjust_setup
Set /proc/self/oom_score_adj from 0 to -1000
debug2: fd 3 setting O_NONBLOCK
debug1: Bind to port 22 on 0.0.0.0.
Server listening on 0.0.0.0 port 22.

[COLOR=#000000]is it correct test[/COLOR]

---

### Post by Lars Noodén on 2015-03-25
It looks like you are posting the file here before you are trying to log in instead of afterwards.  I don't know another way to explain it, but we are trying to see what happens when you try to log in.  But ...

Let's try something else for now.  

If you are willing to start over with a default installation of the SSH server and don't mind getting new keys, then you can remove it, move the directory aside and then reinstall.  

```

service ssh stop
mv /etc/ssh /etc/ssh.old
mkdir -m 755 /etc/ssh
apt-get remove openssh-server
apt-get install openssh-server

```

Then if you've made any customizations to sshd_config you'll have to re-add them, preferably one at a time.

Also, the clients will complain that the host keys have changed but in this case it is ok.

---

### Post by noktualek on 2015-03-25
I try
> service ssh stopmv /etc/ssh /etc/ssh.old
mkdir -m 755 /etc/ssh
apt-get remove openssh-server
apt-get install openssh-server
reboot
login
the result


[IMG]http://upic.me/i/vf/2015-03-26_02-28-49remove.png[/IMG]

[IMG]http://upic.me/i/fg/2015-03-26_02-29-55install.png[/IMG]


[IMG]http://upic.me/i/b4/2015-03-26_02-41-02termi.png[/IMG]

---

### Post by Lars Noodén on 2015-03-25
Ok.  I had suspected as much but this confirms that the problem is neither with your host keys nor with your configuration.  

However, without the output from sshd like in #22 above I can only take fairly blind guesses.  

What happens if you remove all reference to sshd from /etc/hosts.allow and /etc/hosts.deny?

---

### Post by noktualek on 2015-03-25
hosts.allow
[IMG]http://upic.me/i/pl/2015-03-26_02-55-00hosts.allow.png[/IMG]

hosts.deny
[IMG]http://upic.me/i/94/2015-03-26_02-55-37hosts.deny.png[/IMG]

# reboot
login again

try again
[IMG]http://upic.me/i/0t/2015-03-26_02-57-45noktualek.png[/IMG]

> [COLOR=#000000] without the output from sshd like in #22 above[/COLOR]
I don't understand. What should i do ? please explain me step by step or example (my English is poor)
Thousand Thanks. ^^

---

### Post by Lars Noodén on 2015-03-25
My ability to explain is not so good.  You seem to be running the right commands but are jumping ahead to collect the logs before you log in.  You need to collect the logs only after you try to log in.  Or so it looks from here.   

"ssh -ddd" needs to run to completion before you post the output here.  It will run to completion and exit only after you have tried to log in with the client (ssh).  After it has exited naturally should you post the output.  If you copy and post the output before you have tried to log in, then we miss the logs about the log in.

---

### Post by noktualek on 2015-03-25
1 i log in with root user on tty1
# service ssh stop
# /usr/sbin/sshd -ddd 2>&1 | tee /home/noktualek/sshdlog.txt

2 i log in with root user on tty2 (alt+f2)
# ssh localhost -l root

3 copy /home/noktualek/sshdlog.txt to post bellow
> debug2: load_server_config: filename /etc/ssh/sshd_configdebug2: load_server_config: done config len = 735
debug2: parse_server_config: config /etc/ssh/sshd_config len 735
debug3: /etc/ssh/sshd_config:5 setting Port 22
debug3: /etc/ssh/sshd_config:9 setting Protocol 2
debug3: /etc/ssh/sshd_config:11 setting HostKey /etc/ssh/ssh_host_rsa_key
debug3: /etc/ssh/sshd_config:12 setting HostKey /etc/ssh/ssh_host_dsa_key
debug3: /etc/ssh/sshd_config:13 setting HostKey /etc/ssh/ssh_host_ecdsa_key
debug3: /etc/ssh/sshd_config:14 setting HostKey /etc/ssh/ssh_host_ed25519_key
debug3: /etc/ssh/sshd_config:16 setting UsePrivilegeSeparation yes
debug3: /etc/ssh/sshd_config:19 setting KeyRegenerationInterval 3600
debug3: /etc/ssh/sshd_config:20 setting ServerKeyBits 1024
debug3: /etc/ssh/sshd_config:23 setting SyslogFacility AUTH
debug3: /etc/ssh/sshd_config:24 setting LogLevel INFO
debug3: /etc/ssh/sshd_config:27 setting LoginGraceTime 120
debug3: /etc/ssh/sshd_config:28 setting PermitRootLogin without-password
debug3: /etc/ssh/sshd_config:29 setting StrictModes yes
debug3: /etc/ssh/sshd_config:31 setting RSAAuthentication yes
debug3: /etc/ssh/sshd_config:32 setting PubkeyAuthentication yes
debug3: /etc/ssh/sshd_config:36 setting IgnoreRhosts yes
debug3: /etc/ssh/sshd_config:38 setting RhostsRSAAuthentication no
debug3: /etc/ssh/sshd_config:40 setting HostbasedAuthentication no
debug3: /etc/ssh/sshd_config:45 setting PermitEmptyPasswords no
debug3: /etc/ssh/sshd_config:49 setting ChallengeResponseAuthentication no
debug3: /etc/ssh/sshd_config:64 setting X11Forwarding yes
debug3: /etc/ssh/sshd_config:65 setting X11DisplayOffset 10
debug3: /etc/ssh/sshd_config:66 setting PrintMotd no
debug3: /etc/ssh/sshd_config:67 setting PrintLastLog yes
debug3: /etc/ssh/sshd_config:68 setting TCPKeepAlive yes
debug3: /etc/ssh/sshd_config:75 setting AcceptEnv LANG LC_*
debug3: /etc/ssh/sshd_config:77 setting Subsystem sftp /usr/lib/openssh/sftp-server
debug3: /etc/ssh/sshd_config:88 setting UsePAM yes
debug1: sshd version OpenSSH_6.6.1, OpenSSL 1.0.1f 6 Jan 2014
debug3: Incorrect RSA1 identifier
debug1: key_parse_private2: missing begin marker
debug1: read PEM private key done: type RSA
debug3: Incorrect RSA1 identifier
debug3: Could not load "/etc/ssh/ssh_host_rsa_key" as a RSA1 public key
debug1: private host key: #0 type 1 RSA
debug3: Incorrect RSA1 identifier
debug1: key_parse_private2: missing begin marker
debug1: read PEM private key done: type DSA
debug3: Incorrect RSA1 identifier
debug3: Could not load "/etc/ssh/ssh_host_dsa_key" as a RSA1 public key
debug1: private host key: #1 type 2 DSA
debug3: Incorrect RSA1 identifier
debug1: key_parse_private2: missing begin marker
debug1: read PEM private key done: type ECDSA
debug3: Incorrect RSA1 identifier
debug3: Could not load "/etc/ssh/ssh_host_ecdsa_key" as a RSA1 public key
debug1: private host key: #2 type 3 ECDSA
debug3: Incorrect RSA1 identifier
debug3: Incorrect RSA1 identifier
debug3: Could not load "/etc/ssh/ssh_host_ed25519_key" as a RSA1 public key
debug1: private host key: #3 type 4 ED25519
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug1: rexec_argv[1]='-ddd'
debug3: oom_adjust_setup
Set /proc/self/oom_score_adj from 0 to -1000
debug2: fd 3 setting O_NONBLOCK
debug1: Bind to port 22 on 0.0.0.0.
Server listening on 0.0.0.0 port 22.
debug2: fd 4 setting O_NONBLOCK
debug3: sock_set_v6only: set socket 4 IPV6_V6ONLY
debug1: Bind to port 22 on ::.
Server listening on :: port 22.
debug3: fd 5 is not O_NONBLOCK
debug1: Server will not fork when running in debugging mode.
debug3: send_rexec_state: entering fd = 8 config len 735
debug3: ssh_msg_send: type 0
debug3: send_rexec_state: done
debug1: rexec start in 5 out 5 newsock 5 pipe -1 sock 8
debug1: inetd sockets after dupping: 3, 3
Connection from 127.0.0.1 port 35995 on 127.0.0.1 port 22
debug1: Client protocol version 2.0; client software version OpenSSH_6.6.1p1 Ubuntu-2ubuntu2
debug1: match: OpenSSH_6.6.1p1 Ubuntu-2ubuntu2 pat OpenSSH_6.6.1* compat 0x04000000
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.6.1p1 Ubuntu-2ubuntu2
debug2: fd 3 setting O_NONBLOCK
debug2: Network child is on pid 5878
debug3: preauth child monitor started
debug3: privsep user:group 105:65534 [preauth]
debug1: permanently_set_uid: 105/65534 [preauth]
debug1: list_hostkey_types: ssh-rsa,ssh-dss,ecdsa-sha2-nistp256,ssh-ed25519 [preauth]
debug1: SSH2_MSG_KEXINIT sent [preauth]
debug1: SSH2_MSG_KEXINIT received [preauth]
debug2: kex_parse_kexinit: [EMAIL="curve25519-sha256@libssh.org"]curve25519-sha256@libssh.org[/EMAIL],ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1 [preauth]
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss,ecdsa-sha2-nistp256,ssh-ed25519 [preauth]
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se [preauth]
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se [preauth]
debug2: kex_parse_kexinit: [email]hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com[/email],hmac-sha1-96,hmac-md5-96 [preauth]
debug2: kex_parse_kexinit: [email]hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com[/email],hmac-sha1-96,hmac-md5-96 [preauth]
debug2: kex_parse_kexinit: none,zlib@openssh.com [preauth]
debug2: kex_parse_kexinit: none,zlib@openssh.com [preauth]
debug2: kex_parse_kexinit:  [preauth]
debug2: kex_parse_kexinit:  [preauth]
debug2: kex_parse_kexinit: first_kex_follows 0  [preauth]
debug2: kex_parse_kexinit: reserved 0  [preauth]
debug2: kex_parse_kexinit: [EMAIL="curve25519-sha256@libssh.org"]curve25519-sha256@libssh.org[/EMAIL],ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1 [preauth]
debug2: kex_parse_kexinit: [email]ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ssh-ed25519-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-dss-cert-v00@openssh.com[/email],ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-ed25519,ssh-rsa,ssh-dss [preauth]
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se [preauth]
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se [preauth]
debug2: kex_parse_kexinit: [email]hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com[/email],hmac-sha1-96,hmac-md5-96 [preauth]
debug2: kex_parse_kexinit: [email]hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com[/email],hmac-sha1-96,hmac-md5-96 [preauth]
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib [preauth]
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib [preauth]
debug2: kex_parse_kexinit:  [preauth]
debug2: kex_parse_kexinit:  [preauth]
debug2: kex_parse_kexinit: first_kex_follows 0  [preauth]
debug2: kex_parse_kexinit: reserved 0  [preauth]
debug2: mac_setup: setup [EMAIL="hmac-md5-etm@openssh.com"]hmac-md5-etm@openssh.com[/EMAIL] [preauth]
debug1: kex: client->server aes128-ctr [EMAIL="hmac-md5-etm@openssh.com"]hmac-md5-etm@openssh.com[/EMAIL] none [preauth]
debug2: mac_setup: setup [EMAIL="hmac-md5-etm@openssh.com"]hmac-md5-etm@openssh.com[/EMAIL] [preauth]
debug1: kex: server->client aes128-ctr [EMAIL="hmac-md5-etm@openssh.com"]hmac-md5-etm@openssh.com[/EMAIL] none [preauth]
debug1: expecting SSH2_MSG_KEX_ECDH_INIT [preauth]
debug3: mm_key_sign entering [preauth]
debug3: mm_request_send entering: type 6 [preauth]
debug3: mm_key_sign: waiting for MONITOR_ANS_SIGN [preauth]
debug3: mm_request_receive_expect entering: type 7 [preauth]
debug3: mm_request_receive entering [preauth]
debug3: mm_request_receive entering
debug3: monitor_read: checking request 6
debug3: mm_answer_sign
debug3: mm_answer_sign: signature 0x7f69f14839c0(101)
debug3: mm_request_send entering: type 7
debug2: monitor_read: 6 used once, disabling now
debug2: kex_derive_keys [preauth]
debug2: set_newkeys: mode 1 [preauth]
debug1: SSH2_MSG_NEWKEYS sent [preauth]
debug1: expecting SSH2_MSG_NEWKEYS [preauth]
mm_log_handler: write: Broken pipe
debug1: do_cleanup
debug3: PAM: sshpam_thread_cleanup entering


**tty1**
[IMG]http://upic.me/i/ib/2015-03-26_10-20-44tt1.png[/IMG]

**tty2**
[IMG]http://upic.me/i/64/2015-03-26_10-21-30tty2.png[/IMG]



Is it correct process. 
thanks  ^^

---

### Post by Lars Noodén on 2015-03-26
Thanks!  That is the part that shows when the error occurs:

```

debug1: SSH2_MSG_NEWKEYS sent [preauth]
debug1: expecting SSH2_MSG_NEWKEYS [preauth]
mm_log_handler: write: Broken pipe

```

The rest looks normal as far as I know.

However, the error is new to me and I find only one unresolved mention of a similar error in any of the mailing list archives or web pages.  I'm not sure where to look next.

---

### Post by noktualek on 2015-03-26
The problem appear after I reset root password by recovery mode menu. (CD Boot)

Thanks for you advance and your help .

---

