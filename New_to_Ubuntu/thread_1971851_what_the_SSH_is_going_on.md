---
title: "what the SSH is going on?"
date: 2012-05-03
forum: New to Ubuntu
---

### Post by wlraider70 on 2012-05-03
I am having an ssh nightmare, I have not idea what I am doing wrong. So i just started over, here are my steps.




First
```

Luke@Cygwin ~
$ ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (/home/Luke/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/Luke/.ssh/id_rsa.
Your public key has been saved in /home/Luke/.ssh/id_rsa.pub.
The key fingerprint is:
----------------------------- Luke@Cygwin
The key's randomart image is:
+--[ RSA 2048]----+


```

Second

```

Luke@Cygwin ~
$ ssh-copy-id -i id_rsa.pub "server@xxx.xxx.xxx.xxx (not a porn site) -p 2222"
server@x's password:
Now try logging into the machine, with "ssh 'server@x -p 2222'", and check in:

  ~/.ssh/authorized_keys

to make sure we haven't added extra keys that you weren't expecting.


```



last
 
```

Luke@Cygwin ~/.ssh
$ ssh server@x -p 2222 -i ~/.ssh/id_rsa -vv
OpenSSH_5.9p1, OpenSSL 0.9.8t 18 Jan 2012
debug2: ssh_connect: needpriv 0
debug1: Connecting to xxx port 2222.
debug1: Connection established.
debug1: identity file /home/Luke/.ssh/id_rsa type 1
debug1: identity file /home/Luke/.ssh/id_rsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.8p1 Debian-7ubuntu1
debug1: match: OpenSSH_5.8p1 Debian-7ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.9
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-dss-cert-v00@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss,ecdsa-sha2-nistp256
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-ctr hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA dc:3e:53:21:bd:40:ca:5f:c1:00:8d:4b:c0:66:83:61
debug1: checking without port identifier
The authenticity of host '[x]:2222 ([x]:2222)' can't be established.
ECDSA key fingerprint is dc:3e:53:21:bd:40:ca:5f:c1:00:8d:4b:c0:66:83:61.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '[x]:2222' (ECDSA) to the list of known hosts.
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
debug2: key: /home/Luke/.ssh/id_rsa (0x80046fb0)
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/Luke/.ssh/id_rsa
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug2: we did not send a packet, disable method
debug1: Next authentication method: password
server@2x's password:
debug2: we sent a password packet, wait for reply
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
server@x's password:
debug2: we sent a password packet, wait for reply
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
server@x's password:
debug2: we sent a password packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey,password).

```

What am I missing, I've been at this so long, I could be missing something VERY obvious.

---

### Post by jerome1232 on 2012-05-03
My first thought (although this isn't mentioned in your output) is to check the permisions on your key file, it should be readable to the owner only. 

For example these are the permissions on my key file

```
-rw-------  1 jeremy jeremy  771 Dec 16 10:19 id_dsa
```

---

### Post by wlraider70 on 2012-05-03
i think i did these, but 

fourth,
```


Luke@Cygwin ~/.ssh
$ chmod 600 ~/.ssh/authorized_keys

Luke@Cygwin ~/.ssh
$ chmod 700 ~/.ssh

Luke@Cygwin ~/.ssh
$ chmod go-w ~/


```

NO CHANGE

---

### Post by papibe on 2012-05-03
Hi wlraider70.

By any chance do you have your /home partition encrypted?

Regards.

---

### Post by wlraider70 on 2012-05-03
Home is not encrypted.

---

### Post by jerome1232 on 2012-05-03
okay, taking a closer look at your output and comparing to my succesful login I see this key difference


```
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/jeremy/.ssh/id_rsa
debug1: Trying private key: /home/jeremy/.ssh/id_dsa

```


```
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/Luke/.ssh/id_rsa
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug2: we did not send a packet, disable method
debug1: Next authentication method: password

```

It seems you are offering a public key when you should be offering a private key, but id_rsa should be a private key so now I am as confused as you are.

---

### Post by wlraider70 on 2012-05-03
Could that be because I specified the key in my command? I know that -i works. My hope was to elimiante and misconfiguration in the ssh_config realm by listing the key in the command.

---

### Post by jerome1232 on 2012-05-03
Perhaps this is a case of the blind leading the blind! I tried specifying with -i as well and I got output more similar to yours

```
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering DSA public key: .ssh/id_dsa
debug2: we sent a publickey packet, wait for reply
debug1: Server accepts key: pkalg ssh-dss blen 434

```

Now I am suspecting that the server is rejecting your key, if you log on with the password method you can check auth.log (grep it for sshd) for clues as to why it's rejecting the key, if that is the case.

---

### Post by papibe on 2012-05-03
Could you post the result of this command on the server?
```
sudo tail /var/log/auth.log
```
Regards.

---

### Post by wlraider70 on 2012-05-03
I have both password and RSA keys enabled.
This doesn't seem helpful to me

```



May  3 00:04:39 philo sshd[11476]: Failed password for server from ... port 16216 ssh2
May  3 00:04:39 philo sshd[11476]: Failed password for server from x port 16216 ssh2
May  3 00:05:10 philo sshd[11479]: Failed password for server from x8 port 16217 ssh2
May  3 00:05:10 philo sshd[11479]: Failed password for server from x port 16217 ssh2
May  3 00:09:15 philo sshd[11496]: Failed password for server from x port 16236 ssh2
May  3 00:09:15 philo sshd[11496]: Failed password for server from x port 16236 ssh2
May  3 00:23:48 philo sshd[11545]: Failed password for server from x8 port 16407 ssh2
May  3 00:23:48 philo sshd[11545]: Failed password for server from x8 port 16407 ssh2
May  3 00:24:46 philo sshd[11550]: Failed password for server from x8 port 16411 ssh2
May  3 00:24:47 philo sshd[11550]: Failed password for server from x8 port 16411 ssh2


```

---

### Post by jerome1232 on 2012-05-03
Try getting more output. You can adjust the number after -n to get more or less lines of output.
```

grep sshd /var/log/auth.log | tail -n 30
```

edit: if you really don't want your ip shown an easy way to accomplish that is

```
grep sshd /var/log/auth.log | tail -n 30 | sed 's:your.ip.here:x.x.x.x:'
```

---

### Post by wlraider70 on 2012-05-03
server@philo:~$ grep sshd /var/log/auth.log | tail -n 30
May  3 00:00:46 philo sshd[11407]: Failed password for server from x.x.x.x p                                                                                                    ort 16203 ssh2
May  3 00:00:47 philo sshd[11407]: Failed password for server from x.x.x.x p                                                                                                    ort 16203 ssh2
May  3 00:01:23 philo sshd[11411]: Failed password for server from x.x.x.x p                                                                                                    ort 16205 ssh2
May  3 00:01:24 philo sshd[11411]: Failed password for server from x.x.x.x p                                                                                                    ort 16205 ssh2
May  3 00:03:22 philo sshd[11418]: Accepted password for server from x.x.x.x                                                                                                     port 16211 ssh2
May  3 00:03:22 philo sshd[11418]: pam_unix(sshd:session): session opened for us                                                                                                    er server by (uid=0)
May  3 00:03:23 philo sshd[11443]: Received disconnect from x.x.x.x: 11: dis                                                                                                    connected by user
May  3 00:03:23 philo sshd[11418]: pam_unix(sshd:session): session closed for us                                                                                                    er server
May  3 00:04:15 philo sshd[11448]: Accepted password for server from x.x.x.x                                                                                                     port 16214 ssh2
May  3 00:04:15 philo sshd[11448]: pam_unix(sshd:session): session opened for us                                                                                                    er server by (uid=0)
May  3 00:04:16 philo sshd[11472]: Received disconnect from x.x.x.x: 11: dis                                                                                                    connected by user
May  3 00:04:16 philo sshd[11448]: pam_unix(sshd:session): session closed for us                                                                                                    er server
May  3 00:04:39 philo sshd[11476]: Failed password for server from x.x.x.x p                                                                                                    ort 16216 ssh2
May  3 00:04:39 philo sshd[11476]: Failed password for server from x.x.x.x p                                                                                                    ort 16216 ssh2
May  3 00:05:10 philo sshd[11479]: Failed password for server from x.x.x.x p                                                                                                    ort 16217 ssh2
May  3 00:05:10 philo sshd[11479]: Failed password for server from x.x.x.x p                                                                                                    ort 16217 ssh2
May  3 00:09:15 philo sshd[11496]: Failed password for server from x.x.x.x p                                                                                                    ort 16236 ssh2
May  3 00:09:15 philo sshd[11496]: Failed password for server from x.x.x.x p                                                                                                    ort 16236 ssh2
May  3 00:23:48 philo sshd[11545]: Failed password for server from x.x.x.x p                                                                                                    ort 16407 ssh2
May  3 00:23:48 philo sshd[11545]: Failed password for server from x.x.x.x p                                                                                                    ort 16407 ssh2
May  3 00:24:46 philo sshd[11550]: Failed password for server from x.x.x.x p                                                                                                    ort 16411 ssh2
May  3 00:24:47 philo sshd[11550]: Failed password for server from x.x.x.x p                                                                                                    ort 16411 ssh2
May  3 02:08:49 philo sshd[11150]: pam_unix(sshd:session): session closed for us                                                                                                    er server
May  3 07:19:03 philo sshd[13133]: Accepted password for server from x.x.x.x                                                                                                     port 16556 ssh2
May  3 07:19:03 philo sshd[13133]: pam_unix(sshd:session): session opened for us                                                                                                    er server by (uid=0)
May  3 09:34:58 philo sshd[13133]: pam_unix(sshd:session): session closed for us                                                                                                    er server
May  3 14:06:47 philo sshd[9856]: Received disconnect from 10.10.10.100: 11: dis                                                                                                    connected by user
May  3 14:06:47 philo sshd[9831]: pam_unix(sshd:session): session closed for use                                                                                                    r server
May  3 14:24:10 philo sshd[14522]: Accepted password for server from 10.10.10.10                                                                                                    0 port 50851 ssh2
May  3 14:24:10 philo sshd[14522]: pam_unix(sshd:session): session opened for us                                                                                                    er server by (uid=0)

---

### Post by wlraider70 on 2012-05-05
Bump

---

### Post by wlraider70 on 2012-05-06
this might be my fist ever double bump :oops:

---

### Post by Lars Noodén on 2012-05-07
Have you opened ~/.ssh/authorized_keys on the target computer and verified that it is the same as the public key from the source computer?

---

