---
title: "firefox 3 refuses all connection when there are 30 active downloads"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by afeasfaerw23231233 on 2008-07-09
firefox 3 refuses all connection when there are 30 active downloads. it cannot connect to any webpages. but it doesn't have this problem if there are only 29 active downloads. how can i fix this? can i increase it to 100?

edit: i find out this in about:config
network.http.max-connections 30
i set it to 10000 now 

p.s. why is the default value 30?

---

### Post by gressen on 2008-07-09
Greetings,

To change the connection limit type "about:config" in your Firefox address bar, then change "network.http.max-connections" to whatever you like.

cheers

---

