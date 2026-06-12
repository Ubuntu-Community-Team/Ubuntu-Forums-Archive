---
title: "Continually send out DNS look up request for &quot;mail&quot;"
date: 2014-01-09
forum: New to Ubuntu
---

### Post by lance7 on 2014-01-09
I use Ubuntu 12.04.
I found with wireshark that my PC always send out DNS look up for "mail", with different source port.
Yes, the look up from different ports every time.
How can I find out which application is crazy and stop this weird thing.
Thanks!

---

### Post by lance7 on 2014-01-09
Solved by killall [B]nullmailer-send
[/B]Look up "mail" cause by [B]/etc/nullmailer/remotes
[/B]If rm all file upder **/var/spool/nullmailer/queue**, it will not look up anymore.

Still don't know why so many messages I need to send...

---

