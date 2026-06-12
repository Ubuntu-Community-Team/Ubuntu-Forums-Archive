---
title: "Problem with using shell command line arguments in awk"
date: 2008-11-26
forum: Programming Talk
---

### Post by Tasma on 2008-11-26
I've been trying to figure out the cause of this problem for a few hours already, but sadly without success. Hope someone can help me solve it.

I got a shell script which I run with 3 command line arguments and inside the shell script I run a awk script with the following command(I want to use the command line arguments in the awk script):
awk -f awkscript.awk -v one=$1 -v two=$2 -v three=$3 file.txt

Inside the awk script I got:
/one/ {print}

The problem is that the variables do not work since I get nothing returned(even though the value exists in the file). When I use "{print one}" inside the awk script I get the right input value returned. When using "/InPutValue/ {print}" it works the way it's supposed to. Any help with finding out what causes the problem and how to fix it greatly appreciated.

---

### Post by ghostdog74 on 2008-11-26
```

$0 ~ one {print}

```

---

### Post by Tasma on 2008-11-27
Thanks alot =)

Pretty simple solution, but for some reason I didn't think of this x)

---

