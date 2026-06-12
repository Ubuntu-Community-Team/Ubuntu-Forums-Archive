---
title: "[bash]writing text to write protected file"
date: 2009-09-29
forum: Programming Talk
---

### Post by Jordanwb on 2009-09-29
I'm making a bash script that will be run as non-root but will need root privileges when needed. Currently I'm trying to echo "deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main" to /etc/apt/sources.list This is what I have so far:

```
#!/bin/sh

echo "deb http://wine.budgetdedicated.com/apt jaunty main" | sudo /etc/apt/sources.list
tail /etc/apt/sources.list
```

I'm not sure what to put between sudo and the file path.

---

### Post by falconindy on 2009-09-29
sudo tee -a /etc/apt/sources.list

---

### Post by Jordanwb on 2009-09-29
Thanks.

---

