---
title: "[SOLVED] How to Change Directories that has spaces in terminal"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by fr.theo on 2008-06-22
Hello, Everyone 


I was wondering If any one knew how to change a directory that has a space in it eg. "Linux Is The Best" compared to "Linuxisthebest", I know how to change directories with whole names easily but those with spaces I am having difficulty.


any help would be much appreciated.


Kind Regards.

Fr. T

---

### Post by Oldsoldier2003 on 2008-06-22
> **fr.theo said:**
> Hello, Everyone 


I was wondering If any one knew how to change a directory that has a space in it eg. "Linux Is The Best" compared to "Linuxisthebest", I know how to change directories with whole names easily but those with spaces I am having difficulty.


any help would be much appreciated.


Kind Regards.

Fr. T

cd Lin [tab]

---

### Post by fahadsadah on 2008-06-22
This would only work if there was nothing else in the directory beginning with Lin.
It would be more correct to do a ```
cd Linux\ is\ The\ Best
```

---

### Post by Oldsoldier2003 on 2008-06-22
or you can escape the spaces with \ and end the name with / like so:

```
cd Linux\ is\ the\ best/
```

---

### Post by vvvladut on 2008-06-22
You have to precede the spaces with a backslash symbol: \

Like this:

```
you@yourdesktop:~$ cd Linux\ Is\ The\ Best
```

---

### Post by fahadsadah on 2008-06-22
The forward slashs are unneccesary, and all they do is help to make a picket fence.

---

### Post by Oldsoldier2003 on 2008-06-22
nvm typoed when comparing the commands. Either way works fine. But from a practical stanpoint , use dashes or underscores when naming directories instead of spaces and you'll never have this issue :)

---

### Post by ad_267 on 2008-06-22
You can also use:
```
cd "Linux Is The Best"
```

You don't need a / at the end.

---

