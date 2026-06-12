---
title: "Access school compy files from home"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by LusciousChunks on 2008-04-29
So I have a computer with Ubuntu on it at school.  This school has a pretty sweet network for filesharing.  Now I have all these files on my school computer.  Is there a way to access these files outside the school network, say from a home computer.  I don't know if sshfs is what I want, and if it is, well there isn't a newbieish enough tutorial for me that I can find.

---

### Post by martrn on 2008-04-29
> **LusciousChunks said:**
> So I have a computer with Ubuntu on it at school.  This school has a pretty sweet network for filesharing.  Now I have all these files on my school computer.  Is there a way to access these files outside the school network, say from a home computer.  I don't know if sshfs is what I want, and if it is, well there isn't a newbieish enough tutorial for me that I can find.

Secure Shell or SSH is a network protocol that allows data to be exchanged using a secure channel between two computers.

I am presuming that your school network has SSH installed on it as you talk about being pretty sweet for networking and filesharing.  You would need a password to connect to that computer.

If you wish to connect to ssh on your school computer and have ubuntu installed on your home computer here is the ssh [https://help.ubuntu.com/community/SSHHowto]("https://help.ubuntu.com/community/SSHHowto") howto.

If you are on a windows comupter you would need a windows ssh client, and ask for a tutorial on the forums for you client.

---

### Post by shad0w_walker on 2008-04-29
I would suggest you talk to the IT people at the school about this. I doubt they would take kindly to people suddenly connecting into their systems from outside their own network.

---

### Post by quirks on 2008-04-29
If your school has done a good job securing its network, there should not be any (straighforward) way to access the network from outside except for a VPN access, maybe. A firewall should block any connections from outside and stations inside the network also should not be allowed to connect to the Internet directly. However, it is doubtful, if there is a VPN access at all. And even if it has one, it is unlikely that the administrator gives the credentials to you.

---

### Post by PeterJS on 2008-04-29
> **shad0w_walker said:**
> I would suggest you talk to the IT people at the school about this. I doubt they would take kindly to people suddenly connecting into their systems from outside their own network.

If it's a university network that's publicly accessible, I wouldn't bother asking, machines on public networks running sshd are expected to have people connect to them, they wouldn't (shouldn't) have put sshd on them if that wasn't the expectation. Furthermore they shouldn't grant a user permission to login to a machine they don't want them logging in to.

As for using sshfs, it's probably the easiest way there is to access remote files on a machine running sshd. Sshfs is dead easy to use once you have it setup:
```

sshfs user@host:/remote/path /local/path/

```
and if you omit the remote path an just use:
```

sshfs user@host: /local/path/

```
sshfs will assume that you want the remote path to be your home directory on the remote machine.
and to unmount it:
```

fusermount -u /local/path/

```

---

### Post by shad0w_walker on 2008-04-29
> **PeterJS said:**
> If it's a university network that's publicly accessible, I wouldn't bother asking, machines on public networks running sshd are expected to have people connect to them, they wouldn't (shouldn't) have put sshd on them if that wasn't the expectation. Furthermore they shouldn't grant a user permission to login to a machine they don't want them logging in to.


That's true enough however I don't recall seeing anything actually saying that SSH was setup on the computer at all, it was just mentioned as 'maybe this is what I want' so it is still quite possible that it isn't setup. Also asking the staff will let you find out if there is a preferred method of accessing the network from outside or if there is a set of rules to follow, etc.

---

