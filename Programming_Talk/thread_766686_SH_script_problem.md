---
title: "SH script problem"
date: 2008-04-25
forum: Programming Talk
---

### Post by diehard_hm on 2008-04-25
I have a question. I use Ac3D for 3d modelling and have installed it, when I go to the terminal and go to the bin and exec ./ac3d the application runs and the terminal stays open. I have tried to create a launcher for this but I just get a flash on the screen which I think is the terminal opening and closing and no app. I have tried to write a sh file but get the same just a flash.

here is what I did in gedit

#!/bin/sh
/home/diehard/Public/ac3dlx
./ac3d

Nothing but a flash on the screen

Thanks for your help

tony

---

### Post by tseliot on 2008-04-25
> **diehard_hm said:**
> here is what I did in gedit

#!/bin/sh
/home/diehard/Public/ac3dlx
./ac3d


It should be:

```
#!/bin/sh
cd /home/diehard/Public/ac3dlx
./ac3d
```

---

### Post by diehard_hm on 2008-04-25
Thank you, that was it..

---

