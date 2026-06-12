---
title: "what is the command to find out disk space usage?"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by Linux Lover on 2008-04-30
i am showing that i am running short of disc space. 97% of my disc space already in use. i want to know what are the files or directories which are using high volume of space of my hdd.

what command should i use?

---

### Post by hermes0710 on 2008-04-30
I'm not aware of a command (it probably exists but I don't know it) but you can check through nautilus (right click the folders under "/" and select properties, then you can find out which one takes over most of your hdd's capacity)

---

### Post by kpkeerthi on 2008-04-30
```
df -h
```

Or use the Disk Space Explorer from System -> Admin

---

### Post by Linux Lover on 2008-04-30
Thank you all.

I have done it using```
find -name '*' -size +1G
```

thank you all once again.

---

### Post by ibutho on 2008-04-30
The du command is pretty good at determining disk space usage. You can pipe the output to sort for better presentation.

---

### Post by hyper_ch on 2008-04-30
```

du

```

---

