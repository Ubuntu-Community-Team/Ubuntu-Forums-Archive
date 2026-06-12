---
title: "[SOLVED] config files"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by ub007 on 2008-09-05
Hi,

I tried to remove ssh with all of the configuration files(messed with the configurations and wanted restore to the defualt state)

code:
sudo apt-get remove -purge ssh

However the configuration files remained the same,So i did

rm -rf /etc/ssh/ssh_config
rm -rf /etc/ssh/sshd_config

then reinstalled ssh

sudo apt-get install ssh

now i find the config files 
 /etc/ssh/ssh_config
 /etc/ssh/sshd_config are both empty

Could anyone tell me how to get this sorted out?

cheers
david

---

### Post by brian_p on 2008-09-05
> **ub007 said:**
> 

Did this yesterday:

```
sudo apt-get remove --purge openssh-server openssh-client openssh-blacklist

```

```
sudo apt-get install openssh-server openssh-client
```

Note: --purge not -purge. And there is no package called ssh.

---

### Post by Pro-reason on 2008-09-05
/etc/ssh/ssh_config
```
# This is the ssh client system-wide configuration file.  See
# ssh_config(5) for more information.  This file provides defaults for
# users, and the values can be changed in per-user configuration files
# or on the command line.

# Configuration data is parsed as follows:
#  1. command line options
#  2. user-specific file
#  3. system-wide file
# Any configuration value is only changed the first time it is set.
# Thus, host-specific definitions should be at the beginning of the
# configuration file, and defaults at the end.

# Site-wide defaults for some commonly used options.  For a comprehensive
# list of available options, their meanings and defaults, please see the
# ssh_config(5) man page.

Host *
#   ForwardAgent no
#   ForwardX11 no
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   GSSAPIAuthentication no
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange no
#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   Port 22
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no

```


/etc/ssh/sshd_config
```

# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
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
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
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

UsePAM yes

```

---

### Post by OffAxis on 2008-09-05
> **brian_p said:**
> Did this yesterday:
 And there is no package called ssh.

There didn't used to be, but there is now (in hardy); the openssh package (which used to be the meta-package for both the client and server) now goes by the name 'ssh'.

[http://packages.ubuntu.com/source/hardy/openssh](http://packages.ubuntu.com/source/hardy/openssh)

---

### Post by Pro-reason on 2008-09-05
That package *ssh* exists in Hardy, but it is just a meta-package that pulls in *openssh-client* and *openssh-server*.

Purging it will do nothing.  The real packages must be purged.

---

### Post by ub007 on 2008-09-05
> sudo apt-get remove --purge openssh-server openssh-client openssh-blacklist

This does the job.Thanks all of you

---

