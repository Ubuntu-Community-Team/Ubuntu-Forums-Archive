---
title: "SSH problems"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by dreadh3ad on 2008-07-08
I cannot ssh into an ubuntu 7.10 server I set up last night.  

I am using an ubuntu 7.10 desktop machine to ssh into a 7.10 server.  Here is the error message:

```
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is [key]
Please contact your system administrator.
Add correct host key in /home/baka/.ssh/known_hosts to get rid of this message.
Offending key in /home/baka/.ssh/known_hosts:3 RSA host key for [IP & Port] has changed and you have requested strict checking.
Host key verification failed.
```

I have installed Bastille on my 7.10 desktop.  I cannot tell if the problem comes from Bastille or the SSH configuration on my server.

---

### Post by eldragon on 2008-07-08
there was a vulnerability in ssh key generation, and you must have been forced to regenerate keys....

deleting ~/.ssh/known_hosts will fix you. unless you are being attacked with a man in the middle kind of attack. make sure you are in a trusted zone when you accept the new key

EDIT, 

just open the known_hosts file and delete the third line, so that you dont have to accept keys for all known hosts again

---

### Post by tamoneya on 2008-07-08
did you have an old ssh server on the machine and then reinstall.  If so that just means that your desktop machine has stored the old ssh key and it notices it changed and is letting you know.  This is to make sure no one is intercepting your ssh traffic.  If you know that this isnt happening the matter is easily resolved by editing /home/baka/.ssh/known_hosts and removing the third line.```
gedit /home/baka/.ssh/known_hosts
```

---

### Post by dreadh3ad on 2008-07-08
I think I used the same IP address and port for my previous configuration.  I am at work now but I will check it out when I get home.  Thanks!

---

### Post by dreadh3ad on 2008-07-08
What if i was subject to a man in the middle attack, what would I do?

---

### Post by tcpip4lyfe on 2008-07-08
> **dreadh3ad said:**
> What if i was subject to a man in the middle attack, what would I do?

Create an entry in iptables to block that specific mac. Or you could just pull the plug on the server. :)

---

### Post by tamoneya on 2008-07-08
if you are doing this across your local network at your house and you are just using internal IPs it really isnt possible unless the "man in the middle" was your brother or something.

---

### Post by sydbat on 2008-07-08
I imagine it is just a reinstall issue. I had the same thing happen when I changed from wubi to a full install. I found that deleting ~/.ssh/known_hosts (as eldragon suggests) worked best. It will simply write a new file for ssh access and you should be good to go.

---

### Post by dreadh3ad on 2008-07-09
> **tamoneya said:**
> did you have an old ssh server on the machine and then reinstall.  If so that just means that your desktop machine has stored the old ssh key and it notices it changed and is letting you know.  This is to make sure no one is intercepting your ssh traffic.  If you know that this isnt happening the matter is easily resolved by editing /home/baka/.ssh/known_hosts and removing the third line.```
gedit /home/baka/.ssh/known_hosts
```

How is it I can open that path yet it remains hidden when using 'ls'?

---

### Post by Sydius on 2008-07-09
> **dreadh3ad said:**
> How is it I can open that path yet it remains hidden when using 'ls'?

Files starting with a period are hidden... try "ls -a"

---

