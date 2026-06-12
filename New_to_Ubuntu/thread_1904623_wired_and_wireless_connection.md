---
title: "wired and wireless connection"
date: 2012-01-05
forum: New to Ubuntu
---

### Post by praneethreddy462 on 2012-01-05
iam using dell n5050 i3 processor,  iam not able to access internet through wired and wireless in ubuntu.

so please help me.

---

### Post by cariboo on 2012-01-06
It would be a big help if you gave us more information, like what networking chipsets you system uses. Could you open a terminal, and type the following command:

```
sudo lshw -C network > network.txt
```

the above command creates a text file, that you can move to a computer with a working network connection, then paste it into your next post.

---

