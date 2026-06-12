---
title: "Keepass (mono ?) fails to get file over Https ?"
date: 2014-04-22
forum: New to Ubuntu
---

### Post by phedon on 2014-04-22
I host my keepass2 database (kdbx) on server. It is accessible through https.
On 13.10, 12.04 (and Windows), Keepass2 would retrieve the database but on 14.04 it does not saying "Authentication or decryption has failed".
(I double-checked that it can be retrieved with cadaver)

Looking around, I tried:
1) In keepass -> Options -> Advanced -> Accept invalid certificates  (same error)
and also:
2) Tried also to import certificates for mono as stated here : [http://sourceforge.net/p/keepass/bugs/1147/](http://sourceforge.net/p/keepass/bugs/1147/) (same error)

- Keepass version 2.25
- "mono -V" gives "Mono JIT compiler version 3.2.8 (Debian 3.2.8+dfsg-4ubuntu1)"
 
Any idea ?

---

### Post by phedon on 2014-04-24
I finally got it to work after:

```
sudo apt-get install mono-complete
```

I don't know what part of this 133 MB install made the trick but it solved it !  
There is maybe a "lighter" solution...

---

