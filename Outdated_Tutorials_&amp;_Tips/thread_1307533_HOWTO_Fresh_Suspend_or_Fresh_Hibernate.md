---
title: "HOWTO: Fresh Suspend or Fresh Hibernate"
date: 2009-10-31
forum: Outdated Tutorials &amp; Tips
---

### Post by 3rdalbum on 2009-10-31
**Reboot and suspend.**

Some people never turn off their computers - they just suspend or hibernate them, so the machines are always ready for use in a couple of seconds.

But sometimes after you've been suspending and resuming, something doesn't work; maybe your wifi, maybe your sound, and this will continue until you actually reboot.

Of course it's a **pain** to reboot the machine and then sit around waiting for it to boot, before then suspending it. Alternatively, you could just shut down the machine; but then the next time you want to use it you'll have to wait for it to boot.

So instead you can do a "fresh suspend" or a "fresh hibernate".

Go into the terminal and type the following:

```
sudo at now + 3 minutes
```

This brings up a new prompt; it's waiting for you to type a command to run in 3 minutes.

```
pm-suspend
```

(or you can use "pm-hibernate"). Now press Control-D and the job will be saved, and you'll be returned to Bash.

Run:

```
sudo at now + 1 minute
reboot
```

And press Control-D again.

The system will reboot in 1 minute, and suspend two minutes afterwards. You can just walk away.

WARNING: You should NEVER put a laptop into a bag or case until you are sure that it has turned off or suspended.

---

### Post by bapoumba on 2009-11-05
Sorry it took so long for the tutorial to be approved. Thanks for you patience :)

---

