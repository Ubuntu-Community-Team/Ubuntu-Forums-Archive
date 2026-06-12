---
title: "Cannot connect with Android to my Linux machine"
date: 2013-10-30
forum: New to Ubuntu
---

### Post by LinuxUser666 on 2013-10-30
[COLOR=#000000][INDENT]Since nobody responded to this post in networking and wireless section I'm posting it here, hope forum admins won't get mad for this and I sincerely apologise for reposting here. Hello fellow Ubuntu users, I am running a 32-bit Xubuntu 12.10 on my PC and running Android 4.0.4 on my rooted SE Xperia Neo V. I have installed an application called VX ConnectBot as an ssh client so I can connect to my PC. I have ssh client installed on my computer but every time I try to connect to it via my phone it takes forever to connect and then it gives me expired connection error.

Does anyone have any idea how to run diagnostics for this or how to fix it, much obliged.
Stay brutal, my regards. :grin:[/INDENT]
[/COLOR]

---

### Post by mörgæs on 2013-10-30
If you want a most moved the best you can do is to report it, also if it's your own.

---

### Post by ajgreeny on 2013-10-30
You need **openssh-server** on your PC, not just openssh-client if you want to connect to the PC from your android device.

---

### Post by newb85 on 2013-10-30
Also, if you're running UFW, you'll need to add a rule allowing SSH.  The easiest way:
```
 sudo ufw allow ssh 
```

That's assuming you're using the default port 22.

---

### Post by LinuxUser666 on 2013-10-30
Yeah thanks for a lot of good advice here, it really was needed to do ```
sudo ufw allow ssh
``` 
because I already had **openssh-server** installed on my machine. But anyway thanks for help, much obliged.

My regards, stay brutal. :guitar:

---

