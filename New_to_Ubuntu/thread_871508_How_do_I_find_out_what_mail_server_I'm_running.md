---
title: "How do I find out what mail server I'm running?"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by BlueKnight84 on 2008-07-27
Hello.

I am a complete noob, just so that's clear.  I took over an Ubuntu system that runs a mail server but I need to know which one it is.

You see, I'm going to take a stab in the dark at installing Mailman and that's why I need to know what mail server I'm running.

Thank you for reading!

---

### Post by Thingymebob on 2008-07-27
Have a look in Sytem>Administration>Services and look for "Mail Agent"

---

### Post by ghostdog74 on 2008-07-27
assuming its port 25
```

lsof -i tcp:25

```
then look for the PID that is running. Do a ps -ef and grep for the PID, you will see which command invokes the mail server.

---

