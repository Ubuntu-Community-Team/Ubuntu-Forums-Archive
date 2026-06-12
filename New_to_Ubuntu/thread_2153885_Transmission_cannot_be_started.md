---
title: "Transmission cannot be started"
date: 2013-06-12
forum: New to Ubuntu
---

### Post by kom333 on 2013-06-12
Hello lovely GNU/Linux users!

I have problem with my Transmission.  I noticed that a while ago but I didn't pay attention. When I try to  open it I get error same as title of this post. 
In that same window I  get message: Couldn't open "/home/kom/.config/transmission/lock":  Permission denied. I have tried to re-install it, but with no result :( 
Is there any way to fix this? I think I have to change something in the config file, but I don't know what. 
If you know how to fix it, I'll be glad! :D 

Thanks ahead.

---

### Post by andrew.46 on 2013-06-12
Could be an old process was not terminated gracefully, try:

```

mv -v /home/kom/.config/transmission/lock /home/kom/.config/transmission/lock_bak

```

and this might be enough to kickstart transmission...

---

### Post by kom333 on 2013-06-13
Ok, I will try that. Thanks.  ;)

---

### Post by kom333 on 2013-06-15
I tried that and now I can only open it from terminal, typing it: ```
sudo transmission
```. But I can't add torrent file or magnet link. When I try to add magnet link I got message from my Firefox: > The address wasn't understood. Firefox doesn't know how to open this address, because the protocol (magnet) isn't associated with any program. You might need to install other software to open this address.

---

