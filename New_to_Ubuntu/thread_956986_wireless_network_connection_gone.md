---
title: "wireless network connection gone"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by rogerboivin on 2008-10-23
Finally decided to ditch Microsoft and loaded the latest version of Ubuntu (8.04?) on my home computer.  Everything works fine except I have lost wireless network access.  

I find most instructions to fix this expect you to know what to do or how to decipher a response to a terminal sessions and I'm too new to know that.

Is there someone who can provide instructions to determine why I have lost my wireless network?

---

### Post by bsharp on 2008-10-23
I'm sorry to say this, but you are going to have to use the terminal. Can you start by opening a terminal and copy/pasting the output of:

```
lspci | grep Ethernet
```

---

