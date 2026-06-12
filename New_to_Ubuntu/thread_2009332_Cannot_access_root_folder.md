---
title: "Cannot access root folder"
date: 2012-06-24
forum: New to Ubuntu
---

### Post by Fuzzy Felt Bloke on 2012-06-24
Hi 

I need to access a folder in root to make some changes. When I try to access I see a message 'Do not have permission to view content'. I'm currently login as as Administrator and running 12.04LTS.

I would be grateful if someone could help me out here.

Kind regards

Fuzzy Felt Bloke

---

### Post by Fernhill Linux Project on 2012-06-24
You need to be root to do that, you can use  "gksudo nautilus" to browse the file system as root, or to go straight to the root folder as root, use the following command from a terminal :

```
gksudo nautilus /root
```

And then use ctrl & h to show hidden files.

---

