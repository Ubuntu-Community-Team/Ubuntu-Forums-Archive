---
title: "[SOLVED] ssh or scp without password?"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by garyed on 2008-10-05
I've been trying to do this for two days following instructions on both these websites [http://www.linuxjournal.com/article/8600](http://www.linuxjournal.com/article/8600)  and [http://www.hostingrails.com/forums/wiki_thread/27](http://www.hostingrails.com/forums/wiki_thread/27)  and I still have to use a password every time I log in or scp from one computer to the other. I've entered the command 
```
 ssh-keygen -t rsa 
``` & then copied the id_rsa.pub to the remote computer as ~/.ssh/authorized_keys I also tried the file as ~/authorized_keys on the remote computer but it still doesn't work. Any one have any ideas what I might be missing?

---

### Post by bobnutfield on 2008-10-05
I have been successful doing this with:

> ssh-keygen -t dsa

Then, just pressing enter when it asks for a passphrase, meaning none.  Then, send the public key to the desired location with:

> ssh-copy-id -i ~/.ssh/id_dsa.pub user@192.168.X.X

I can then ssh to the other machine without a password.  I am not an expert, but this works for me, and I cannot tell you what the difference between dsa and rsa is.

---

### Post by jamesrl on 2008-10-05
It also depends how the sshd is configured on the other end.  Specifically, the authentication settings in /etc/ssh/sshd_config
You can read up on the various setting in man sshd_config  though I think the relevant ones for you are AuthorizedKeysFile and RSAAuthentication.

Some sysadmin's do not allow passwordless authentication, as problems can arise (if someone gets access to your private key than they can access any machine you can access).  See my post here: [http://ubuntuforums.org/showthread.php?t=904796]("http://ubuntuforums.org/showthread.php?t=904796")

---

### Post by garyed on 2008-10-05
The only thing I haven't tried is to use the ip address instead of the computer name. The authorized_keys is copied in the ~/.ssh folder though.
I've edited the sshd_config file on the remote too for those two lines also.
I'm at a loss. When you log in using ssh remotecomputer does it matter if I add my user name too? I've done it both ways & it still prompts for a password.

---

### Post by Dr Small on 2008-10-05
Greetings,
Have you tried this?
[http://php.8ez.com/drsmall/blog/?p=218](http://php.8ez.com/drsmall/blog/?p=218)

Dr Small

---

### Post by marshal_mellow on 2008-10-05
> **garyed said:**
> The only thing I haven't tried is to use the ip address instead of the computer name. The authorized_keys is copied in the ~/.ssh folder though.
I've edited the sshd_config file on the remote too for those two lines also.
I'm at a loss. When you log in using ssh remotecomputer does it matter if I add my user name too? I've done it both ways & it still prompts for a password.

unless you have the same username on both computers you need to do specify a username for example
```
ssh user@remotecomputer
```

---

### Post by garyed on 2008-10-05
> **Dr Small said:**
> Greetings,
Have you tried this?
[http://php.8ez.com/drsmall/blog/?p=218](http://php.8ez.com/drsmall/blog/?p=218)

Dr Small

Yes but to no avail.
When I issue the command
```
ssh-copy-id -i ~/.ssh/id_dsa.pub user@remotehost
```
I always get the number " 26 " returned before I get prompted for my password

---

### Post by garyed on 2008-10-05
What wouldd be the best way to clean everything up & start from scratch.
I've run the ssh-keygen command 20 times or more. In the /etc/ssh folder I've got a bunch of files. I don't know if they're all supposed to be there.

---

### Post by jamesrl on 2008-10-05
To restart,

first on your local computer (that you want to run ssh from and connect to sshd on the remote computer)
 ```

mv ~/.ssh ~/.ssh_old
mkdir ~/.ssh
cp ~/.ssh_old/known_hosts ~/.ssh/known_hosts
```

and you will be reset to follow a guide again. You also can edit the .ssh/authorized_keys file on the remote computer to remove public keys that you no longer use.

---

### Post by bodhi.zazen on 2008-10-05
To start over:

```
rm -rf ~/.ssh
mkdir ~/.ssh
```

Really, do you need a key with no password ?


Why not just use a key with a password and then load it with ssh-agent

---

### Post by djhedges on 2008-10-05
#On the computer that is making the inital connection (Call this Computer A)
```
ssh-keygen -t rsa
ssh user@computer_b "cat >> .ssh/authorized_keys" < .ssh/id_rsa.pub
```

#On Computer B (authorized_keys needs to have 600 permissions or it won't work)
```
chmod 600 .ssh/authorized_keys
```

---

### Post by garyed on 2008-10-05
I finally got it.
Thanks to all for the help.
The problem I think was the laptop I was using didn't have all the ssh files on it. I had been accessing the remote-comp from my laptop for a while using ssh to log on & scp swapping files so I assumed I had ssh loaded properly on the laptop. When I realized I couldn't access my laptop from the other computer the bell started ringing. I did:
```
 apt-get install openssh-client openssh-server 
``` then reran the ssh-keygen command & copied it over everything worked perfectly.
Thanks again

---

