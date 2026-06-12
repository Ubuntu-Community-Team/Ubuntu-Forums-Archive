---
title: "No-Ip on Ubuntu"
date: 2019-07-31
forum: New to Ubuntu
---

### Post by grenic on 2019-07-31
How do I check if no-ip.com is running on my Ubuntu machine?

---

### Post by #&amp;thj^% on 2019-07-31
```
systemctl status noip2
```
Please remember that noip.com free accounts have a limitation: they need to be confirmed every 30 days (You will receive an email and you need to click on the link contained to update your DNS).

---

### Post by grenic on 2019-07-31
Thanks for the reply 1fallen. I am using my mates account who has the premium account to avoid the 30 day activation.

"Unit noip2.service could not be found."

How can I run it?

---

### Post by #&amp;thj^% on 2019-07-31
Try without the 2
```
systemctl status noip
```
It's hard to tell how you installed it though.
Install instructions found here: [https://www.noip.com/support/knowledgebase/installing-the-linux-dynamic-update-client-on-ubuntu/](https://www.noip.com/support/knowledgebase/installing-the-linux-dynamic-update-client-on-ubuntu/)

---

