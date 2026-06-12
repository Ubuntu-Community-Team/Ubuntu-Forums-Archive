---
title: "shell program not execiting?"
date: 2009-05-16
forum: Programming Talk
---

### Post by abhilashm86 on 2009-05-16
i just tried to print command arguements in reverse order, but only last arguement i printing, also it is giving some error,
[PHP]
#!/bin/sh
i=$#
while [ $i -gt 0 ]
do
eval echo \$$i
i=`expr $i-1`
done
[/PHP]
error is 
```

abhilash@abhilash:~$ sh pgm1.sh a b c
c
[: 1: Illegal number: 3-1

```
what is actually missing?
in php /$$i is not shown, here it is

#!/bin/sh
i=$#
while [ $i -gt 0 ]
do
eval echo \$$i
i=`expr $i-1`
done
~

---

### Post by kaibob on 2009-05-16
Try this:

```
eval echo \$$i
i=`expr $i - 1`
```

or better yet

```
eval echo \$$i
i=$(($i-1))
```

---

### Post by abhilashm86 on 2009-05-16
> **kaibob said:**
> Try this:

```
i=`expr $i - 1`
```

or better yet

```
i=$(($i-1))
```

yes it worked, thanks.....
after learning C++ n  object oriented, shell is little hard to crack:)

---

