---
title: "Internal SSH works, External SSH has connection issues"
date: 2013-03-21
forum: New to Ubuntu
---

### Post by nbpradford on 2013-03-21
Let me outline the situation for you, desktop A running Ubuntu 12.04, and laptop B running Ubuntu 12.04.  No firewalls (atm), all ports (22, and 2200) are being forwarded by router to Desktop A.  I know my external IP (curl ifconfig.me), and my sshd_config is

```
 Package generated configuration file
# See the sshd_config(5) manpage for details

# What ports, IPs and protocols we listen for
Port 2200
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
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
#AuthorizedKeysFile     %h/.ssh/authorized_keys
``` 

so when I try ```
ssh <username>@<public IP> -p 2200 
```
laptop B on my schools network is unable to connect to desktop A.  I know this is an issue on my side because I used to be running an Amahi HDA server on this exact desktop and was able to easily SSH out of my schools network on to it.  But now since I took away all the HDA baggage with a fresh install of Ubuntu 12.04 LTS I can't connect from an external network anymore.  I really have no idea at this point why this would be happening, so I'm out of ideas on how to fix it.

---

### Post by Cheesemill on 2013-03-21
Can you post the output of...
```
ssh -vvv <username>@<public IP> -p 2200
```
This will give us alot more information about where the issue could be.

---

### Post by nbpradford on 2013-03-21
Funny you say that, I was just working with that.

```
ssh -vvv <username>@<external ip> -p 2200 
``` returns

```


Starting Nmap 5.21 ( http://nmap.org ) at 2013-03-21 12:14 EDT
Note: Host seems down. If it is really up, but blocking our ping probes, try -PN
Nmap done: 1 IP address (0 hosts up) scanned in 3.06 seconds


$ ssh -vvv <username>@<external ip> -p 2200
OpenSSH_5.9p1 Debian-5ubuntu1, OpenSSL 1.0.1 14 Mar 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to <external ip> [external ip] port 2200.
debug1: connect to address <external ip> port 2200: Connection timed out
ssh: connect to host <external ip> port 2200: Connection timed out

```


I left in the nmap scan of the IP to show you those results, I know for a fact that host is not down, and there is no firewall that would be blocking this scan.

Here's the ssh_config file to, as the debug shows the ssh calling for it, i thought you might request to see it.
```

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
#   Port 2200
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
#   VisualHostKey no
#   ProxyCommand ssh -q -W %h:%p gateway.example.com
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no


```

---

### Post by nbpradford on 2013-03-21
I also just tried to ping my external IP and found out it is unable to do so. Any ideas on why this might have worked before and not now?

---

### Post by CharlesA on 2013-03-21
If you are trying to access your external IP address from inside the network, that might not work.

You can run a check at [http://canyouseeme.org/](http://canyouseeme.org/) to see if they show port 2200 open.

If they don't show it as open, check your port forwarding rules.

---

### Post by nbpradford on 2013-03-21
no I am testing this from outside of my local network, and on my router my ports are all being forwarded correctly to the desktop.

---

### Post by papibe on 2013-03-21
Hi nbpradford.

Did you restart your ssh service after changing the port from 22 to 2200?

Regards.

---

### Post by Cheesemill on 2013-03-21
Maybe your school has changed their network policy and are now blocking outgoing pings and ssh connections.

It's definitely worth checking with your school's network admin and also with your ISP, they may have changed something as well.

The results of your verbose ssh attempt and your nmap scan clearly point to a network issue of some sort between you and your public IP.

---

### Post by nbpradford on 2013-03-21
@ papibe: yes i did a ssh restart when I changed the ports from 22 to 2200

@ cheesemill I know my school didn't do this because I'm quite close with my schools IT and was able to ask them and also just last week I was able to SSH and VPN into this same server on the same public IP, except at that time it was running Amahis HDA ([https://www.amahi.org/](https://www.amahi.org/)).  I did n't want to install the amahi hda again, but it looks like to get this working I'm going to have to.  Oh well.  Would it matter that the HDA was working as my DNS server before, and now the router is being the DNS server.  I know I changed the router back after to the DNS server as I set the router back to factory defaults, and checked to see if it was on.  

Thanks all for the help, if anything its making me look at the problem from different angles.

---

### Post by nbpradford on 2013-03-21
I also just remembered that i've tested this also via my phone.  So my phone network to cable network can not connect to the ssh client.  So you would then have to assume it's an issue either with my ISP provider (though i don't see them changing something like that in a matter of a day or two), or my router configuration, right?

---

### Post by Cheesemill on 2013-03-21
Silly question, but are you ***absolutely*** sure you have the correct external IP address?

If you don't pay for a static IP with your ISP there is a chance it may have changed since you last did 'curl ifconfig.me'.

---

### Post by nbpradford on 2013-03-21
no such thing as a silly question, and yes the external IP i'm using was curl'd today.  Now I'm finding out that after my external ip, there is some extra "notes" you could say. It looks like <external ip>.dhcp.davl.<state>.<ISP>.com  I've never noticed this before but this would have no affect on a ssh connection right?

---

### Post by nbpradford on 2013-03-21
To note, when I ssh into the server my terminal will "act" like its connected display the username and IP address it's connected to.  I didn't know if this was a sign that the laptop was communicating with my desktop, or it was all being done on the laptop.

---

### Post by CharlesA on 2013-03-21
> **nbpradford said:**
> To note, when I ssh into the server my terminal will "act" like its connected display the username and IP address it's connected to.  I didn't know if this was a sign that the laptop was communicating with my desktop, or it was all being done on the laptop.

If you successfully ssh into another machine, the prompt should look like:

```
remoteuser@remotehost
```

---

### Post by nbpradford on 2013-03-21
Well i figured out my issue, but i'm to embarassed to tell ya'll what I was doing wrong.  Thanks all for the help, in the end some of ya'll did end up helping me out a bunch!

---

### Post by papibe on 2013-03-21
> **nbpradford said:**
> Well i figured out my issue
You don't have to share it, but IMHO it would help other users that are trying to attempt the same task.

Best Regards.

---

