---
title: "SSH issue"
date: 2018-09-04
forum: New to Ubuntu
---

### Post by Nezmin2 on 2018-09-04
Alright guy's, I really need some common sense step by step help. I have installed Ubuntu LTS Server (18.04) on a VirtualBox VM. I have set up my ip address and I am able to ping it from my win10 machine. I have verified that OpenSSH-Server is running and I have set port 22 in the sshd_config file. I still cannot connect using putty. I have spent many day's scouring the web for answers but nothing has worked. (This machine will sit on my host and run as a minecraft server for me to play on. There will not be anyone else connecting to it)

---

### Post by steeldriver on 2018-09-04
Did you configure the VM's networking mode as bridged or NAT? if it is NAT, you will need to forward port 22 across it (just like you would with a physical router)

---

### Post by Nezmin2 on 2018-09-04
I have tried both but have settled on bridge

---

### Post by aromo2 on 2018-09-04
Try:
```
telnet 10.10.10.10  22
```
(assuming 10.10.10.10 is the IP of your SSH server)

That will tell you if the SSH daemon is listening and accepting connections

NOTE: to exit from telnet press [FONT=courier new]Ctrl[/FONT] [FONT=courier new]][/FONT]

---

### Post by Nezmin2 on 2018-09-04
Results:
[ATTACH=CONFIG]280986[/ATTACH]


Now how to I exit telnet? The ctrl ] didn't take me back to cmd prompt

---

### Post by Nezmin2 on 2018-09-06
So Telnet connected, but I don't know what that means. I can ping the VM's ip and connect with Telnet, but not with SSH. What am I doing wrong?

---

### Post by cariboo on 2018-09-07
Try:

```
ssh -vv user@server
```

it should show you an error.

---

### Post by jdeiros on 2018-09-08
Try this command and paste the outcome to us? ```
netstat -lnt
```

The output you are looking for needs to show that your device is listening locally on :22

Also, you should run a ```
cat /etc/services
``` in the terminal and read that the device has the correct port/protocol combination.

---

### Post by Nezmin2 on 2018-09-08
here is the output of netstat -lnt

[ATTACH=CONFIG]281025[/ATTACH]

I ran the cat command but there is so much info I can't print screen it. How do I have it show a page at a time?

---

### Post by Nezmin2 on 2018-09-10
Anyone?

---

### Post by jdeiros on 2018-09-11
> **Nezmin2 said:**
> here is the output of netstat -lnt

[ATTACH=CONFIG]281025[/ATTACH]

I ran the cat command but there is so much info I can't print screen it. How do I have it show a page at a time?

It says your PC is listening on port 22 from anything; can you SSH into yourself with via ```
ssh -l nez 127.0.0.1
``` 

Try a ```
sudo service --status-all
``` and see that SSH has a [+] to ensure it's online.

I am assuming here but I  find it so weird that you have the VM on the same PC via bridge and should you  do an ```
ip addr
``` from your Linux box and ```
ipconfig
``` (i'm assuming you're on Windows) and should they both be on the same subnet you  should literally have no network issues...

---

### Post by jdeiros on 2018-09-11
> **cariboo said:**
> Try:

```
ssh -vv user@server
```

it should show you an error.

You should try this, too. It's a debug mode; the person who posted this knows much more than us and more could probably help you if you post the output :)

---

### Post by QIII on 2018-09-11
Would you please post the entirety of your sshd_config file (redact anything you are worried about posting)?

Please enclose the text in code tags.  Images can be hard to read, and posting between code tags will allow others to copy the text and make suggested changes in their posts.

Either:

1.  Click the # button above the text entry box, place your cursor between the code tags that appear and paste your text.  Alternatively, paste your text, highlight it and click the #.

2.  Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] following it.  The square brackets are required.

---

### Post by Nezmin2 on 2018-09-15
So, I ran all of the tests that you advised. I am now able to ssh in, but only after removing the comments from:

Port 22
AddressFamily any
ListenAddress 0.0.0.0
ListenAddress ::



```

#$OpenBSD: sshd_config,v 1.101 2017/03/14 07:19:07 djm Exp $


# This is the sshd server system-wide configuration file.  See
# sshd_config(5) for more information.


# This sshd was compiled with PATH=/usr/bin:/bin:/usr/sbin:/sbin


# The strategy used for options in the default sshd_config shipped with
# OpenSSH is to specify options with their default value where
# possible, but leave them commented.  Uncommented options override the
# default value.


Port 22
AddressFamily any
ListenAddress 0.0.0.0
ListenAddress ::


#HostKey /etc/ssh/ssh_host_rsa_key
#HostKey /etc/ssh/ssh_host_ecdsa_key
#HostKey /etc/ssh/ssh_host_ed25519_key


# Ciphers and keying
#RekeyLimit default none


# Logging
#SyslogFacility AUTH
#LogLevel INFO


# Authentication:


#LoginGraceTime 2m
PermitRootLogin no
PasswordAuthentication yes
AllowUsers nez
#StrictModes yes
#MaxAuthTries 6
#MaxSessions 10


#PubkeyAuthentication yes


# Expect .ssh/authorized_keys2 to be disregarded by default in future.
#AuthorizedKeysFile     .ssh/authorized_keys .ssh/authorized_keys2


#AuthorizedPrincipalsFile none


#AuthorizedKeysCommand none
#AuthorizedKeysCommandUser nobody



# For this to work you will also need host keys in /etc/ssh/ssh_known_hosts
#HostbasedAuthentication no
# Change to yes if you don't trust ~/.ssh/known_hosts for
# HostbasedAuthentication
#IgnoreUserKnownHosts no
# Don't read the user's ~/.rhosts and ~/.shosts files
#IgnoreRhosts yes


# To disable tunneled clear text passwords, change to no here!
#PasswordAuthentication yes
#PermitEmptyPasswords no


# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no


# Kerberos options
#KerberosAuthentication no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes
#KerberosGetAFSToken no


# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes
#GSSAPIStrictAcceptorCheck yes
#GSSAPIKeyExchange no


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


#AllowAgentForwarding yes
#AllowTcpForwarding yes
#GatewayPorts no
X11Forwarding yes
#X11DisplayOffset 10
#X11UseLocalhost yes
#PermitTTY yes
PrintMotd no
#PrintLastLog yes
#TCPKeepAlive yes
#UseLogin no
#PermitUserEnvironment no
#Compression delayed
#ClientAliveInterval 0
#ClientAliveCountMax 3
#UseDNS no
#PidFile /var/run/sshd.pid
#MaxStartups 10:30:100
#PermitTunnel no
#ChrootDirectory none
#VersionAddendum none


# no default banner path
#Banner none


# Allow client to pass locale environment variables
AcceptEnv LANG LC_*


# override default of no subsystems
Subsystem       sftp    /usr/lib/openssh/sftp-server


# Example of overriding settings on a per-user basis
#Match User anoncvs
#       X11Forwarding no
#       AllowTcpForwarding no
#       PermitTTY no
#       ForceCommand cvs server




```


[EDITED SECTION] I actually have no idea why it worked here as I am unable to reproduce it and it is no longer working.

---

### Post by Nezmin2 on 2018-09-21
Dammit...Ok guys, I have a brand new (fresh install of Ubuntu Server LTS 18.04) vps running in VirtualBox. I have updated, upgraded, and added the extensions pack for VB. The install comes with openssh-server pre-installed and it's running. I have a static ip set as 192.168.1.16/27. It can ping itself and google. I can ping the machine from the host (not the guest to host though). When I run the ufw status cmd it is listening to the port that I set in the sshd_config file and ufw. both netplan and ip addr show the correct ip address. However, I am just not able to ssh into it. I have been searching the web and youtube for the process and they all show how simple it's supposed to be, but nothing works for me.

The error that I keep getting is "Connection failed. FlowSocketConnector: Failed to connect to target address. Windows error 10061: No connection could be made because the target machine actively refused it."

This server will not be exposed publicly. It will stay running on the host and act as a Minecraft server for a single player. Could someone please tell me what I am missing. I have also gone through all the direction from those who have posted to this thread. Still nothing...I'm very frustrated.

Thanks...

---

