---
title: "[SOLVED] Shutting the thing (server) off completely..."
date: 2008-08-09
forum: New to Ubuntu
---

### Post by expunkermikey on 2008-08-09
Yeah, 

Kinda' silly to ask but...

I am not hosting anything, nor is it being user for file storage. Just want to shut it down when i am not configureing things or learning stuff. Why waste the energy?

The documentation is fine and good, all the other things I have read are great, But for some reason it seems to be unversaly accepted that some things are much too basic to include.

Like:
"how do I turn this darn thing off without unplugging the machine...?"

Thanks

---

### Post by jordanmthomas on 2008-08-09
shutdown or halt will work

If you're not root, 
```
sudo shutdown
```

---

### Post by Joeb454 on 2008-08-09
run ```
sudo shutdown -P now
``` to turn it off immediately. That's what I do

---

### Post by st33med on 2008-08-09
Unplug it :)

Or:
```
sudo poweroff
```

---

### Post by expunkermikey on 2008-08-11
Thank you all.

Quite a vaiety aproaches I must say...

One of them should work.

Mikey  :)

---

### Post by Vivaldi Gloria on 2008-08-11
There is also

```
sudo halt
sudo reboot
```

---

