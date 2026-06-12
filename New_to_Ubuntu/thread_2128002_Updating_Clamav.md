---
title: "Updating Clamav"
date: 2013-03-21
forum: New to Ubuntu
---

### Post by mitmag on 2013-03-21
When trying to update Clamav using Freshclam, I get this message:
ERROR: Can't change dir to /usr/local/share/clamav
I am using Version 10.04 and have Version 97.7 Clamav loaded.
Can anyone please help me?

---

### Post by DuckHook on 2013-03-22
I hesitate to respond to a thread in which I cannot help directly, but:

1. Why are you using 10.04? Support will be dropped in a few days.
2. Why do you use antivirus? In Linux, this is like adding wings to an Elephant.

---

### Post by lisati on 2013-03-22
As well as 10.04 nearing the end of its supported life, which could cause issues in itself, you need to use:
```

sudo freshcleam

```
You will be asked for your password, which won't be shown on the screen while you type.

---

