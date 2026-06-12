---
title: "[SOLVED] VNC after reboot"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by sakid on 2008-06-15
Hi all,

Here is my problem: I am currently have a VPN connection to work so I can use my work computer with VNC. After putting on updates I was required to reboot.  After rebooting I can't VNC because I haven't logged in yet.  I do have ssh access.

Is there a way of being able to VNC again without having to physically go to the machine(about 100km away)

Thanks in advance

---

### Post by wormser on 2008-06-15
You could try a VNC ssh tunnel.  If I am understanding you right.  VNC will not log in because no user has logged in.  Try the following.

```
ssh -L 5900:localhost:5900 username@domain.com
```

Now, in your VNC client use localhost as the domain and 5900 as the port.  The 5900 needs to be the same port number you VNC into the remote machine.  

BTW, you should tunnel your VNC connections anyway.

---

### Post by sakid on 2008-06-15
Didn't work - although I'm not sure if I understand what you mean and how to do it..

---

### Post by wormser on 2008-06-15
What part did you not understand, the VNC part?  It looks like you just need to start the VNC server on the remote machine.  You can do this with ssh.  I am just unsure what the command is.

---

### Post by sakid on 2008-06-15
I got it working using this tutorial.
[http://ubuntuforums.org/showthread.php?t=795036](http://ubuntuforums.org/showthread.php?t=795036)

Thanks for your help - you put me on the right track.

Cheers

---

