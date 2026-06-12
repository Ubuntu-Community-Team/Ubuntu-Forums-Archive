---
title: "How do I find out the host name, or IP adress, of an internally networked Server"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by Under_there on 2008-04-22
Hello!  I am trying to install PuTTY to a vista comp., so as to access an Ubuntu Server which currently holds all the office files.

Unfortunately, everyone in the office is scared of this machine, and has no idea what the Host Name might be.  

Any help as to where I can find this information would be greatly appreciated. Also, are the usernames and passwords that we used to access the files accross Samba going to be the same on the main machine?

The machine came installed with Samba, and was just plugged into the Telus router.  That is all I know, so far.  

Cheers wise people.

---

### Post by Golem XIV on 2008-04-22
If you can log into the server, type ifconfig and it will tell you.

If you can't log into the server, try the netstat command from a terminal on your system (or use System -> Administration -> Network Tools, Netstat tab) to show what servers your system is connected to.  From there you may be able through elimination to find out which one is the server.

---

### Post by mlentink on 2008-04-22
If it holds all office files, is it already connected to the network? If so, what is its name on the network? You could try to ping it with that name.
Are you afraid to simply log on to that machine? I mean directly, not through ssh.

Oops, too late

---

### Post by rax_m on 2008-04-22
If you can log in to the ubuntu server you can type the following to get the ip address associated with each of the network interfaces. 

```
ifconfig


```


and the following to get the hostname:
```
hostname
```
;)

I think how you access the share is going to depend on how the share was set up and who has permissions to it. If it's an open share then you should be able to get to it from  anywhere. If not you might need logon credentials either of the main server or the user that was granted the permissions to the directory.

---

### Post by arguellodw on 2008-04-22
If you have access to a machine already on the network, you can use the command
$ nslookup <IP address>
and the domain name will be returned.  As well, if you issue
$ nslookup <domain name>
the IP address will be returned.

Hope this helps. =)

---

### Post by Under_there on 2008-04-22
Not afraid, just lazy.  It's headless and I can't be bothered to drag my monitor and keyboard over there.  Thank you, though!  Seem to have solved problem 1.

---

### Post by Under_there on 2008-04-22
Thanks.  Pinging it was the easiest way.

---

