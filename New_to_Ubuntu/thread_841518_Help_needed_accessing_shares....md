---
title: "Help needed: accessing shares..."
date: 2008-06-26
forum: New to Ubuntu
---

### Post by PsycoGeek on 2008-06-26
I am working on converting my whole network over to Ubuntu (from Windows).  Every question that I have refers to sharing files between Ubuntu machines ,NOT aces sing Ubuntu shares from a Windows machine... Windows is going away.

Here is the situation in a nutshell... I have one machine that will do all of the sharing (U1).  It is a desktop build of Ubuntu 8.04, but will ace like a file server, since that is all I need (no printer sharing, it will not act as a DNS or DHCP server, or as a router... just file sharing).  I have client machines that will connect (U2, U3, etc...).  Here are my questions...

1. What is the easiest method of creating the shares?
2. How do I give the clients access (as users)? Permissions?
3. What method of connecting is best in this situation?
3. How do I make the client connections persistent (reconnect at log-in)?

---

### Post by sydbat on 2008-06-26
I found this helpful - [http://ubuntuforums.org/showthread.php?t=837387&highlight=ssh+sharing+ubuntu+computers](http://ubuntuforums.org/showthread.php?t=837387&highlight=ssh+sharing+ubuntu+computers) - it allows me to share the 2 boxes I have very easily. I think there are settings for other network needs through this.

---

### Post by DGortze380 on 2008-06-26
I'm not sure if there is a better way to do it, but what I do:

Obviously, set up your network appropriately with static IP, etc.

Install ssh on all machines 
```
 sudo apt-get install ssh 
```

Set-up all user accounts including groups and permissions on the SERVER (set up all other machines too, but user names and password on the server are need to connect)

Ubuntu allows you to set-up a network folder right on the desktop, or access via the command line. 

Click places, connect to server, enter username and password. Server folders will be accessible through the GUI. 

Or

ssh username@host -D portNumber     (accesses the server in a shell. man ssh for more info)
sftp username@host -D portNumber    (accesses the server for file transfer. man sftp for more info)


Thats just a quick rundown, any specific questions post or PM.

---

### Post by PsycoGeek on 2008-06-26
Thank you both, sydbat and DGortze380.  I will be putting some of this to the test ASAP.  I may not get to it until later tonight or tomorrow.

---

