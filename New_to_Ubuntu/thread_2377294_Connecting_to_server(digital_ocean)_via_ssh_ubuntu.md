---
title: "Connecting to server(digital ocean) via ssh ubuntu 17 / Host key verification failed"
date: 2017-11-11
forum: New to Ubuntu
---

### Post by smoestar on 2017-11-11
Hello! I'm fairly new to all of this, and i have recently rented a droplet. I'm trying to connect to the droplet via SSH on my ubuntu, but i keep getting error messages - and i've googled my ass of without getting any smarter.
sidenote before i post the errormessags: It worked perfectly fine on my desktop(win 10, putty)
I've deleted the droplet and createt several new keys and tried over and over again. On my current droplet i have not been able to connect at all via ssh. I have not tried windows.
I do not have a known hosts file.


Please dear linux gods. Show me the way.
ssh -vv root@ip gives me:
```
OpenSSH_7.5p1 Ubuntu-10, OpenSSL 1.0.2g  1 Mar 2016
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: resolving "198.211.123.63" port 22
debug2: ssh_connect_direct: needpriv 0
debug1: Connecting to 198.211.123.63 [198.211.123.63] port 22.
debug1: Connection established.
debug1: identity file /home/sverre/.ssh/id_rsa type 1
debug1: key_load_public: No such file or directory
debug1: identity file /home/sverre/.ssh/id_rsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/sverre/.ssh/id_dsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/sverre/.ssh/id_dsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/sverre/.ssh/id_ecdsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/sverre/.ssh/id_ecdsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/sverre/.ssh/id_ed25519 type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/sverre/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_7.5p1 Ubuntu-10
debug1: Remote protocol version 2.0, remote software version OpenSSH_7.2p2 Ubuntu-4ubuntu2.2
debug1: match: OpenSSH_7.2p2 Ubuntu-4ubuntu2.2 pat OpenSSH* compat 0x04000000
debug2: fd 3 setting O_NONBLOCK
debug1: Authenticating to 198.211.123.63:22 as 'root'
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: local client KEXINIT proposal
debug2: KEX algorithms: curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha256,diffie-hellman-group14-sha1,ext-info-c
debug2: host key algorithms: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ssh-ed25519-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-ed25519,rsa-sha2-512,rsa-sha2-256,ssh-rsa
debug2: ciphers ctos: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com,aes128-cbc,aes192-cbc,aes256-cbc
debug2: ciphers stoc: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com,aes128-cbc,aes192-cbc,aes256-cbc
debug2: MACs ctos: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: MACs stoc: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: compression ctos: none,zlib@openssh.com,zlib
debug2: compression stoc: none,zlib@openssh.com,zlib
debug2: languages ctos: 
debug2: languages stoc: 
debug2: first_kex_follows 0 
debug2: reserved 0 
debug2: peer server KEXINIT proposal
debug2: KEX algorithms: curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha1
debug2: host key algorithms: ssh-rsa,rsa-sha2-512,rsa-sha2-256,ecdsa-sha2-nistp256,ssh-ed25519
debug2: ciphers ctos: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: ciphers stoc: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: MACs ctos: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: MACs stoc: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: compression ctos: none,zlib@openssh.com
debug2: compression stoc: none,zlib@openssh.com
debug2: languages ctos: 
debug2: languages stoc: 
debug2: first_kex_follows 0 
debug2: reserved 0 
debug1: kex: algorithm: curve25519-sha256@libssh.org
debug1: kex: host key algorithm: ecdsa-sha2-nistp256
debug1: kex: server->client cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
debug1: kex: client->server cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ecdsa-sha2-nistp256 SHA256:Rw7hDMScFl+1Og3XLsxE5MlXV/ctjv7WSvKy6y/mTuY
The authenticity of host '198.211.123.63 (198.211.123.63)' can't be established.
ECDSA key fingerprint is SHA256:Rw7hDMScFl+1Og3XLsxE5MlXV/ctjv7WSvKy6y/mTuY.
Are you sure you want to continue connecting (yes/no)? 
Host key verification failed.
```

---

### Post by The Cog on 2017-11-12
Looking at the last-but-one line in your post, it says Are you sure you want to continue connecting. It should stop at that point and wait for you to say yes. Did it not stop? Did you say no? 

Essentially, it is saying that it hasn't spoken to this host before so it can't check that the host's fingerprint hasn't changed. You need to say yes, and it will then add this fingerprint to known-hosts and will check that the identity hasn't changed in future.

---

