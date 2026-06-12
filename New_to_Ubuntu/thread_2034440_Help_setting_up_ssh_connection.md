---
title: "Help setting up ssh connection"
date: 2012-07-28
forum: New to Ubuntu
---

### Post by nkizz on 2012-07-28
Hi, 
I Have ubento server and i need to set a ssh connection between my server and my mac.
Please Help!:)

---

### Post by Cheesemill on 2012-07-28
On the server do:
```
sudo apt-get install openssh-server
```

Then open a terminal on your Mac and connect by typing:
```
ssh <user>@<IP address>
```
(replacing <user> and <IP address> with the correct values for your server).

---

### Post by nkizz on 2012-07-28
Well I did that and terminal printed
> @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
a8:68:67:9e:8f:95:db:68:fa:50:ba:c3:40:f8:86:88.
Please contact your system administrator.
Add correct host key in /Users/Greenman/.ssh/known_hosts to get rid of this message.
Offending key in /Users/Greenman/.ssh/known_hosts:1
RSA host key for 192.168.1.3 has changed and you have requested strict checking.
Host key verification failed.


---

### Post by Cheesemill on 2012-07-28
This simply means that you have already used ssh to connect to a different machine that used to have the same IP address.

If you are sure that you are trying to connect to the correct machine then you need to edit the file /Users/Greenman/.ssh/known_hosts and delete the first line, you will then be able to connect without the error (you will be prompted to accept the RSA key for your server first).

---

### Post by MrMstr on 2012-07-28
This usually happens when you have re-installed the host and the identification has changed.

A quick solution will be to delete identification file on the mac in your home directory. However you will have to re-acknowledge all previous ssh hosts (it is not a problem).

to remove ssh identification file issue this command on your mac in your home directory:

```
rm .ssh
```

Hope this helps.

---

### Post by MrMstr on 2012-07-28
apologies. meant 
rm .ssh/known_hosts

Hope that helps.

---

### Post by nkizz on 2012-07-29
It worked!!!!
Thanks so much!!:D:D:D:D:D

---

### Post by Lars Noodén on 2012-07-29
> **MrMstr said:**
> apologies. meant 
rm .ssh/known_hosts

Hope that helps.

That's a bit of overkill and nukes all your known hosts.  If you want to remove just a single host key you can use [ssh-keygen](http://manpages.ubuntu.com/manpages/precise/en/man1/ssh-keygen.1.html)

```

ssh-keygen -R *192.168.1.3*

```

That will remove the key for only 192.168.1.3.

---

