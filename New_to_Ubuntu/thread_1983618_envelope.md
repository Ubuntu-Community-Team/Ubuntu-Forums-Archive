---
title: "envelope"
date: 2012-05-20
forum: New to Ubuntu
---

### Post by rosswmcgee on 2012-05-20
How to return T-Bird envelope to panel once you have removed it? Ubuntu 12.04

---

### Post by uRock on 2012-05-20
> **rosswmcgee said:**
> How to return T-Bird envelope to panel once you have removed it? Ubuntu 12.04

How'd you remove it?

---

### Post by JRV on 2012-05-20
```
sudo apt-get install indicator-messages
```

---

### Post by Frogs Hair on 2012-05-20
Logout in or restart may be required after installing indicator-messages.

---

### Post by rosswmcgee on 2012-05-20
sudo apt-get remove indicator-messages

---

### Post by Frogs Hair on 2012-05-20
> **rosswmcgee said:**
> sudo apt-get remove indicator-messages

see post # 3

---

### Post by rosswmcgee on 2012-05-20
Thanks that did it, and I think I discovered why the weather app would not stay in the 

panel after I removed the indicator msgs. It would work for awhile and then disappear,

and ubuntu would leave an error msg..

---

