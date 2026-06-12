---
title: "How to close running applications automatically..."
date: 2012-09-12
forum: New to Ubuntu
---

### Post by visitnag on 2012-09-12
Hi,

I am running ubuntu 10.10. I know how to shutdown the system at a specific time. I want to know before the system shuts down automatically, how can I close the running applications automatically. 

thank you.

---

### Post by Lars Noodén on 2012-09-12
I'm not sure if there is a way to gracefully shutdown all processes.  It would be incumbent on the individual applications to respond properly with a shutdown signal of some kind. 

Just a wild guess but you could try [pkill](http://manpages.ubuntu.com/manpages/precise/en/man1/pkill.1.html) to send HUP or TERM or STOP some other signal to your user's processes.

```

pkill -HUP -u visitnag
pkill -TERM -u visitnag

```

If that works, then you could then use [at](http://manpages.ubuntu.com/manpages/precise/en/man1/at.1.html) to send the signal just before the shutdown.

---

