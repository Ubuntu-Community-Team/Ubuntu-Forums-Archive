---
title: "[SOLVED] 8.04 shutdown woes"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by aszxcv on 2008-11-26
here is the code i usually run to shutdown
> sudo shutdown -h now

my pc always shutdown fine but i always get a message bus connection fail 

so i was reading another thread about printing shutdown error to a log file via this code here so i can post result here just to make sure everything is on the up and up
> sudo shutdown -vh now >> /var/log/shutdown.log 2>&1
i enter it but i get this  > bash: /var/log/shutdown.log: Permission denied 


when i try to run that script

---

### Post by aszxcv on 2008-11-26
any help as to why i get Permission denied :confused:

---

### Post by CatKiller on 2008-11-27
Is there a reason that you especially want your shutdown log in /var? I suspect that with the command you're running, only the shutdown command is running as root. The rest is running as a normal user. Which is why you can't write to /var/log. There's probably some clever syntax that lets you run the whole thing as root, but I don't know what it is.

Personally, I'd just change */var/log/shutdown.log* with *~/Desktop/shutdown.log* if all you want it for is to post information here.

Or you could run ```
sudo -i
shutdown -vh now >> /var/log/shutdown.log 2>&1 
```

---

### Post by Bucky Ball on 2008-11-27
Sorry to butt in, but is your avatar a 16 track reel to reel, CatKiller? Too cool.

---

### Post by maxbaldwin on 2008-11-27
A better code to run it would be:

```
cd && sudo shutdown -h now > shutdown.log
```

Because you won't need to run everything as sudo, and the file will be placed in your home directory.

---

### Post by CatKiller on 2008-11-27
> **Bucky Ball said:**
> Sorry to butt in, but is your avatar a 16 track reel to reel, CatKiller? Too cool.

Yeah, a Tascam MS-16 I used to use when I was working with a 15-piece ska band. It was an important part of the sound they wanted. I don't work with them any more and use an Alesis HD24 instead. It's technically better in every way, but using it is much less human than using tape.

---

### Post by aszxcv on 2008-11-27
> **maxbaldwin said:**
> A better code to run it would be:

```
cd && sudo shutdown -h now > shutdown.log
```

Because you won't need to run everything as sudo, and the file will be placed in your home directory.

thanks

---

