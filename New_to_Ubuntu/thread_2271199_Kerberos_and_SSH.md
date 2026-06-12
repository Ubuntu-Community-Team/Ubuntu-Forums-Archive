---
title: "Kerberos and SSH"
date: 2015-03-28
forum: New to Ubuntu
---

### Post by SLuffy on 2015-03-28
hello everybody ! i'm using kerberos in order to use the password only when i log from "kinit user" and i want to log in from this user with ssh but i keep getting "Permission denied (publickey,gssapi-keyex,gssapi-with-mic,password)." I tried all the forums but i didn't get any solution. 
this is the output of ssh -v user@server
> root@s1:/home/sara# ssh -vv 192.168.0.2OpenSSH_6.6.1, OpenSSL 1.0.1f 6 Jan 2014
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.0.2 [192.168.0.2] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/id_rsa type 1
debug1: identity file /root/.ssh/id_rsa-cert type -1
debug1: identity file /root/.ssh/id_dsa type -1
debug1: identity file /root/.ssh/id_dsa-cert type -1
debug1: identity file /root/.ssh/id_ecdsa type -1
debug1: identity file /root/.ssh/id_ecdsa-cert type -1
debug1: identity file /root/.ssh/id_ed25519 type -1
debug1: identity file /root/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.6.1p1 Ubuntu-2ubuntu2
debug1: Remote protocol version 2.0, remote software version OpenSSH_6.6.1p1 Ubuntu-2ubuntu2
debug1: match: OpenSSH_6.6.1p1 Ubuntu-2ubuntu2 pat OpenSSH_6.6.1* compat 0x04000000
debug2: fd 3 setting O_NONBLOCK
debug1: Offering GSSAPI proposal: gss-gex-sha1-toWM5Slw5Ew8Mqkay+al2g==,gss-group1-sha1-toWM5Slw5Ew8Mqkay+al2g==,gss-group14-sha1-toWM5Slw5Ew8Mqkay+al2g==,gss-gex-sha1-A/vxljAEU54gt9a48EiANQ==,gss-group1-sha1-A/vxljAEU54gt9a48EiANQ==,gss-group14-sha1-A/vxljAEU54gt9a48EiANQ==,gss-gex-sha1-bontcUwnM6aGfWCP21alxQ==,gss-group1-sha1-bontcUwnM6aGfWCP21alxQ==,gss-group14-sha1-bontcUwnM6aGfWCP21alxQ==,gss-gex-sha1-eipGX3TCiQSrx573bT1o1Q==,gss-group1-sha1-eipGX3TCiQSrx573bT1o1Q==,gss-group14-sha1-eipGX3TCiQSrx573bT1o1Q==
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: gss-gex-sha1-toWM5Slw5Ew8Mqkay+al2g==,gss-group1-sha1-toWM5Slw5Ew8Mqkay+al2g==,gss-group14-sha1-toWM5Slw5Ew8Mqkay+al2g==,gss-gex-sha1-A/vxljAEU54gt9a48EiANQ==,gss-group1-sha1-A/vxljAEU54gt9a48EiANQ==,gss-group14-sha1-A/vxljAEU54gt9a48EiANQ==,gss-gex-sha1-bontcUwnM6aGfWCP21alxQ==,gss-group1-sha1-bontcUwnM6aGfWCP21alxQ==,gss-group14-sha1-bontcUwnM6aGfWCP21alxQ==,gss-gex-sha1-eipGX3TCiQSrx573bT1o1Q==,gss-group1-sha1-eipGX3TCiQSrx573bT1o1Q==,gss-group14-sha1-eipGX3TCiQSrx573bT1o1Q==,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: [email]ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-ed25519-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-dss-cert-v00@openssh.com[/email],ssh-ed25519,ssh-rsa,ssh-dss,null
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
debug2: kex_parse_kexinit: gss-gex-sha1-toWM5Slw5Ew8Mqkay+al2g==,gss-group1-sha1-toWM5Slw5Ew8Mqkay+al2g==,gss-group14-sha1-toWM5Slw5Ew8Mqkay+al2g==,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss,ecdsa-sha2-nistp256,ssh-ed25519
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: [email]hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com[/email],hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: [email]hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com[/email],hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: mac_setup: setup [email]hmac-md5-etm@openssh.com[/email]
debug1: kex: server->client aes128-ctr [email]hmac-md5-etm@openssh.com[/email] none
debug2: mac_setup: setup [email]hmac-md5-etm@openssh.com[/email]
debug1: kex: client->server aes128-ctr [email]hmac-md5-etm@openssh.com[/email] none
debug1: Doing group exchange


debug2: bits set: 1523/3072
debug1: Calling gss_init_sec_context
debug1: Delegating credentials
debug1: Received GSSAPI_COMPLETE
debug1: Calling gss_init_sec_context
debug1: Delegating credentials
debug2: bits set: 1559/3072
debug1: Rekey has happened - updating saved versions
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
debug2: key: /root/.ssh/id_rsa (0x7f16cb58e780),
debug2: key: /root/.ssh/id_dsa ((nil)),
debug2: key: /root/.ssh/id_ecdsa ((nil)),
debug2: key: /root/.ssh/id_ed25519 ((nil)),
debug1: Authentications that can continue: publickey,gssapi-keyex,gssapi-with-mic,password
debug1: Next authentication method: gssapi-keyex
debug2: we sent a gssapi-keyex packet, wait for reply
debug1: Authentications that can continue: publickey,gssapi-keyex,gssapi-with-mic,password
debug2: we did not send a packet, disable method
debug1: Next authentication method: gssapi-with-mic
debug2: we sent a gssapi-with-mic packet, wait for reply
debug1: Authentications that can continue: publickey,gssapi-keyex,gssapi-with-mic,password
debug2: we sent a gssapi-with-mic packet, wait for reply
debug1: Authentications that can continue: publickey,gssapi-keyex,gssapi-with-mic,password
debug2: we sent a gssapi-with-mic packet, wait for reply
debug1: Authentications that can continue: publickey,gssapi-keyex,gssapi-with-mic,password
debug2: we sent a gssapi-with-mic packet, wait for reply
debug1: Authentications that can continue: publickey,gssapi-keyex,gssapi-with-mic,password
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey,gssapi-keyex,gssapi-with-mic,password).
If anyone knows how can I fix the problem or from where i'm getting it please help :)

---

### Post by chopra on 2015-03-28
Are you logged in as root on your local machine when you kinit and ssh?  I'm not sure why you would want to do that, as that leaves your system quite vulnerable.  You should be doing these commands as yourself, not root.
 But here's some tips:
kinit <user> is your username on the remote host, and if it's different from you local username, you have to do:
 ssh -l <remote_username> <remote_host>  
or
ssh <remote_username>@<remote_host>

for it to recognize your ticket.  You should also execute the kinit and ssh commands as the same user on your local machine, or it will not work. The permission denied indicates that it isn't accepting your ticket, which can mean either you local username (which appears to be root in your case) or your remote username are not what it's expecting.
 You can also do the command:
klist
in order to see whether you have a valid ticket owned by the user you're logged in to you local machine as.

---

