---
title: "excluding filw from scan"
date: 2021-01-17
forum: New to Ubuntu
---

### Post by rburkartjo on 2021-01-17
i want to run the below but exclude /timeshift from the scan
maldet --scan-all /
what would be the correct way to accomplish that /tks

---

### Post by simon-webb on 2021-01-22
```
maldet --scan-all / -x "/timeshift"
```

---

### Post by rburkartjo on 2021-01-28
tks si that did it

---

