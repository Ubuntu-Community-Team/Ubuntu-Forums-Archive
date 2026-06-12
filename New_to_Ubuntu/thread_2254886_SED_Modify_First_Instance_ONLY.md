---
title: "SED Modify First Instance ONLY"
date: 2014-11-30
forum: New to Ubuntu
---

### Post by Brian_Strauch on 2014-11-30
*Before Modification*
```
brian@strauch:~$ cat test
Banana
Banana
Apple
Apple
Banana
Apple
```

> The following will change ALL instances of 'Apple' to 'Orange'...
> sed -i '/Apple/ c\Orange' test

*After Modification*
```
brian@strauch:~$ cat test
Banana
Banana
**Orange**
**Orange**
Banana
**Orange**
```

> How to I change ONLY THE FIRST instance of 'Apple' to 'Orange' below?

*Desired Result*
```
brian@strauch:~$ cat test
Banana
Banana
**Orange**
Apple
Banana
Apple
```

Thanks for the help!

---

### Post by steeldriver on 2014-11-30
I'm not familiar with the meaning of c\

However in GNU sed you could try something like

```

sed '0,/Apple/ s//Orange/' test

```

which replaces 'Apple' with 'Orange' only in the address space up to and including the first instance of 'Apple'

---

### Post by Brian_Strauch on 2014-11-30
How would the i\ command (which inserts text above the line with the pattern) be integrated into this?
```
sed '0,/Apple/ i\Orange' test
```
^ That doesn't seem to work...

---

### Post by steeldriver on 2014-11-30
The -i is an **option** to the sed program not an editing command, although there is an i (insert) command - that's different. So you would do

```

sed **-i** '0,/Apple/ s//Orange/' test

```

---

### Post by nerdtron on 2014-12-01
Original:
```
kenneth@nerdtron:~$ cat test
Banana
Banana
Apple
Apple
Banana
Apple

```

To replace all instances use the /g for global replacement.
```
kenneth@nerdtron:~$ sed 's/Apple/Oranges/g' test 
Banana
Banana
Oranges
Oranges
Banana
Oranges
```

To replace only the first instance
```
kenneth@nerdtron:~$ sed '0,/Apple/s/Apple/Oranges/' test 
Banana
Banana
Oranges
Apple
Banana
Apple
```

The above examples will not edit the original file but will only output on the command line.
use the "sed -i" for inplace, which will edit the original file.

---

