---
title: "See who logs in remotely."
date: 2008-11-07
forum: New to Ubuntu
---

### Post by terranet-tb on 2008-11-07
Good day,

I'm pretty new within the Linux OS and I've stumbled upon some things that I couldn't quite figure out.

I've tried to use the search function and google them, but unfortunatly the key words resembled other functions in general computing.

So I've decided to try my luck here on the Ubuntu forums, as that's the distribution me and my team have chosen to work with for our school's project.

What was asked of us was to setup a file/internet server with two type of clients.

1. Instructor client, for the instructor to monitor who logs in at what location and time on the second client. 

2. Student client, for students with limited access. 

The idea is to monitor the student client from the instructor's client. 

The server and clients are all running Ubuntu's distribution with their respective editions.

What should suffice is a simple log; who logs in where at what time.

What would be ideal, is the above with the option to view the screen entirely (in a way like VNC). 

What would be the best course of actions to make this possible?


Thanks in advance.

---

### Post by jaytek13 on 2008-11-07
I'm not really sure I'm understanding the need for 2 machines here... I mean, if you set up an SSH server there will be a /var/log/secure log which all successful and failed logins would be logged. If the point is to have a seperate are for the students, you could set up jail shell access ([http://rhcelinuxguide.wordpress.com/2006/07/02/linux-jail/](http://rhcelinuxguide.wordpress.com/2006/07/02/linux-jail/)). But I still feel I'm not really understanding the assignment.

---

### Post by terranet-tb on 2008-11-07
Perhaps my choice of words were somewhat unclear.

The assignment is to have an instructor type of client (full access to the system) and a student type of client (one that is pretty locked down, with the exception of some applications).

That part has already been implemented. But the follow up is to be able to view the student clients on who logs in, and at what workstation they log in, around what time.

We're first testing one student client, but later on there will be around ten of them. 

It's really a small network setup with one "administrative" client monitoring the rest of the clients. But the only type of administrative function it needs is to see who logs in as mentioned above.

I hope I've made it a bit more clearer. Thanks for the suggestion though.

---

### Post by hictio on 2008-11-07
There are also the terminal commands: 'who'. 'last' & 'lastlog' which will show you information on logins (from where, who, when was the last time, etc)
Read the man on them on your system.
At the prompt, type, for instance:
```

man lastlog (ENTER)

```

---

### Post by achase79 on 2008-11-07
Is the network a netboot setup or is each computer set up separately?

---

### Post by achase79 on 2008-11-07
The file/internet server that you set up will have a log of who logged into it and when (file server would be best for this because it would require a username). Depending on what server you set up (Samba or NFS) would be where you would find the log.

---

### Post by terranet-tb on 2008-11-07
Thanks for the replies, I will check out each option with my team.

I'll let you know if all goes well.

---

