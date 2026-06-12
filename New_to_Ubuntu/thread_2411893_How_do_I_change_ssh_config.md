---
title: "How do I change ssh_config?"
date: 2019-02-05
forum: New to Ubuntu
---

### Post by sawaix on 2019-02-05
I failed ssh, and it showed message of ssh_config.
How do I change ssh_config?


<-------------------------- OS  -------------------------->


onany@ubuntu:~$ cat /etc/os-release 
NAME="Ubuntu"
VERSION="16.04.5 LTS (Xenial Xerus)"




<-------------------------- Symptoms  -------------------------->


Onany@ubuntu:~$  ssh root@192.168.254.10
/etc/ssh/ssh_config: line 56: Bad configuration option: permitrootlogin
/etc/ssh/ssh_config: terminating, 1 bad configuration options




<-------------------------- status  -------------------------->


onany@ubuntu:~$ service ssh status
&#9679; ssh.service - OpenBSD Secure Shell server
   Loaded: loaded (/lib/systemd/system/ssh.service; enabled; vendor preset: ena
   Active: active (running) since Tue 2019-02-05 22:01:43 JST; 8min ago
 Main PID: 5471 (sshd)
   CGroup: /system.slice/ssh.service
           &#9492;&#9472;5471 /usr/sbin/sshd -D




<-------------------------- ssh_config  -------------------------->


{# This is the ssh client system-wide configuration file.  See}
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
#   IdentityFile ~/.ssh/id_ecdsa
#   IdentityFile ~/.ssh/id_ed25519
    Port 22
#   Protocol 2
#   Cipher 3des
#   Ciphers aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
#   VisualHostKey no
#   ProxyCommand ssh -q -W %h:%p gateway.example.com
#   RekeyLimit 1G 1h
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no
    PermitRootLogin yes

---

### Post by TheFu on 2019-02-05
Please use *code tags*, so things line up.

ssh_config is the client-side config file. Everything inside there can be overruled by ~/.ssh/config file. It is preferred to leave the system file alone and only modify the per-userid file instead.

sshd_config is the server-side config file.  This controls the behavior of the sshd daemon.  It has a manpage which describes the available options.

In general, the root account doesn't allow direct logins on ubuntu systems. This is part of the Ubuntu security philosophy.  Allowing remote root is a really bad idea.

So, I see this error:
```
/etc/ssh/ssh_config: line 56: Bad configuration option: permitrootlogin
```
The client config file doesn't control the sshd.  Perhaps you meant to modify the sshd_config file?  I would also suggest that you use ssh-keys for authentication for remote root needs AND that you restrict the source IPs from which those connections are allowed.
```
PermitRootLogin without-password
```
or perhaps:
```
PasswordAuthentication no
ChallengeResponseAuthentication no
Match Address 10.0.0.0/8,172.16.0.0/12,192.168.0.0/16
    PasswordAuthentication yes
``` so only internal LANs get to attempt using passwords, but never over the internet.  These are all sshd_config settings.

Lastly, consider using **sudoedit** for a safe way to edit the files. There are multiple reasons why this is best over other options, especially if a GUI editor is preferred.

---

### Post by sawaix on 2019-02-06
I get it. Thank you!

---

