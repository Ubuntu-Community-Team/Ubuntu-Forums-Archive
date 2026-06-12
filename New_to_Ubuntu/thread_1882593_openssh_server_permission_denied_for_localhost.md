---
title: "openssh server permission denied for localhost"
date: 2011-11-17
forum: New to Ubuntu
---

### Post by greendragons on 2011-11-17
I have installed openssh-server.... when i was trying to test with localhost
i got permission denied error

```

kodedozer@KodeWagen:~$ ssh localhost
kodedozer@localhost's password: 
Permission denied, please try again.

kodedozer@KodeWagen:~$ ssh -v kodedozer@localhost
OpenSSH_5.8p1 Debian-1ubuntu3, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: Connection established.
debug1: identity file /home/kodedozer/.ssh/id_rsa type -1
debug1: identity file /home/kodedozer/.ssh/id_rsa-cert type -1
debug1: identity file /home/kodedozer/.ssh/id_dsa type -1
debug1: identity file /home/kodedozer/.ssh/id_dsa-cert type -1
debug1: identity file /home/kodedozer/.ssh/id_ecdsa type -1
debug1: identity file /home/kodedozer/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.8p1 Debian-1ubuntu3
debug1: match: OpenSSH_5.8p1 Debian-1ubuntu3 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.8p1 Debian-1ubuntu3
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA 50:e4:10:cd:2f:d5:11:5d:60:a7:7a:c9:e1:9d:d0:7c
debug1: Host 'localhost' is known and matches the ECDSA host key.
debug1: Found key in /home/kodedozer/.ssh/known_hosts:4
debug1: ssh_ecdsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/kodedozer/.ssh/id_rsa
debug1: Trying private key: /home/kodedozer/.ssh/id_dsa
debug1: Trying private key: /home/kodedozer/.ssh/id_ecdsa
debug1: Next authentication method: password
kodedozer@localhost's password: 

kodedozer@KodeWagen:~$ ssh -v kodedozer@localhost
OpenSSH_5.8p1 Debian-1ubuntu3, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: Connection established.
debug1: identity file /home/kodedozer/.ssh/id_rsa type -1
debug1: identity file /home/kodedozer/.ssh/id_rsa-cert type -1
debug1: identity file /home/kodedozer/.ssh/id_dsa type -1
debug1: identity file /home/kodedozer/.ssh/id_dsa-cert type -1
debug1: identity file /home/kodedozer/.ssh/id_ecdsa type -1
debug1: identity file /home/kodedozer/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.8p1 Debian-1ubuntu3
debug1: match: OpenSSH_5.8p1 Debian-1ubuntu3 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.8p1 Debian-1ubuntu3
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA 50:e4:10:cd:2f:d5:11:5d:60:a7:7a:c9:e1:9d:d0:7c
debug1: Host 'localhost' is known and matches the ECDSA host key.
debug1: Found key in /home/kodedozer/.ssh/known_hosts:4
debug1: ssh_ecdsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/kodedozer/.ssh/id_rsa
debug1: Trying private key: /home/kodedozer/.ssh/id_dsa
debug1: Trying private key: /home/kodedozer/.ssh/id_ecdsa
debug1: Next authentication method: password
kodedozer@localhost's password: 
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
kodedozer@localhost's password: 
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.


```
Why it is not letting me connect as im entering correct password

Thnx!!

---

