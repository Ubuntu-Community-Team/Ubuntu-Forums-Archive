---
title: "Trying to run a custom xkbmap on startup"
date: 2014-03-16
forum: New to Ubuntu
---

### Post by Daan_Celie on 2014-03-16
Hi there,

I have an edited xkbmap file (which fixes the caps lock delay problem) which I want to run on startup. I've tried adding it to rc.local and I've tried creating a startup script in /etc/init.d but none of these methods work.

The command that should run on startup is the following one:
xkbcomp /home/username/myxkbmap $DISPLAY
I did some research on the internet about this but I couldn't  find anything (understandable) about this topic.

I'm still pretty new to Linux so I hope you guys can help me :)

Thanks.

---

