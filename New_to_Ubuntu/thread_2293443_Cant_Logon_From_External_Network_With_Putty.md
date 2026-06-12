---
title: "Cant Logon From External Network With Putty"
date: 2015-09-05
forum: New to Ubuntu
---

### Post by crypto430 on 2015-09-05
Hi, I am new to ubuntu and very glad I found this forum.  Anyways, I am an experienced IT professional with little to no linux experience.  So I researched and decided to install ubuntu 14.04 on a home server.  So far, so good.  I can use Putty to logon from my home network, however when I attempt to logon from work or any other network outside my home, I get "Access Denied".

 Now, I think I've read every post on this subject on the net and still haven't solved the issue.  When I look at my auth.log file, I see the logon and immediate logoff.  So it seems I successfully logon and then immediately get logged off without a clue as to what is happening.  I am also posting my sshd_config file.  Any and all help would be extremely appreciated. Thanks in advance.

**_Version_**
```
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:        14.04
Codename:       trusty
```

**_auth.log_**
```
crypto430@linux:/var/log$ tail auth.log
Sep  4 05:47:20 linux sshd[13632]: Server listening on 0.0.0.0 port 22.
Sep  4 05:47:20 linux sshd[13632]: Server listening on :: port 22.
Sep  4 05:47:20 linux sudo: pam_unix(sudo:session): session closed for user root
Sep  4 05:55:20 linux sudo: crypto430 : TTY=pts/1 ; PWD=/etc/ssh ; USER=root ; COMMAND=/usr/sbin/service sshd restart
Sep  4 05:55:20 linux sudo: pam_unix(sudo:session): session opened for user root by crypto430(uid=0)
Sep  4 05:55:20 linux sudo: pam_unix(sudo:session): session closed for user root
Sep  4 06:17:01 linux CRON[13868]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep  4 06:17:01 linux CRON[13868]: pam_unix(cron:session): session closed for user root
Sep  4 06:25:01 linux CRON[13913]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep  4 06:27:29 linux CRON[13913]: pam_unix(cron:session): session closed for user root
```

**_sshd_config_**
```
# Package generated configuration file
# See the sshd_config(5) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
HostKey /etc/ssh/ssh_host_ed25519_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 1024

# Logging
SyslogFacility AUTH
LogLevel VERBOSE

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile     %h/.ssh/authorized_keys

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
 PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes

AllowUsers root crypto430@*
AllowUsers root crypto430
```

---

### Post by steeldriver on 2015-09-05
Hello and welcome to the forums

I don't see anything in your auth.log that suggests you are getting successfully logged on and then immediately logged off - you should see something like

```

pam_unix(sshd:session): session opened for user xxxx
pam_unix(sshd:session): session closed for user xxxx

```

Are you sure you have set up the correct port forwarding across your router? BTW do you have a static public IP?

---

### Post by cdh79 on 2015-09-05
the auth.log logons/logoffs are from cron, not from sshd..

i agree with steeldriver, check the port-forwarding on the router, to make sure all incoming traffic on port 22 are being forwarded to the correct server-IP

---

### Post by crypto430 on 2015-09-05
Thanks for the reply.  Are you saying this is not me being logged on?  I setup the admin user as crypto430.

[COLOR=#000000]Sep 4 05:55:20 linux sudo: pam_unix(sudo:session): session opened for user root by crypto430(uid=0)[/COLOR]
[COLOR=#000000]Sep 4 05:55:20 linux sudo: pam_unix(sudo:session): session closed for user root[/COLOR]

---

### Post by steeldriver on 2015-09-05
Correct - that would be PAM authenticating the preceding '/usr/sbin/service sshd restart' command (run using 'sudo')

---

### Post by HermanAB on 2015-09-05
You should first debug the network issues, then the ssh issues (if any).

A good tool for network trouble shooting is the ancient telnet program:
$ telnet ip.ad.dre.ss 22

You should get the SSH server banner.

Once you got that to work, try ssh with verbose error messages:
$ ssh -vvv [email]user@ip.ad.dre.ss[/email]

---

### Post by crypto430 on 2015-09-06
Yes, I am familiar with telnet :) and got the banner.  For whatever reason, it doesn't seem to accept the password which I know is correct from logging on locally.  So here is the SSH logon attempt with verbose error messages:

```
crypto430@linux:~$ ssh -vvv crypto430@108.61.228.114
OpenSSH_6.6.1, OpenSSL 1.0.1f 6 Jan 2014
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 108.61.228.114 [108.61.228.114] port 22.
debug1: Connection established.
debug1: identity file /home/crypto430/.ssh/id_rsa type -1
debug1: identity file /home/crypto430/.ssh/id_rsa-cert type -1
debug1: identity file /home/crypto430/.ssh/id_dsa type -1
debug1: identity file /home/crypto430/.ssh/id_dsa-cert type -1
debug1: identity file /home/crypto430/.ssh/id_ecdsa type -1
debug1: identity file /home/crypto430/.ssh/id_ecdsa-cert type -1
debug1: identity file /home/crypto430/.ssh/id_ed25519 type -1
debug1: identity file /home/crypto430/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.6.1p1 Ubuntu-2ubuntu2.3
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.9p1 Debian-5ubuntu1.7
debug1: match: OpenSSH_5.9p1 Debian-5ubuntu1.7 pat OpenSSH_5* compat 0x0c000000
debug2: fd 3 setting O_NONBLOCK
debug3: load_hostkeys: loading entries for host "108.61.228.114" from file "/home/crypto430/.ssh/known_hosts"
debug3: load_hostkeys: loaded 0 keys
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: [email]curve25519-sha256@libssh.org[/email],ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: [email]ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ssh-ed25519-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-dss-cert-v00@openssh.com[/email],ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-ed25519,ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: [email]hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com[/email],hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: [email]hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com[/email],hmac-sha1-96,hmac-md5-96
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
debug2: mac_setup: setup hmac-md5
debug1: kex: server->client aes128-ctr hmac-md5 none
debug2: mac_setup: setup hmac-md5
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA 00:4e:89:c7:85:58:c6:5f:59:d9:f1:ce:a5:8c:7c:d7
debug3: load_hostkeys: loading entries for host "108.61.228.114" from file "/home/crypto430/.ssh/known_hosts"
debug3: load_hostkeys: loaded 0 keys
The authenticity of host '108.61.228.114 (108.61.228.114)' can't be established.
ECDSA key fingerprint is 00:4e:89:c7:85:58:c6:5f:59:d9:f1:ce:a5:8c:7c:d7.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '108.61.228.114' (ECDSA) to the list of known hosts.
debug1: ssh_ecdsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/crypto430/.ssh/id_rsa ((nil)),
debug2: key: /home/crypto430/.ssh/id_dsa ((nil)),
debug2: key: /home/crypto430/.ssh/id_ecdsa ((nil)),
debug2: key: /home/crypto430/.ssh/id_ed25519 ((nil)),
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/crypto430/.ssh/id_rsa
debug3: no such identity: /home/crypto430/.ssh/id_rsa: No such file or directory
debug1: Trying private key: /home/crypto430/.ssh/id_dsa
debug3: no such identity: /home/crypto430/.ssh/id_dsa: No such file or directory
debug1: Trying private key: /home/crypto430/.ssh/id_ecdsa
debug3: no such identity: /home/crypto430/.ssh/id_ecdsa: No such file or directory
debug1: Trying private key: /home/crypto430/.ssh/id_ed25519
debug3: no such identity: /home/crypto430/.ssh/id_ed25519: No such file or directory
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
crypto430@108.61.228.114's password:
debug3: packet_send2: adding 48 (len 64 padlen 16 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
crypto430@108.61.228.114's password:
```

---

### Post by QIII on 2015-09-06
Hello, crypto430.

Please use code tags.  They preserve formatting and make your posts easier to read.

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.


Cheers!

---

### Post by crypto430 on 2015-09-06
Thank you for the tips QIII, I will certainly adhere to that advice going forward.  I'm now happy to report this issue is resolved.  It appears this was a comedy of errors on my part. The biggest issue was the laptop I'm using is connected to one of my proxy servers.  So, my real IP address was actually disguised and I was apparently trying to log into the proxy server :( Once I corrected that, I got a timeout. I then checked my port forwarding and I was forwarding to the prior local IP address my linux was running on before I rebooted my router.

I would like to thank everyone who took the time to help me out on this issue.  It was your advice and guidance that got me to logically retrace my steps to debug this issue.  I'm glad I found this forum and it's nice knowing people take time out of their busy lives to help completely anonymous people.  Hopefully I get to the point where some day I will be a be able to provide others with help.

I will now mark this thread SOLVED.

Kind Regards,
Crypto430

---

