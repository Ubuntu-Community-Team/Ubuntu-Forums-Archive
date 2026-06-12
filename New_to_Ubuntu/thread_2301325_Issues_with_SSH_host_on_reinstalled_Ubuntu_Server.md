---
title: "Issues with SSH host on reinstalled Ubuntu Server"
date: 2015-11-01
forum: New to Ubuntu
---

### Post by eddiefiggie on 2015-11-01
I had my Ubuntu Server (14.04) working just fine with my laptop connecting with an authentication key.    After I reinstalled my server, I can't seem to create a new key that actually works.  Key keeps getting denied.

After scouring the Internet, I can't seem to find a solution.  I've used the seahorse application as well...  Gave that a go.  Created a key seemingly successfully but my server denied that one as well.

Any insight to this issue would be great!

---

### Post by sandyd on 2015-11-01
Hi, can you check the following:

a) SSH Client Verbose Output

You can get the SSH Client verbose output by adding -vvv after typing ssh.

For example:
```

ssh -vvv root@192.168.2.2
```

b) SSH Logs on server

Not sure if you still have access to the server, but you can view the logs at /var/log/auth.log.

Post any errors you find.

---

### Post by eddiefiggie on 2015-11-01
When I run:

```
ssh -vvv root@server
```

I get the following in the terminal session:

```
      OpenSSH_6.6.1, OpenSSL 1.0.1f 6 Jan 2014 
 debug1: Reading configuration data /etc/ssh/ssh_config 
 debug1: /etc/ssh/ssh_config line 19: Applying options for * 
 debug2: ssh_connect: needpriv 0 
 debug1: Connecting to SERVER [10.9.8.7] port 22. 
 debug1: Connection established. 
 debug3: Incorrect RSA1 identifier 
 debug3: Could not load "/home/user/.ssh/id_rsa" as a RSA1 public key 
 debug1: identity file /home/user/.ssh/id_rsa type 1 
 debug1: identity file /home/user/.ssh/id_rsa-cert type -1 
 debug1: identity file /home/user/.ssh/id_dsa type -1 
 debug1: identity file /home/user/.ssh/id_dsa-cert type -1 
 debug1: identity file /home/user/.ssh/id_ecdsa type -1 
 debug1: identity file /home/user/.ssh/id_ecdsa-cert type -1 
 debug1: identity file /home/user/.ssh/id_ed25519 type -1 
 debug1: identity file /home/user/.ssh/id_ed25519-cert type -1 
 debug1: Enabling compatibility mode for protocol 2.0 
 debug1: Local version string SSH-2.0-OpenSSH_6.6.1p1 Ubuntu-2ubuntu2.3 
 debug1: Remote protocol version 2.0, remote software version OpenSSH_6.6.1p1 Ubuntu-2ubuntu2.3 
 debug1: match: OpenSSH_6.6.1p1 Ubuntu-2ubuntu2.3 pat OpenSSH_6.6.1* compat 0x04000000 
 debug2: fd 3 setting O_NONBLOCK 
 debug3: load_hostkeys: loading entries for host "SERVER" from file "/home/user/.ssh/known_hosts" 
 debug3: load_hostkeys: found key type ECDSA in file /home/user/.ssh/known_hosts:2 
 debug3: load_hostkeys: loaded 1 keys 
 debug3: order_hostkeyalgs: prefer hostkeyalgs: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521 
 debug1: SSH2_MSG_KEXINIT sent 
 debug1: SSH2_MSG_KEXINIT received 
 debug2: kex_parse_kexinit: curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1 
 debug2: kex_parse_kexinit: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-ed25519-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-dss-cert-v00@openssh.com,ssh-ed25519,ssh-rsa,ssh-dss 
 debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se 
 debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se 
 debug2: kex_parse_kexinit: hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96 
 debug2: kex_parse_kexinit: hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96 
 debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib 
 debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib 
 debug2: kex_parse_kexinit:  
 debug2: kex_parse_kexinit:  
 debug2: kex_parse_kexinit: first_kex_follows 0  
 debug2: kex_parse_kexinit: reserved 0  
 debug2: kex_parse_kexinit: curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1 
 debug2: kex_parse_kexinit: ssh-rsa,ssh-dss,ecdsa-sha2-nistp256,ssh-ed25519 
 debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se 
 debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se 
 debug2: kex_parse_kexinit: hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96 
 debug2: kex_parse_kexinit: hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96 
 debug2: kex_parse_kexinit: none,zlib@openssh.com 
 debug2: kex_parse_kexinit: none,zlib@openssh.com 
 debug2: kex_parse_kexinit:  
 debug2: kex_parse_kexinit:  
 debug2: kex_parse_kexinit: first_kex_follows 0  
 debug2: kex_parse_kexinit: reserved 0  
 debug2: mac_setup: setup hmac-md5-etm@openssh.com 
 debug1: kex: server->client aes128-ctr hmac-md5-etm@openssh.com none 
 debug2: mac_setup: setup hmac-md5-etm@openssh.com 
 debug1: kex: client->server aes128-ctr hmac-md5-etm@openssh.com none 
 debug1: sending SSH2_MSG_KEX_ECDH_INIT 
 debug1: expecting SSH2_MSG_KEX_ECDH_REPLY 
 debug1: Server host key: ECDSA 44:25:77:91:de:a8:48:b4:3f:fe:20:42:87:c9:dc:8b 
 debug3: load_hostkeys: loading entries for host "SERVER" from file "/home/user/.ssh/known_hosts" 
 debug3: load_hostkeys: found key type ECDSA in file /home/user/.ssh/known_hosts:2 
 debug3: load_hostkeys: loaded 1 keys 
 debug3: load_hostkeys: loading entries for host "10.9.8.7" from file "/home/user/.ssh/known_hosts" 
 debug3: load_hostkeys: found key type ECDSA in file /home/user/.ssh/known_hosts:1 
 debug3: load_hostkeys: loaded 1 keys 
 debug1: Host 'SERVER' is known and matches the ECDSA host key. 
 debug1: Found key in /home/user/.ssh/known_hosts:2 
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
 debug2: key: /home/user/.ssh/id_rsa (0x7f58a91ee8b0), 
 debug2: key: /home/user/.ssh/id_dsa ((nil)), 
 debug2: key: /home/user/.ssh/id_ecdsa ((nil)), 
 debug2: key: /home/user/.ssh/id_ed25519 ((nil)), 
 debug1: Authentications that can continue: publickey,password 
 debug3: start over, passed a different list publickey,password 
 debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password 
 debug3: authmethod_lookup publickey 
 debug3: remaining preferred: keyboard-interactive,password 
 debug3: authmethod_is_enabled publickey 
 debug1: Next authentication method: publickey 
 debug1: Offering RSA public key: /home/user/.ssh/id_rsa 
 debug3: send_pubkey_test 
 debug2: we sent a publickey packet, wait for reply 
 debug1: Server accepts key: pkalg ssh-rsa blen 535 
 debug2: input_userauth_pk_ok: fp 5e:a6:b9:81:9a:43:31:3b:85:bc:14:fd:ee:ec:50:de 
 debug3: sign_and_send_pubkey: RSA 5e:a6:b9:81:9a:43:31:3b:85:bc:14:fd:ee:ec:50:de 
 Agent admitted failure to sign using the key. 
 debug1: Trying private key: /home/user/.ssh/id_dsa 
 debug3: no such identity: /home/user/.ssh/id_dsa: No such file or directory 
 debug1: Trying private key: /home/user/.ssh/id_ecdsa 
 debug3: no such identity: /home/user/.ssh/id_ecdsa: No such file or directory 
 debug1: Trying private key: /home/user/.ssh/id_ed25519 
 debug3: no such identity: /home/user/.ssh/id_ed25519: No such file or directory 
 debug2: we did not send a packet, disable method 
 debug3: authmethod_lookup password 
 debug3: remaining preferred: ,password 
 debug3: authmethod_is_enabled password 
 debug1: Next authentication method: password 
 

 

 

 

 



```

After logging in this way, here are the lines from my auth.log:

```
     Nov  1 19:39:21 server sshd[4269]: pam_unix(sshd:session): session closed for user user 
 Nov  1 19:39:21 server sudo: pam_unix(sudo:session): session closed for user root 
 Nov  1 19:39:28 server sshd[4308]: Set /proc/self/oom_score_adj to 0 
 Nov  1 19:39:28 server sshd[4308]: Connection from 10.9.8.6 port 40761 on 10.9.8.7 port 22 
 Nov  1 19:39:29 server sshd[4308]: Postponed publickey for user from 10.9.8.6 port 40761 ssh2 [preauth] 
 Nov  1 19:39:32 server sshd[4308]: pam_ecryptfs: pam_sm_authenticate: /home/user is already mounted 
 Nov  1 19:39:32 server sshd[4308]: Accepted password for user from 10.9.8.6 port 40761 ssh2: RSA 5e:a6:b9:81:9a:43:31:3b:85:bc:14:fd$ 
 Nov  1 19:39:32 server sshd[4308]: pam_unix(sshd:session): session opened for user user by (uid=0) 
 Nov  1 19:39:32 server sshd[4308]: User child is on pid 4327 
 Nov  1 19:39:32 server sshd[4327]: Starting session: shell on pts/0 for user from 10.9.8.6 port 40761 
 Nov  1 19:39:38 server sudo: user : TTY=pts/0 ; PWD=/home/user ; USER=root ; COMMAND=/usr/bin/nano /var/log/auth.log 
 Nov  1 19:39:38 server sudo: pam_unix(sudo:session): session opened for user root by user(uid=0) 




```

For good measure, here's my sshd_config:

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
LoginGraceTime 30
PermitRootLogin without-password
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile      %h/.ssh/authorized_keys
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

#MaxStartups 2:30:10
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







```

---

### Post by sandyd on 2015-11-02
Here we go```

      OpenSSH_6.6.1, OpenSSL 1.0.1f 6 Jan 2014 
 debug1: Reading configuration data /etc/ssh/ssh_config 
 debug1: /etc/ssh/ssh_config line 19: Applying options for * 
 debug2: ssh_connect: needpriv 0 
 debug1: Connecting to SERVER [10.9.8.7] port 22. 
 debug1: Connection established. 
 debug3: Incorrect RSA1 identifier 
 debug3: Could not load "/home/user/.ssh/id_rsa" as a RSA1 public key 
 debug1: identity file /home/user/.ssh/id_rsa type 1 
 debug1: identity file /home/user/.ssh/id_rsa-cert type -1 
 debug1: identity file /home/user/.ssh/id_dsa type -1 
 debug1: identity file /home/user/.ssh/id_dsa-cert type -1 
 debug1: identity file /home/user/.ssh/id_ecdsa type -1 
 debug1: identity file /home/user/.ssh/id_ecdsa-cert type -1 
 debug1: identity file /home/user/.ssh/id_ed25519 type -1 
 debug1: identity file /home/user/.ssh/id_ed25519-cert type -1 
 debug1: Enabling compatibility mode for protocol 2.0 
 debug1: Local version string SSH-2.0-OpenSSH_6.6.1p1 Ubuntu-2ubuntu2.3 
 debug1: Remote protocol version 2.0, remote software version OpenSSH_6.6.1p1 Ubuntu-2ubuntu2.3 
 debug1: match: OpenSSH_6.6.1p1 Ubuntu-2ubuntu2.3 pat OpenSSH_6.6.1* compat 0x04000000 
 debug2: fd 3 setting O_NONBLOCK 
 debug3: load_hostkeys: loading entries for host "SERVER" from file "/home/user/.ssh/known_hosts" 
 debug3: load_hostkeys: found key type ECDSA in file /home/user/.ssh/known_hosts:2 
 debug3: load_hostkeys: loaded 1 keys 
 debug3: order_hostkeyalgs: prefer hostkeyalgs: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521 
 debug1: SSH2_MSG_KEXINIT sent 
 debug1: SSH2_MSG_KEXINIT received 
 debug2: kex_parse_kexinit: curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1 
 debug2: kex_parse_kexinit: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-ed25519-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-dss-cert-v00@openssh.com,ssh-ed25519,ssh-rsa,ssh-dss 
 debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se 
 debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se 
 debug2: kex_parse_kexinit: hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96 
 debug2: kex_parse_kexinit: hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96 
 debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib 
 debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib 
 debug2: kex_parse_kexinit:  
 debug2: kex_parse_kexinit:  
 debug2: kex_parse_kexinit: first_kex_follows 0  
 debug2: kex_parse_kexinit: reserved 0  
 debug2: kex_parse_kexinit: curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1 
 debug2: kex_parse_kexinit: ssh-rsa,ssh-dss,ecdsa-sha2-nistp256,ssh-ed25519 
 debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se 
 debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se 
 debug2: kex_parse_kexinit: hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96 
 debug2: kex_parse_kexinit: hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96 
 debug2: kex_parse_kexinit: none,zlib@openssh.com 
 debug2: kex_parse_kexinit: none,zlib@openssh.com 
 debug2: kex_parse_kexinit:  
 debug2: kex_parse_kexinit:  
 debug2: kex_parse_kexinit: first_kex_follows 0  
 debug2: kex_parse_kexinit: reserved 0  
 debug2: mac_setup: setup hmac-md5-etm@openssh.com 
 debug1: kex: server->client aes128-ctr hmac-md5-etm@openssh.com none 
 debug2: mac_setup: setup hmac-md5-etm@openssh.com 
 debug1: kex: client->server aes128-ctr hmac-md5-etm@openssh.com none 
 debug1: sending SSH2_MSG_KEX_ECDH_INIT 
 debug1: expecting SSH2_MSG_KEX_ECDH_REPLY 
 debug1: Server host key: ECDSA 44:25:77:91:de:a8:48:b4:3f:fe:20:42:87:c9:dc:8b 
 debug3: load_hostkeys: loading entries for host "SERVER" from file "/home/user/.ssh/known_hosts" 
 debug3: load_hostkeys: found key type ECDSA in file /home/user/.ssh/known_hosts:2 
 debug3: load_hostkeys: loaded 1 keys 
 debug3: load_hostkeys: loading entries for host "10.9.8.7" from file "/home/user/.ssh/known_hosts" 
 debug3: load_hostkeys: found key type ECDSA in file /home/user/.ssh/known_hosts:1 
 debug3: load_hostkeys: loaded 1 keys 
 debug1: Host 'SERVER' is known and matches the ECDSA host key. 
 debug1: Found key in /home/user/.ssh/known_hosts:2 
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
 debug2: key: /home/user/.ssh/id_rsa (0x7f58a91ee8b0), 
 debug2: key: /home/user/.ssh/id_dsa ((nil)), 
 debug2: key: /home/user/.ssh/id_ecdsa ((nil)), 
 debug2: key: /home/user/.ssh/id_ed25519 ((nil)), 
 debug1: Authentications that can continue: publickey,password 
 debug3: start over, passed a different list publickey,password 
 debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password 
 debug3: authmethod_lookup publickey 
 debug3: remaining preferred: keyboard-interactive,password 
 debug3: authmethod_is_enabled publickey 
 debug1: Next authentication method: publickey 
 debug1: Offering RSA public key: /home/user/.ssh/id_rsa 
 debug3: send_pubkey_test 
 debug2: we sent a publickey packet, wait for reply 
 debug1: Server accepts key: pkalg ssh-rsa blen 535 
 debug2: input_userauth_pk_ok: fp 5e:a6:b9:81:9a:43:31:3b:85:bc:14:fd:ee:ec:50:de 
 debug3: sign_and_send_pubkey: RSA 5e:a6:b9:81:9a:43:31:3b:85:bc:14:fd:ee:ec:50:de 
** Agent admitted failure to sign using the key. **
 debug1: Trying private key: /home/user/.ssh/id_dsa 
 debug3: no such identity: /home/user/.ssh/id_dsa: No such file or directory 
 debug1: Trying private key: /home/user/.ssh/id_ecdsa 
 debug3: no such identity: /home/user/.ssh/id_ecdsa: No such file or directory 
 debug1: Trying private key: /home/user/.ssh/id_ed25519 
 debug3: no such identity: /home/user/.ssh/id_ed25519: No such file or directory 
 debug2: we did not send a packet, disable method 
 debug3: authmethod_lookup password 
 debug3: remaining preferred: ,password 
 debug3: authmethod_is_enabled password 
 debug1: Next authentication method: password
```
The issue is bolded above.

Are you using ssh-add to add the keys by any chance?

If so, just run ```

ssh-add
``` on your current PC (where you are running the client).

ssh-copy-id will also work.

---

### Post by Lars Noodén on 2015-11-02
> **eddiefiggie said:**
> 
```

 Nov  1 19:39:32 server sshd[4308]: pam_ecryptfs: pam_sm_authenticate: /home/user is already mounted 

```

Or do you now have an encrypted home directory?  If so, you will have to set *sshd_config* to provide an alternate location for *authorized_keys*, one outside the home directory.

---

### Post by eddiefiggie on 2015-11-02
> **sandyd said:**
> 
Are you using ssh-add to add the keys by any chance?

If so, just run ```

ssh-add
``` on your current PC (where you are running the client).

ssh-copy-id will also work.

I'm 75% I did this.  So to isolate this however, tonight I'll give it a go and post the results.


> **Lars Noodén said:**
> Or do you now have an encrypted home directory? If so, you will have to set *sshd_config* to provide an alternate location for *authorized_keys*, one outside the home directory.

Interesting that you bring this up.  For starters, I don't know if I encrypted my client or not.  I do recall the question in the installation process for my client, but can't recall if I did this.  Is there a way to find out?  My client laptop has nothing critical on it, I do clean installs on it quite regularly.  Mostly for self education and learning.

That being said, I has my KEY working from that same laptop installation connecting to the SSH server before I reinstalled the server.  So, since I didn't have to remap the path within the sshd_config then, I'm certain that's not the issue.  Thanks though!  This is definitely something to look out for in the future.

---

### Post by Lars Noodén on 2015-11-02
The client 's encryption won't affect anything but if the server now has an encrypted home you'll have to work around that.  Can you log in with a password and, staying logged in, can you then log in with keys from another terminal?  If you can use keys in that situation but not others then that would suggest that the server has an encrypted home directory.  [AuthorizedKeysFile](http://manpages.ubuntu.com/manpages/trusty/en/man5/sshd_config.5.html) can take multiple values.

```

AuthorizedKeysFile     %h/.ssh/authorized_keys     /etc/ssh/keys/%u/authorized_keys

```

---

### Post by SeijiSensei on 2015-11-02
What is the rationale for having an encrypted file system on a server?  If the server is up and running 24/7, then the filesystem will always be unencrypted.  The only thing encryption might protect against is someone physically removing the hard drive from the server.  If that's a real threat, you need to find a new location to house the server.

I think people just choose the encryption option during installation because it sounds cool and "secure."  I could see using encrypted file systems on a laptop which might be stolen.  For most other use cases, it doesn't make a whole lot sense to me.  I'm open to being enlightened however.

---

### Post by eddiefiggie on 2015-11-03
100% the issue was the fact that the server encryption was in the way.  Darn, I feel like I just regained 10 years of my life back.  Finding the problem (or having this community point it out for me) is so fulfilling!  hehe

Thanks for the support everyone.




.[COLOR=#000000]  [/COLOR]

---

