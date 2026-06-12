---
title: "get &quot;Permission denied (publickey,password)&quot; message when trying to login as root"
date: 2014-10-18
forum: New to Ubuntu
---

### Post by lily5 on 2014-10-18
Hi All,
I am new to Ubuntu and met a problem today. 
I'm recently trying to upload my website to a remote server(It's from digital ocean). I accidentally executed
ssh-keygen -t rsaon server, then I find I can not login into my server anymore:
here is what I tried:
#-----------------------------------------
root@104.131.27.144's password: 
Permission denied, please try again.
root@104.131.27.144's password: 
Permission denied, please try again.
root@104.131.27.144's password: 
Permission denied (publickey,password).
#------------------------------------------
But I can login when try "ssh 104.131.27.144", and I tried to modify /etc/ssh/sshd_config[COLOR=#000000][FONT=Times] ,but turns out it is read only file. I am guessing I should login root@ and modify that.[/FONT][/COLOR]

And the ssh debug page is shown as below:
#-------------------------------------------------------

lilys-MacBook-Air-2:~ lily$ ssh root@104.131.27.144
root@104.131.27.144's password: 
Permission denied, please try again.
root@104.131.27.144's password: 
Permission denied, please try again.
root@104.131.27.144's password: 
Permission denied (publickey,password).
lilys-MacBook-Air-2:~ lily$ ssh -v root@104.131.27.144
OpenSSH_6.2p2, OSSLShim 0.9.8r 8 Dec 2011
debug1: Reading configuration data /etc/ssh_config
debug1: /etc/ssh_config line 20: Applying options for *
debug1: /etc/ssh_config line 102: Applying options for *
debug1: Connecting to 104.131.27.144 [104.131.27.144] port 22.
debug1: Connection established.
debug1: identity file /Users/lily/.ssh/id_rsa type 1
debug1: identity file /Users/lily/.ssh/id_rsa-cert type -1
debug1: identity file /Users/lily/.ssh/id_dsa type -1
debug1: identity file /Users/lily/.ssh/id_dsa-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.2
debug1: Remote protocol version 2.0, remote software version OpenSSH_6.6.1p1 Ubuntu-2ubuntu2
debug1: match: OpenSSH_6.6.1p1 Ubuntu-2ubuntu2 pat OpenSSH*
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr [email]hmac-md5-etm@openssh.com[/email] none
debug1: kex: client->server aes128-ctr [email]hmac-md5-etm@openssh.com[/email] none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Server host key: RSA a2:99:bd:64:35:98:ec:fd:c2:fe:90:e9:30:3c:9f:28
debug1: Host '104.131.27.144' is known and matches the RSA host key.
debug1: Found key in /Users/lily/.ssh/known_hosts:3
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /Users/lily/.ssh/id_rsa
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /Users/lily/.ssh/id_dsa
debug1: Next authentication method: password
root@104.131.27.144's password: 
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
root@104.131.27.144's password: 
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
root@104.131.27.144's password: 
debug1: Authentications that can continue: publickey,password
debug1: No more authentication methods to try.
Permission denied (publickey,password).
#-------------------------------------------------------------------------

I have no idea what I should do, I spent half of a day dealing with it but it does not work.  
Thanks so much!!

---

### Post by nerdtron on 2014-10-18
[quote]But I can login when try "ssh 104.131.27.144", and I tried to modify /etc/ssh/sshd_config[COLOR=#000000][FONT=Times] ,but turns out it is read only file. I am guessing I should login root@ and modify that. [/[/FONT][/COLOR]quote]

You were able to login to the server as a normal user? Did you try to sudo afterwards?
```
 sudo su - 
```

If the above fails you to get to root, you need to copy the new keys from the server since you regenerated them.
[https://www.digitalocean.com/community/tutorials/how-to-use-ssh-keys-with-digitalocean-droplets](https://www.digitalocean.com/community/tutorials/how-to-use-ssh-keys-with-digitalocean-droplets)

---

