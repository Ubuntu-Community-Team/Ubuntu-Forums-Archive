---
title: "Need some informations about piping and a command."
date: 2020-07-23
forum: New to Ubuntu
---

### Post by xcfstarflight1 on 2020-07-23
Hi! I was wondering if anyone can help me figure out how to make df show used and available space in MB or GB? 
I used to program PowerShell and did some tricks with the commands to get it to show that. 
Or if there are another command i can use?

---

### Post by ActionParsnip on 2020-07-23
```

df -h

```

-h = human readable

---

### Post by Holger_Gehrke on 2020-07-23
From 'man df':> 
-h, --human-readable
              print sizes in powers of 1024 (e.g., 1023M)

-H, --si
              print sizes in powers of 1000 (e.g., 1.1G)


Holger

---

### Post by ActionParsnip on 2020-07-23
Or:
[https://stackoverflow.com/questions/16962041/how-to-get-df-linux-command-output-always-in-gb#16962064](https://stackoverflow.com/questions/16962041/how-to-get-df-linux-command-output-always-in-gb#16962064)

---

