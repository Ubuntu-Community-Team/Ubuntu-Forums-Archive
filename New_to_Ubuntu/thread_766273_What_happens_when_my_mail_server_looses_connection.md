---
title: "What happens when my mail server looses connection to isp ?"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by chrisdee on 2008-04-25
Hello.

Im running a Ubuntu 7.10 server with apache, mail (postfix/courier), ssh, samba, etc services.

I wonder what happens to my email when my server looses
connection with my ISP provider ?

This has happened some times because they have worked on their
lines. Are my emails qued on another server in the mean time,
or can they get lost ?

---

### Post by hyper_ch on 2008-04-25
generally if the sending mail server can't reach the destination it will try again... I think, depending on the configuration, up to 7 days and if the mail could not be successfully transmitted to the receiving email server, then the sender should get a notice that the other email server couldn't be reached.

---

### Post by jaytek13 on 2008-04-25
I think the default is actually 72 hours before the mailserver will give up.

---

### Post by hyper_ch on 2008-04-25
you might be right on that...

However if the mailserver gives up, you will never receive anything if you are the recipient... only the sender will then get this notice.

---

