---
title: "Allowing network printing on firewall"
date: 2014-02-22
forum: New to Ubuntu
---

### Post by amber4 on 2014-02-22
I set up ufw a couple days ago, only allowing ports 25, 53, 80, 110, 443, 51413, and 6969 for TCP and 53, 67, 68, and 51413 for UDP, according to [https://wiki.ubuntu.com/BasicSecurity/Firewall](https://wiki.ubuntu.com/BasicSecurity/Firewall). I then realized that my HP Photosmart 6510 series printer wouldn't print from network any more. I'm thinking there's probably a port I missed allowing, and if there is, what is it?

---

### Post by deadflowr on 2014-02-22
You're probably printing using CUPS.
Which usually uses port 631.
You can look over and manage cups with pasting this in  a URL of a browser
```
localhost:631
```

See if any of this helps.

---

