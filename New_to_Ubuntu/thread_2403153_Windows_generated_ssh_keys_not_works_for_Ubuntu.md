---
title: "Windows generated ssh keys not works for Ubuntu"
date: 2018-10-08
forum: New to Ubuntu
---

### Post by raakh5 on 2018-10-08
Hello,

I have generated a key on windows with SSH Secure Shell client. Its working fine from windows but not working at all on Ubuntu system. 
Here is log:
```
OpenSSH_7.6p1 Ubuntu-4, OpenSSL 1.0.2n  7 Dec 2017debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: resolving "163.170.18.15" port 22
debug2: ssh_connect_direct: needpriv 0
debug1: Connecting to 163.170.18.15 [163.170.18.15] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/gsw type 1
debug1: key_load_public: No such file or directory
debug1: identity file /root/.ssh/gsw-cert type -1
debug1: Local version string SSH-2.0-OpenSSH_7.6p1 Ubuntu-4
debug1: Remote protocol version 2.0, remote software version OpenSSH_7.4
debug1: match: OpenSSH_7.4 pat OpenSSH* compat 0x04000000
debug2: fd 3 setting O_NONBLOCK
debug1: Authenticating to 163.170.18.15:22 as 'linux'
debug3: put_host_port: [163.170.18.15]:22
debug3: hostkeys_foreach: reading file "/root/.ssh/known_hosts"
debug3: record_hostkey: found key type ECDSA in file /root/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys from [163.170.18.15]:22
debug3: order_hostkeyalgs: prefer hostkeyalgs: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521
debug3: send packet: type 20
debug1: SSH2_MSG_KEXINIT sent
debug3: receive packet: type 20
debug1: SSH2_MSG_KEXINIT received
debug2: local client KEXINIT proposal
debug2: KEX algorithms: curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha256,diffie-hellman-group14-sha1,ext-info-c
debug2: host key algorithms: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-ed25519-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com,ssh-ed25519,rsa-sha2-512,rsa-sha2-256,ssh-rsa
debug2: ciphers ctos: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: ciphers stoc: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: MACs ctos: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: MACs stoc: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: compression ctos: none,zlib@openssh.com,zlib
debug2: compression stoc: none,zlib@openssh.com,zlib
debug2: languages ctos: 
debug2: languages stoc: 
debug2: first_kex_follows 0 
debug2: reserved 0 
debug2: peer server KEXINIT proposal
debug2: KEX algorithms: curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha256,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: host key algorithms: ssh-rsa,rsa-sha2-512,rsa-sha2-256,ecdsa-sha2-nistp256,ssh-ed25519
debug2: ciphers ctos: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com,aes128-cbc,aes192-cbc,aes256-cbc,blowfish-cbc,cast128-cbc,3des-cbc
debug2: ciphers stoc: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com,aes128-cbc,aes192-cbc,aes256-cbc,blowfish-cbc,cast128-cbc,3des-cbc
debug2: MACs ctos: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: MACs stoc: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: compression ctos: none,zlib@openssh.com
debug2: compression stoc: none,zlib@openssh.com
debug2: languages ctos: 
debug2: languages stoc: 
debug2: first_kex_follows 0 
debug2: reserved 0 
debug1: kex: algorithm: curve25519-sha256
debug1: kex: host key algorithm: ecdsa-sha2-nistp256
debug1: kex: server->client cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
debug1: kex: client->server cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
debug3: send packet: type 30
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug3: receive packet: type 31
debug1: Server host key: ecdsa-sha2-nistp256 SHA256:eP+lKxsh4c9g6nVjdHNXWIAO6Suq/n9wL1lFUeAuwIA
debug3: put_host_port: [163.170.18.15]:22
debug3: put_host_port: [163.170.18.15]:22
debug3: hostkeys_foreach: reading file "/root/.ssh/known_hosts"
debug3: record_hostkey: found key type ECDSA in file /root/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys from [163.170.18.15]:22
debug3: hostkeys_foreach: reading file "/root/.ssh/known_hosts"
debug3: record_hostkey: found key type ECDSA in file /root/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys from [163.170.18.15]:22
debug1: Host '[163.170.18.15]:22' is known and matches the ECDSA host key.
debug1: Found key in /root/.ssh/known_hosts:1
debug3: send packet: type 21
debug2: set_newkeys: mode 1
debug1: rekey after 134217728 blocks
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug3: receive packet: type 21
debug1: SSH2_MSG_NEWKEYS received
debug2: set_newkeys: mode 0
debug1: rekey after 134217728 blocks
debug1: Skipping ssh-dss key /root/.ssh/gsw - not in PubkeyAcceptedKeyTypes
debug3: send packet: type 5
debug3: receive packet: type 7
debug1: SSH2_MSG_EXT_INFO received
debug1: kex_input_ext_info: server-sig-algs=<rsa-sha2-256,rsa-sha2-512>
debug3: receive packet: type 6
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug3: send packet: type 50
debug3: receive packet: type 51
debug1: Authentications that can continue: publickey,gssapi-keyex,gssapi-with-mic
debug3: start over, passed a different list publickey,gssapi-keyex,gssapi-with-mic
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup gssapi-keyex
debug3: remaining preferred: gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_is_enabled gssapi-keyex
debug1: Next authentication method: gssapi-keyex
debug1: No valid Key exchange context
debug2: we did not send a packet, disable method
debug3: authmethod_lookup gssapi-with-mic
debug3: remaining preferred: publickey,keyboard-interactive,password
debug3: authmethod_is_enabled gssapi-with-mic
debug1: Next authentication method: gssapi-with-mic
debug1: Unspecified GSS failure.  Minor code may provide more information
No Kerberos credentials available (default cache: FILE:/tmp/krb5cc_0)


debug1: Unspecified GSS failure.  Minor code may provide more information
No Kerberos credentials available (default cache: FILE:/tmp/krb5cc_0)


debug2: we did not send a packet, disable method
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
linux@163.170.18.15: Permission denied (publickey,gssapi-keyex,gssapi-with-mic).
root@sti ~/.ssh# 

```

---

### Post by DuckHook on 2018-10-08
Welcome to the forums, raakh5.

A wild-eyed guess would be that your key contains characters that are illegal in Linux. This is usually caused by Windows inheriting the MSDOS  convention of <CR> +<LF> versus Linux's standalone <LF>. Explanation and solution here: [http://www.cs.toronto.edu/~krueger/csc209h/tut/line-endings.html](http://www.cs.toronto.edu/~krueger/csc209h/tut/line-endings.html)

There are a vast number of other possible issues. Since you do not describe in detail what you did to add your SSH keys, where you added them, etc, it is impossible to help you with such skimpy information. I note that you may have activated the root account, which in itself is very bad practice. Therefore, you may be handling SSH inappropriately from the start.

---

### Post by sp40140 on 2018-10-08
You need to change the "end of line" characters. The key is always in single line. The thing is when you transfer the file from Win to Unix system (or other way around), you need to account for different line break characters.

---

