---
title: "Emergency Broken Pipe Error"
date: 2014-05-05
forum: New to Ubuntu
---

### Post by mandar2 on 2014-05-05
Hello,

I am getting also same error, but at the beginning while booting itself and so i can't get to my desktop.

When I boot i select Ubuntu and then after disabled BIOS messages i run directly into the black screen with broken pipe error.
In my previous session i had physically removed OpenCV folder which had all it's libraries and avr32 toolchain which was not associated and was unused. plus i had done:
```
 sudo apt-get autoremove
sudo apt-get update

```

Now, i have no idea what i should do.

Thankfully I have Win7 on dual boot so at least I can get help from the forums.

Please reply.

---

### Post by Danger_Monkey on 2014-05-05
You may want to look at /var/log/boot.log.  It's not the most verbose logging in the world, but it can point you to where the real problem is.  "Broken Pipe" is pretty generic, used when communication fails between an application and the socket it uses to talk to the kernel (or other things).

---

### Post by Kirboosy on 2014-05-05
Moved to separate thread.

---

