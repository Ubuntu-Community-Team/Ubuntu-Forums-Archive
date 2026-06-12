---
title: "Cannot ssh as user"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by victorbrca on 2008-07-25
I'm having a problem on a Ubuntu box where I cannot ssh as the main user. I'm able to ssh as root and as a chroot user. I can also do 'ssh user@127.0.0.1' on the problematic box.

The only thing I did different was change the IP scope on my network and install SmoothWall3 on another box.

There are no rules on hosts.allow, hosts.deny or sshd_config.

```
$ ssh-server 
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to xx.xx.xx.xx [xx.xx.xx.xx] port 22.
debug1: Connection established.
debug1: identity file /home/victor/.ssh/identity type -1
debug1: identity file /home/victor/.ssh/id_rsa type -1
debug1: identity file /home/victor/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-5ubuntu1
debug1: match: OpenSSH_4.3p2 Debian-5ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'xx.xx.xx.xx' is known and matches the RSA host key.
debug1: Found key in /home/victor/.ssh/known_hosts:2
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering public key: 
debug1: Server accepts key: pkalg ssh-rsa blen 277
Connection closed by xx.xx.xx.xx
```


Any ideas??

---

### Post by SNuxoll on 2008-07-25
That's because sshd is a system service, you don't run it as a user.

---

### Post by victorbrca on 2008-07-25
> **SNuxoll said:**
> That's because sshd is a system service, you don't run it as a user.

I'm not trying to start the sshd service. What I'm using is an alise:

> ssh-server

# is the same as

ssh -v [email]user@xx.xx.xx.xx[/email]

---

### Post by sp0nge on 2008-07-25
Let's try to simplify. Can you log in via: 

```
ssh user@XXX.XXX.X.XXX
```

:confused:

---

### Post by victorbrca on 2008-07-25
> **sp0nge said:**
> Let's try to simplify. Can you log in via: 

```
ssh user@XXX.XXX.X.XXX
```

:confused:

No... at least not with the user I'm having problems.

I should also mentioned that I blew my known_hosts on both machines. It asks if I want to accept the key rsa key and them gives me the same error msg "Connection closed by xx.xx.xx.xx".

---

