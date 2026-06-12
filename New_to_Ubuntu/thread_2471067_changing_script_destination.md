---
title: "changing script destination"
date: 2022-01-20
forum: New to Ubuntu
---

### Post by rburkartjo on 2022-01-20
how to change this script so it goes to my home folder not desktop

#!/bin/bash
crontab -l > $HOME/Desktop/crontabBackup-`date +"%d-%m-%Y"`


tks

---

### Post by him610 on 2022-01-20
I am not 100% sure about this, but how about trying...
```

#!/bin/bash
crontab -l > $HOME/crontabBackup-`date +"%d-%m-%Y"`

```

---

### Post by rburkartjo on 2022-01-20
him tks works just fine

---

