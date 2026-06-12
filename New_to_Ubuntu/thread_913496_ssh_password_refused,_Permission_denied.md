---
title: "ssh password refused, Permission denied"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by sjaxso on 2008-09-07
Hi,

My SSH server accepts my password from localhost:
```

ssh localhost
```

But not remotely. I have tried within the internal network, external via dyndns, from the ubuntu box and from PuTTY on my XP laptop.

It always finds the SSH server, which responds, asking for a password. I provide the password, which it refuses:
```

debug1: Trying private key: /home/shane/.ssh/id_rsa
debug1: Trying private key: /home/shane/.ssh/id_dsa
debug1: Next authentication method: password
shane@********'s password: 
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
```

I've tried with different users, same result.

I should also say that my hosts.allow includes the lines
```
ALL: 10.1.1.*
ALL: ???.???.*.*
```
the question marks refer to the actual IP address block for my ISP, just a temporary thing...


I've also tried using public/private keys, which would be ideal - but being a newbie I'm struggling with that too. If anyone knows of a step by step tutorial for SSH with keys, I'd like to see it!

I sure would appreciate some help.

---

### Post by Xiong Chiamiov on 2008-09-07
I'd first try to get connected without any restrictions.  From there, you can then slowly lock it up.

That means, change hosts.allow to
```

sshd: ALL

```

As far as guides, [the Ubuntu docs]("https://help.ubuntu.com/community/SSHHowto") are pretty good, although I've found [the Arch ones]("http://wiki.archlinux.org/index.php/SSH") to be a little more helpful in some of the configuration options.  When you get to logging with in keys, take a look at [this]("http://www.ece.uci.edu/~chou/ssh-key.html").

EDIT: Also, make sure that you're using a username that exists on the remote machine.  To make sure, I'd specify the username specifically on the localhost test:
```

ssh user@localhost

```
then use the same thing (though obviously having a different host than localhost) for connecting remotely.

---

### Post by sjaxso on 2008-09-07
*deleted*

---

### Post by adult swim on 2008-09-07
shane is this machine on your local network?

---

### Post by sjaxso on 2008-09-07
> **adult swim said:**
> shane is this machine on your local network?

Yes it is. I've tried from outside the network with the same result.

---

### Post by adult swim on 2008-09-07
did you ever try to login to the remote before you generated rsa keys, using your password only?

---

### Post by sjaxso on 2008-09-07
> **adult swim said:**
> did you ever try to login to the remote before you generated rsa keys, using your password only?

Ah, no. I should delete all the keys and try again?

---

### Post by adult swim on 2008-09-07
that would probably be the best way to troubleshoot it.  you can apt-get purge openssh-client openssh-server and then check to see if the .ssh file is deleted in your home directory, if not delete it, then reisntall both.  do this for the host and the remote.  once you have it reinstalled, the default should be username@server and prompt for your server password.  if that doesnt work then we can build from there.

---

### Post by sjaxso on 2008-09-07
> **adult swim said:**
> that would probably be the best way to troubleshoot it.  you can apt-get purge openssh-client openssh-server and then check to see if the .ssh file is deleted in your home directory, if not delete it, then reisntall both.  do this for the host and the remote.  once you have it reinstalled, the default should be username@server and prompt for your server password.  if that doesnt work then we can build from there.

Hey, I really appreciate this, thanks.

I've purged the apps and deleted the .ssh directory - then installed the apps again.

ssh user@localhost works fine.

ssh user@10.1.1.6 works fine from my XP laptop - which is great.

It refuses my password when I try to ssh from outside though.

---

### Post by Xiong Chiamiov on 2008-09-07
Since you say that it refuses your password, rather than not being able to connect to it at all, I'm assuming it's not a firewall issue.

Does your /etc/allow.hosts look like this?
```

sshd: ALL

```

---

### Post by sjaxso on 2008-09-07
> **Xiong Chiamiov said:**
> Since you say that it refuses your password, rather than not being able to connect to it at all, I'm assuming it's not a firewall issue.

Does your /etc/allow.hosts look like this?
```

sshd: ALL

```

sure, well, it actually looks like this right now:

```
ALL: 10.1.1.*
ALL: 125.*.*.*
sshd: ALL
```

---

### Post by Xiong Chiamiov on 2008-09-07
Hmm, just to make sure, are you forwarding port 22 to the proper machine?  Some routers will actually allow you to ssh into them, so I guess you could be doing that on accident.

---

### Post by sjaxso on 2008-09-07
> **Xiong Chiamiov said:**
> Hmm, just to make sure, are you forwarding port 22 to the proper machine?  Some routers will actually allow you to ssh into them, so I guess you could be doing that on accident.

I do have port 22 forwarded to the server - however I am trying to go out through it and back in, which could be causing problems.

I also tried using a VPN connection to my office, and ssh-ing back from there, but same result. 

gah, I might just put my server into the DMZ and try that.

---

### Post by sjaxso on 2008-09-07
> **Xiong Chiamiov said:**
> Hmm, just to make sure, are you forwarding port 22 to the proper machine?  Some routers will actually allow you to ssh into them, so I guess you could be doing that on accident.

ok! It's definitely a router issue, putting the server into the DMZ fixes it. Really appreciate your help guys, much kudos to you.

---

### Post by Xiong Chiamiov on 2008-09-08
Glad if we could help at all.  And yes, changing login to only using keys is a good idea, as well as changing the port SSH runs on.  But always, start with the simple open-ended stuff, then gradually secure it.

---

### Post by adult swim on 2008-09-08
sjaxso i sent you a PM

---

