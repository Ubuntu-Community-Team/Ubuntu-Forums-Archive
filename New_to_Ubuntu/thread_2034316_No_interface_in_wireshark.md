---
title: "No interface in wireshark"
date: 2012-07-28
forum: New to Ubuntu
---

### Post by alokmystic on 2012-07-28
I am using Ubuntu 12.04 LTS and I am not getting any interface in wireshark, even when using it as root. any help will be highly appreciated

[IMG]http://i45.tinypic.com/2qdmps9.png[/IMG]

---

### Post by Old_Grey_Wolf on 2012-07-28
Did you start it with the command below? ```
gksudo wireshark
```

---

### Post by alokmystic on 2012-08-01
[SIZE=4]**[COLOR=Red]It worked! Thanks a lot[/COLOR]**[/SIZE]   :)

---

### Post by Old_Grey_Wolf on 2012-08-01
When you ran wireshark using gksudo, you should have gotten a warning about running it with those privileges. I would suggest following the recommendation in that warning message.

---

