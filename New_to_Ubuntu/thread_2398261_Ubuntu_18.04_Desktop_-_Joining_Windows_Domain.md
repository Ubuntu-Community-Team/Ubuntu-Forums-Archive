---
title: "Ubuntu 18.04 Desktop - Joining Windows Domain"
date: 2018-08-09
forum: New to Ubuntu
---

### Post by edunnington on 2018-08-09
Hello Everyone,

I am attempting to join my Ubuntu 18.04 desktop to our windows domain. I am using SAMBA/SSSD to do this, i was able to get a ticket from my DC server but when i use command:

```
net ads join -k
```

i get the error:

```
Failed to join domain: failed to lookup DC info for domain 'MY.COMPANY' over rpc: {Operation Failed} The requested operation was unsuccessful.
```

I can ping my two DC controllers and they resolve via DNS. I have googled everywhere and cannot seem to find anything to help me. I suspect that there is a file that i missed but i do not know what this command looks up for DNS records. I am not super savey with Ubuntu but i am trying to learn. Any help is appreciated as always, please let me know if there is anything further i need to provide.

Thanks,

---

### Post by wildmanne39 on 2018-08-09
*Thread moved to **New to Ubuntu for a more appropriate fit**.*

---

### Post by edunnington on 2018-08-09
Thanks, i didnt know where to put this topic.

---

### Post by edunnington on 2018-08-10
Any help here?

---

