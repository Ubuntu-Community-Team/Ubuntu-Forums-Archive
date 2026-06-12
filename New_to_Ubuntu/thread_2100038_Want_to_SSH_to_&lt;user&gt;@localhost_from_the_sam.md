---
title: "Want to SSH to &lt;user&gt;@localhost from the same machine"
date: 2012-12-31
forum: New to Ubuntu
---

### Post by oldtiredandconfused on 2012-12-31
I have read the documentation from
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

and I believe I have done all that was suggested. 
I was able to login with a password. Then edited sshd_config(yes saved original first) and changed the line
#PasswordAuthentication yes
to 
PasswordAuthentication no  as I understood documentation to say.

Then restarted ssh
sudo restart ssh
and when I login as awheeler@localhost I get 
Permission denied (publickey).

then I try 
ssh -v awheeler@localhost

and the output is:

OpenSSH_6.0p1 Debian-3ubuntu1, OpenSSL 1.0.1c 10 May 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: Connection established.
debug1: identity file /home/awheeler/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/awheeler/.ssh/id_rsa-cert type -1
debug1: identity file /home/awheeler/.ssh/id_dsa type -1
debug1: identity file /home/awheeler/.ssh/id_dsa-cert type -1
debug1: identity file /home/awheeler/.ssh/id_ecdsa type -1
debug1: identity file /home/awheeler/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_6.0p1 Debian-3ubuntu1
debug1: match: OpenSSH_6.0p1 Debian-3ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.0p1 Debian-3ubuntu1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA 00:7c:54:cd:3e:34:3e:1c:f9:40:17:6b:58:25:87:71
debug1: Host 'localhost' is known and matches the ECDSA host key.
debug1: Found key in /home/awheeler/.ssh/known_hosts:28
debug1: ssh_ecdsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/awheeler/.ssh/id_rsa
debug1: Authentications that can continue: publickey
debug1: Offering RSA public key: awheeler@ubuntu
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/awheeler/.ssh/id_dsa
debug1: Trying private key: /home/awheeler/.ssh/id_ecdsa
debug1: No more authentication methods to try.
Permission denied (publickey).


I have been struggling off and on for days.

---

### Post by sudodus on 2012-12-31
> **oldtiredandconfused said:**
> Permission denied (publickey).

Welcome to the Ubuntu Forums :-)

I guess you connect to localhost to test that it works. You can also try connecting to the IP address of your computer (instead of localhost).

Run ifconfig: look for eth0, eth1 ... or wlan0, wlan1 ... and inet addr: and the IP address would be 192.168.0.2 or something similar.

I see in your output list that permission is denied, and that you use public key authentication. It can be a little tricky, but if you follow the instructions it works. Repeat if necessary.

If it is at home (a home LAN) I think you can use password authentication, which is not as secure, but it usually works out of the box.

---

### Post by The Cog on 2012-12-31
Did you copy .ssh/id_rsa.pub to .ssh/authorized_keys? 
This is needed to allow you to use your own key to log in as yourself.
Just a guess.

P.S.
The command would be:
```
cat .ssh/id_rsa.pub >> .ssh/authorized_keys
```

---

### Post by Kujua on 2012-12-31
Looks like you have only disabled password authentication. You also have to setup authentication keys. Use ssh-keygen.

---

### Post by Cheesemill on 2012-12-31
> **arifsajjadk said:**
> Looks like you have only disabled password authentication. You also have to setup authentication keys. Use ssh-keygen.
+1

Disabling password authentication doesn't mean that you can just log in, it means that you have to use a different method to authenticate instead, usually using SSH keys.

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

