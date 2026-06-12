---
title: "How to differ network processes from normal process??"
date: 2009-11-17
forum: Programming Talk
---

### Post by K-Z on 2009-11-17
Is it possible to separate processes which require internet connection (or network) from normal processes running in the computer??? If yes, how?? Can it be done using their descriptors??
plz help.....

---

### Post by Zugzwang on 2009-11-17
You can check which process currently have open ports and/or connections:

```

netstat -p

```

---

### Post by Arndt on 2009-11-17
> **K-Z said:**
> Is it possible to separate processes which require internet connection (or network) from normal processes running in the computer??? If yes, how?? Can it be done using their descriptors??
plz help.....

lsof -i may be useful.

---

### Post by K-Z on 2009-11-18
> **Arndt said:**
> lsof -i may be useful.

Thanks for the reply

---

### Post by K-Z on 2009-11-21
> **Zugzwang said:**
> You can check which process currently have open ports and/or connections:

```

netstat -p

```

Can you please tell me the data structure accessed by the netstat command can can help me to know for each process, whether it is normal process or network based one???? plzz help.....

---

### Post by CptPicard on 2009-11-21
Why not take a look inside netstat's source yourself?

---

