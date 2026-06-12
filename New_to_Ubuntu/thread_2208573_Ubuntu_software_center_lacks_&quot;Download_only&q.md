---
title: "Ubuntu software center lacks &quot;Download only&quot;"
date: 2014-03-01
forum: New to Ubuntu
---

### Post by Ardeshir on 2014-03-01
HI everyone !
Last night I was surfing software center and I found 4 interesting updates and started them all .
I slept and in the morning I found out only the first one is downlaoded (which was a FireFox plugin) and It was waiting for my approval to install and it didn't download the rest .
I was thinking if there is an option like synaptic which just downloads the packages (without installing) or is there an option to tell it to continue downloading without installing ?
Thanks !

BTW isn't there a speed limiter or a plugin which limits download speed in software center ??
Thanks !

---

### Post by vasa1 on 2014-03-01
Please reveal the identities of the "interesting updates". Maybe someone can then explain why what happened happened.

---

### Post by Ardeshir on 2014-03-01
I think it doesn't matter ! I  just tried to install some softwares and updates of some other softwares .
But the matter is it stopped after downloading the first one !

---

### Post by Buntu Bunny on 2014-03-01
I think you would be better off using the Update Manager or the command line for updates. Update Manager should be notifying you when updates for your installed software are available. Then choose how you wish to update.

---

### Post by ian-weisser on 2014-03-01
> **Ardeshir said:**
> Last night I was surfing software center and I found 4 interesting updates and started them all .

Software Center is intended for beginners, so it has a limited feature set and sometimes oversimplifies.

Parallel download-and-install is simply not possible using Debian's package manager - that's a good thing, it prevents all kinds of system-breaking problems. So Software Center queues the second and third and later changes. Rather than confuse the unskilled user, it tries to hide the complexity.

> **Ardeshir said:**
> I was thinking if there is an option like synaptic which just downloads the packages (without installing) or is there an option to tell it to continue downloading without installing ?

No. That is not a beginner task.

Your usage indicates that Software Center may no longer be an appropriate tool. You are not a beginner anymore, and do not need the  training wheels.

> **Ardeshir said:**
> [Is] there a speed limiter or a plugin which limits download speed in software center ?

No. What would be the purpose or benefit?
If your current mirror is slow, try a faster mirror or investigate the bandwidth your ISP provides.

---

### Post by Ardeshir on 2014-03-01
@Buntu Bunny Thanks for tge advice .
By "Updates" I meant "Optional add-ons" , sorry for mistake , that's because of my weakness in English .

@ian-wiesser so what is a more advanced package manager ?
Is synaptic fine or are there better options out there ?

BTW The reason I need a speed limiter is I have a slow internet connection (my maximum speed is 20 kbps) and when I'm downloding something I can't surf the web .

---

### Post by ian-weisser on 2014-03-01
Users who want advanced package management features should use Synaptic, aptitude, and/or apt-get.
And, of course, important helper applications like apt-cache, rmadison, and dpkg.

---

### Post by artie3 on 2014-03-05
I think you can do so by using the apt-get command.

Check out the help entry for apt-get.

```
man apt-get
```

Enjoy.

Artie

---

