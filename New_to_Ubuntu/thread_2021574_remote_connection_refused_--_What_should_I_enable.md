---
title: "remote connection refused -- What should I enable?"
date: 2012-07-09
forum: New to Ubuntu
---

### Post by held7over on 2012-07-09
Ubuntu 12.04 openssh-client openssh-sever Firewall set to allow the remote access.

What do I need to enable or disable in my target computer, in order to ssh from my current computer across my network into a computer which has only been powered on? I get either a "no route to host" or:

$ ssh lucky@192.168.2.210
ssh: connect to host 192.168.2.210 port 22: Connection refused

However, if I connect a keyboard and screen to the target computer and directly login in first, THEN and only then, does the above ssh command allow me to login in from another computer on the network.

Thanks! :D

---

### Post by SeijiSensei on 2012-07-09
Is the SSH server configured to start up at boot?  What do you see if you run 

```
chkconfig ssh
```

If it's not set to "on", then follow the instructions I gave in [this post]("http://ubuntuforums.org/showpost.php?p=12088152&postcount=5"), but replace "off" with "on".

---

### Post by held7over on 2012-07-09
Here is the result:

lucky@ispy / $ sudo chkconfig ssh
ssh  on

---

### Post by held7over on 2012-07-09
I need to make a clarification--

Going from Ubuntu 12.04 to Linux Mint Debian Edition 12.04, meaning the LMDE machine is only powered on, I got:

$ ssh lucky@192.168.2.210
ssh: connect to host 192.168.2.210 port 22: Connection refused

And the above was what I was trying to do, and the LMDE machine is the one that I performed your check on which gave:

lucky@ispy / $ sudo chkconfig ssh
ssh on

However, reversing the situation so that the LMDE machine is the origin trying to contact the Ubuntu machine, it works great. So, my problem is actually on the Debian edition of Linux Mint. I had forgotten I had put LMDE on this machine to increase it's speed. Does this make a difference?

---

### Post by held7over on 2012-07-09
I'm going to install Ubuntu 12.04 on that machine and see if that doesn't fix the problem.

---

