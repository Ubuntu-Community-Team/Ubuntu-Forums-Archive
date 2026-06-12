---
title: "Delete numbering for each line"
date: 2008-07-23
forum: Programming Talk
---

### Post by antm88 on 2008-07-23
Hi, I have a file with about 2000 lines, each begins with a number like so:

...
125 $line125
126 $line126
127 $line127
...

The numbers do not have leading zeros, and I would like to remove the space after them as well. The text also contains numbers and spaces.

How can i just remove the numbers and the space, ending with an output of:

...
$line125
$line126
$line127
...

I would also like to try and avoid doing it with a while loop as the script needs to run quickly.

Thanks for any help!
Ant

---

### Post by Trumpen on 2008-07-23
Try this:

[PHP]sed -i 's/^[0-9]\{1,\} \(.*\)$/\1/'  file[/PHP]

---

### Post by WW on 2008-07-23
Trumpen's sed command will work; a slightly simpler version is
```

sed -i -r 's/^[0-9]+ //' file

```

---

### Post by ghostdog74 on 2008-07-23
its easier with awk/cut. No regular expression.
```

awk '{print $2}' file 
cut -f2 -d" " file

```

---

### Post by WW on 2008-07-23
> **ghostdog74 said:**
> its easier with awk/cut. No regular expression.
```

awk '{print $2}' file 
cut -f2 -d" " file

```
These won't work, because
> **antm88 said:**
> The text also contains numbers and spaces.

and I interpret the original post as meaning only the first number and space immediately after it are to be removed.

---

### Post by ghostdog74 on 2008-07-23
I see, then
```

cut -d" " -f2- file

```
should be fine, assuming only one space after the number. otherwise
```

awk '{$1="";sub(/^ /,"")}1' file

```

---

### Post by nanotube on 2008-07-24
> **ghostdog74 said:**
> its easier with awk/cut. No regular expression.
```

awk '{print $2}' file 
cut -f2 -d" " file

```

for some values of "easier" :)
i think that regular expressions (a more or less standard feature set) are easier than learning the idiosyncratic particulars of some commands. ;)

---

### Post by ghostdog74 on 2008-07-24
> **nanotube said:**
> for some values of "easier" :)
i think that regular expressions (a more or less standard feature set) are easier than learning the idiosyncratic particulars of some commands. ;)
different individuals have different definition of what "easier" means. My definition of "easier" is easier to read and debug/modify code w/o regexp. Regular expressions are powerful and i use them often too, but if i were to write code for other people, i would choose to write them no regexp (or minimal regexp) as far as possible. well, that's just me.

---

