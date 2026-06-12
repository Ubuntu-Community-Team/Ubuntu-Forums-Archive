---
title: "deluge issues"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by beanco on 2008-11-16
Hi all, I have some questions regarding  Deluge.

I have a few torrents that I need to down load but they keep showing in Deluge as stalled.... I have no idea how to get them to download.

BTW, I am still on Feisty if this is important at all.

robi

---

### Post by Efros on 2008-11-16
try quitting deluge, use killall python to make sure its dead, restart deluge, right click on each of the torrents and force re-check.

---

### Post by beanco on 2009-03-02
been a while, never got dleuge working... can you tell me how to remove it using the command line?
I want to get rid of it completely.

thanks

robi

---

### Post by Troll_the_Great on 2009-03-05
> **beanco said:**
> been a while, never got dleuge working... can you tell me how to remove it using the command line?
I want to get rid of it completely.

thanks

robi

I think the command is:

```
sudo apt-get purge deluge
```

Or, using Synaptic, click on Deluge - right click - mark for complete removal.
Hope this helps.
Cheers!

---

### Post by beanco on 2009-03-05
thanks.

got a new thread on this topic going... i love this CLI stuff.

robi

---

### Post by Troll_the_Great on 2009-03-05
> **beanco said:**
> thanks.

got a new thread on this topic going... i love this CLI stuff.

robi

Glad I could help.Did you manage to get rid of deluge?

---

### Post by mkvnmtr on 2009-03-05
I find I have better luck in Deluge if I use random ports and allow about 50 half open connections. You might just have seeds that don't wish to connect.

---

### Post by beanco on 2009-03-05
ok 50 half open connections and random ports.

I succeded n removing deluge so when I reinstall it I will keep these things in mind.

Robi

---

