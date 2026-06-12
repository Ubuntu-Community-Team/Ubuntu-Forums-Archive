---
title: "Need help loggin through SSH on my terminal"
date: 2013-08-05
forum: New to Ubuntu
---

### Post by eldan2 on 2013-08-05
Hey,
 
 I have installed ubuntu on a virtual machine and have securely ssh'd into my my server through the terminal on my mac os 10. I had to restart my computer and when i booted up ubuntu again, i tried doing an ssh again but this time it didn't work. It keeps on giving me an error saying "Bad escape character." for my username. 

Attached is a screenshot. How can i fix this issue and what does it mean? 

[ATTACH=CONFIG]245112[/ATTACH]

---

### Post by papibe on 2013-08-05
Hi eldan2.

If your want to connect using the user 'eldan88' to the machine 'sandbox.dev' using port 2222, then this should work:
```
ssh -p2222 eldan88@sandbox.dev
```
Let us know if that works.
Regards.

---

### Post by TheFu on 2013-08-05
It looks like the ssh command is a little off - 

**$ ssh -p 2222 [email]user@server.dev[/email] **
assuming you have the ssh server listening on port 2222.  I have no idea what the -edl.... stuff means. Is that an OSX option?

---

### Post by eldan2 on 2013-08-05
> **papibe said:**
> Hi eldan2.

If your want to connect using the user 'eldan88' to the machine 'sandbox.dev' using port 2222, then this should work:
```
ssh -p2222 eldan88@sandbox.dev
```
Let us know if that works.
Regards.

Hey! Thank you very much!!!! That Worked =)

---

### Post by papibe on 2013-08-05
Glad you worked it out :D

Please mark the thread as solved when you have the chance ([here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")'s how).

Regards.

---

### Post by TheFu on 2013-08-06
Also, you might want to review the ~/.ssh/config file. It lets you create ssh entries for different hosts that are automatically applied by ssh and ssh-using tools (rsync for example).  It is fantastic for switching ports, switching userIDs and when the remote hostname is long and difficult to remember (like an EC2 name).  [http://linux.die.net/man/5/ssh_config](http://linux.die.net/man/5/ssh_config) explains. For example:
```
host spider
  user john_doe43242
  hostname ec2-54-241-76-53.us-west-1.compute.amazonaws.com
  port 5222
```

Just add stanzas like this for every ssh connection.  Then your command looks like **ssh spider** - nothing more. The user, port, and long-ass hostname are replaced automatically. If you have ssh-keys, then it is even better.

---

