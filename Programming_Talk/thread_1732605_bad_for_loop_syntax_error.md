---
title: "bad for loop syntax error"
date: 2011-04-18
forum: Programming Talk
---

### Post by madhushubhu on 2011-04-18
hi,
i have program to print array elements in ascending order using bubble sort
but it is given error in for loop syntax :bad loop syntax

here my for loop

echo "enter array elements"
read n
echo "enter array elements"
for ((i=0;i<n;i++))
do
read a[$i]
done

please give some sugestions

thanks in advance

---

### Post by TeoBigusGeekus on 2011-04-18
No problems here with your code.
I'm using bash though.
Have you added
```
#!/bin/bash
```
on top of your script?
(or is bash a link to dash in ubuntu? I don't know)

---

### Post by kaibob on 2011-04-18
Like TeoBigusGeekus, I tried your script and it works fine with bash. It does not work with dash (/bin/sh) which does not support arrays or ((...)). For more information:

[https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)

---

### Post by cgroza on 2011-04-18
You have a missing shebang!

---

