---
title: "bash - send to gnome 3 notification"
date: 2011-10-14
forum: Programming Talk
---

### Post by sonicb00m on 2011-10-14
I'd like to send a message to the gnome 3 notification area but I can't figure it out.

Can anyone help?

---

### Post by sisco311 on 2011-10-14
Not really a bash question, but you can use notify-send
```
notify-send -i /path//to/icon.png "SUMMARY" "BODY"
```

---

### Post by sonicb00m on 2011-10-15
Thanks, that's perfect!

---

