---
title: "Turning off Ubuntu 12.04 info messages"
date: 2013-02-11
forum: New to Ubuntu
---

### Post by Crash54 on 2013-02-11
I'm using Ubuntu 12.04 and accessing the internet with wireless connection.  Every so often it seems compelled to let me know that my wired connection is disconnected.  Is there any way to turn this pop-up messaging off?  It is somewhat annoying because it obscures the information beneath it and makes it difficult to click on something that it is covering up.

---

### Post by Frogs Hair on 2013-02-11
There are some options in the dconf Editor but I have not experimented with them . I am using Gnome as well as Unity. 
```
sudo apt-get install dconf-tools
```

---

### Post by grahammechanical on 2013-02-11
You could try going to Edit connections and unticking Automatically connect.

Regards.

---

### Post by Crash54 on 2013-02-11
> **Frogs Hair said:**
> There are some options in the dconf Editor but I have not experimented with them . I am using Gnome as well as Unity. 
```
sudo apt-get install dconf-tools
```
Thanks for your reply.

Ok, I got the dconf Editor and took a look at it.  Didn't see anything like the screen shot you showed.  Maybe the selection is buried down a path?  Can you send the full path to it?  I did poke around a bit, but the top level is pretty sparse with entries ... not sure if the installation I have is the same (I have Ubuntu 12.04) and that's the reason or what.

---

### Post by Crash54 on 2013-02-11
> **grahammechanical said:**
> You could try going to Edit connections and unticking Automatically connect.

Regards.
I think the Edit connections entry is in early distributions of Ubuntu.  I'm using 12.04 which doesn't have the same kind of menu scheme.

---

