---
title: "ssh - identity file not recognized/used; ssh-add: &quot;could not open a connection ...&quot;"
date: 2013-05-06
forum: New to Ubuntu
---

### Post by simlei on 2013-05-06
Hi,
I just installed my first Ubuntu; it runs in a VirtualBox environment. I installed it for a specific purpose: to use SSH. Beyond that, it was about time I got myself a linux environment, for finally expanding my Windows horizon.

My current problem lies with the authentication to the remote server. I want to authenticate myself using an id_rsa identity file I still have from my windows machine and which is in use there already to authenticate with github. The remote SSH server knows my public part to the id_rsa.
I created a .ssh folder in my home directory (~/.ssh, right?), and copied the id_rsa key to this location.

the first try with
ssh <remote adress> failed; It apparently didn't see or try the id_rsa file, because it asked for the password for the remote server (not for the password of the private key):

```

sudo ssh uni04@x.x.xxx.x
uni04@x.x.xxx.x's password:

```

I asked a friend, which hinted me to ssh-add, and I did explore that:
 - ssh-add gave me trouble for my lax standard-permissions on .ssh, which I appreciate ;D I was told to chmod the .ssh folder to 600; I did that.
 - ssh-add ~/.ssh/id_rsa now tells me "Could not open a connection to your authentication agent." - Again, on the request of the mentioned friend, I executed the following lines followed by the output:

```

simon@simonUbuntu:~$ eval $(ssh-agent)
Agent pid 2566
simon@simonUbuntu:~$ ps aux | grep ssh-agent
simon     1670  0.0  0.0  12612   320 ?        Ss   12:45   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/im-launch gnome-session --session=ubuntu
simon     2446  0.0  0.0  12612   320 ?        Ss   13:13   0:00 ssh-agent
simon     2556  0.0  0.0  12612   320 ?        Ss   13:33   0:00 ssh-agent
simon     2566  0.0  0.0  12612   320 ?        Ss   13:39   0:00 ssh-agent
simon     2568  0.0  0.0  15104   992 pts/2    S+   13:39   0:00 grep --color=auto ssh-agent
simon@simonUbuntu:~$ sudo ssh-add ~/.ssh/id_rsa
Could not open a connection to your authentication agent.

```

Trying to connect with ssh does not work, If I want to authenticate with the id_rsa:

```

simon@simonUbuntu:~$ sudo ssh uni04@x.x.xxx.x
uni04@x.x.xxx.x's password: 
simon@simonUbuntu:~$ sudo ssh -i ~/.ssh/id_rsa uni04@x.x.xxx.x
uni04@x.x.xxx.x's password: 

```

I really don't know about agents and how SSH operates with the usage of the identity files. But shouldn't it use the id_rsa by standard? 
And even more confusing to me: Why don't I get a meaningful response when I explicitely declare the private key I want to use (sudo ssh -i ~/.ssh/id_rsa) - when it isn't used then apparently?

I would REALLY appreciate your help! I'm not a slow learner and did what I could until here, but I feel the need for advice from someone who knows this behaviour already.
I will respond very quickly if you've got any questions to my setup or environment or whatever ^^ 

Thanks a lot already for reading ;) Greetings.

---

### Post by Lars Noodén on 2013-05-06
The server has to have your public key.  Specifically it has to go into the file ~/.ssh/authorized_keys if you are using the default settings.  The key must be whole and unbroken on one single line in that file.  Some people use [ssh-copy-id](http://manpages.ubuntu.com/manpages/raring/en/man1/ssh-copy-id.1.html) to move the key to the server, but I usually just open an editor and paste it in.  If you use *nano* for your editor, launch it with *-w* to keep the lines from wrapping.  Once the key is in place, you should be able to log in using it.  

```

ssh -i ~/.ssh/id_rsa uni04@x.x.xxx.x

```

ssh-add will work if you have the agent running (which Ubuntu does by default) and if the above key authentication works.  No need to run the agent a second time if Ubuntu has already done it for you.

You don't need sudo for any of this.  Hopefully you didn't create any files in you home directory as root.  If you did, you'll need to find them and change the permissions or delete them.

---

### Post by simlei on 2013-05-06
Hi,
I don't have control over the remote server; an admin installed my key. I'm positive that this was done correctly.
Also, I think the problem is local, Since I never even got to enter the passkey to my private key file (which tells me it was not really considered for authentification, right?)
Furthermore, I don't think the issue lies with the keys themselves; I use them everyday on my windows machine to authenticate with github, and I just copied them over to the ubuntu ssh directory.

I mean: there is this thing with the
```

simon@simonUbuntu:~$ sudo ssh-add ~/.ssh/id_rsa
Could not open a connection to your authentication agent.

```

-- that seems to be the issue to me.

I can't really deny the possibility, that the key has some "Windows illness" since it was created there. Maybe windows linebreaks are the issue? I don't know. The key is in the following form:

```

-----BEGIN RSA PRIVATE KEY-----
Proc-Type: 4,ENCRYPTED
DEK-Info: DES-EDE3-CBC,E7C4F41E739FFBBD


yPY14y4[........]TW6vxK
91KEHlk[........]zyFzTSt8Bq
Voi[........]UDPA2EBW9F
hFJ[........]IgJT9q3ddV
ncr3[........]qrA5oLlG
uhK[........]Q/toGOK
Kwri[........]DHBr4m
Gn[........]Z4ENvx
8Dw5[........]zDSPWQl37
g1Y[........]1c1d
Fd7G[........]aGaf
zQOr[........]HIHun/
xSYE[........]ROs=
-----END RSA PRIVATE KEY-----

```

That looks like a pretty stable format to me (no special characters and all, rectangular form , ... and should ssh really not be able to parse that?
But, shouldn't we consider the agent connectivity thing to be the issue first?

Best,
Simon

---

### Post by Lars Noodén on 2013-05-06
First, sudo is not needed here.  It can cause trouble if you use it and it is the cause of your not being able to connect to the agent.  So don't run sudo to run ssh.  If there is something specific you are trying to do then we can address that after we get the key working.  Try running ssh-add as yourself, not root.  Running it as root fails because it does not know where to look for the agent.

Second, if you have the ability to log into the remote machine with a password, then you have enough access to set up key-based authentication.  Can you do that?

---

### Post by Lars Noodén on 2013-05-06
About sudo, these two lines are equivalent:

```

sudo ssh-add ~/.ssh/id_rsa
sudo ssh-add /root/.ssh/id_rsa

```

They are not what you want.  It won't find the agent because the variable SSH_AUTH_SOCK is not set, even if you made special key for root, but it is set for your own account.  It was set when you logged in.  If your private key is called id_rsa and is found in ~/.ssh, then this is what you want:

```

ssh-add ~/.ssh/id_rsa

```

---

### Post by simlei on 2013-05-06
Hi,

First, I should emphasize agaion, that I have got no password or the like for the user 'uni04' on the remote machine. I was told, I should just send in my public key part, which (I hope ^^) was installed then (But I'm realtively sure that it was done.)

I followed your advice to not sudo. I actually added the id_rsa now successfully to my identities =)
I suspect, though, that this working now had something to do with me installing the openssh-server package (I needed this for trying something out with ssh-copy-id, but I wanted a ssh server running on this amchian later, anyways).

Anyways, when I try to ssh into the remote server now, it gets me this:
```

simon@simonUbuntu:~/.ssh$ ssh uni04@xx.xx.xx.xx
Enter passphrase for key '/home/simon/.ssh/id_rsa': 
uni04@xx.xx.xx.xx's password: 

```

Now, that is confusing, too, and I'm starting to suspect, that (because private-key-authentication alone doesn't seem to be enough and the password for the user si still required), that this could be a remote problem. Of course, the first problem of all is, that I can't interpret what this behaviour says about what the server _expects_ and what his policy is.
Some hints still appreciated =) Even if the key was now installed successfully =))

But, big thanks already =)

---

### Post by Lars Noodén on 2013-05-06
It should have asked for your passphrase when you loaded the key into the agent, and then not needed it further to connect to the remote server.  Then, if the key worked, it should not ask for the password.

Have you looked at the debugging output?  You can have ssh provided more verbose information about the connection:

```

ssh -v uni04@xx.xx.xx.xx

```

That can also be increased further with -vv and -vvv

---

### Post by simlei on 2013-05-06
The -v output reads:

```

simon@simonUbuntu:~/.ssh$ ssh -i id_rsa uni04@x.x.x.x -v
OpenSSH_6.1p1 Debian-4, OpenSSL 1.0.1c 10 May 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to x.x.x.x [x.x.x.x] port 22.
debug1: Connection established.
debug1: identity file id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-1024
debug1: identity file id_rsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.9p1 Debian-5ubuntu1
debug1: match: OpenSSH_5.9p1 Debian-5ubuntu1 pat OpenSSH_5*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.1p1 Debian-4
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: RSA 62:2d:d2:09:dd:7a:6b:84:f5:80:91:a7:06:a6:b6:a4
debug1: Host 'x.x.x.x' is known and matches the RSA host key.
debug1: Found key in /home/simon/.ssh/known_hosts:2
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering RSA public key: id_rsa
debug1: Authentications that can continue: publickey,password
debug1: Offering RSA public key: Simon L@lgbook
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: password
uni04@x.x.x.x's password: 

```

---

### Post by Lars Noodén on 2013-05-06
I'm not sure how much can be gleaned from the client.  Nothing stands out.  The client won't say but the probable culprit may be incorrect permissions on the .ssh directory on the remote system.  If you don't have access, then you'll have to get the sysadmin to double check it.  

*.ssh* should be 700 and *authorized_keys* can be 600 or 640 or 644

Edit: also double check that the directory and the file are owned by your account and didn't accidentally get set as root or something like that.

---

### Post by simlei on 2013-05-06
Hi,
I checked my permissions (were okay).

I finally wrote an email to the sysadmin, since I really can't imagine my side to be the culprit here. To be sure, I sent him a mint ssh public key to try one that was generated from the environment I use (As I said the other keypair was known for a bit of trouble).

Now all I can do is wait, and thank you for your valuable advice =)

Simon Leischnig

---

### Post by simlei on 2013-05-07
The problem was the remote server indeed >_> This topic may be closed. But thank you, I learned something about ssh along the way =)

---

