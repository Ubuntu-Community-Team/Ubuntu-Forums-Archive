---
title: "[SOLVED] Shell Script variable error."
date: 2008-08-20
forum: Programming Talk
---

### Post by ashmew2 on 2008-08-20
Hi , I just wrote this shell script ( with help from SO MANY sites).

```

varx = $(ps ux | awk '/vlc/ && !/awk/ {print $2}')
echo $varx

```

i havent included the #!/bin/sh line on top and when i try to run this file from the terminal :

# ./vlc.sh

I get the Following output :
```

./vlc.sh: line 1: varx: command not found
```

What am i doing wrong ? Please help me , Im out of my mind ](*,)](*,)

---

### Post by ghostdog74 on 2008-08-20
put #!/bin/bash on the first line
When declaring variables, no spaces
```

varx=$(ps ux | awk '/vlc/ && !/awk/ {print $2}')

```

---

### Post by ashmew2 on 2008-08-21
Thankyou

---

### Post by jinksys on 2008-08-21
Do add the [SOLVED] to your thread if you have recieved a satisfactory solution by going into Thread Tools.

---

### Post by ashmew2 on 2008-08-24
Haha  , Yeah , I almost forgot . Thanks for the heads up :)

---

