---
title: "BASH: if var/string contains not"
date: 2011-10-07
forum: Programming Talk
---

### Post by Kakalle on 2011-10-07
Hi,

what would be the opposite of this statement?

if [[ $var =~ regexp ]]; then   #do something fi

I mean: IF var/string contains not THEN

This is not working:

if [[ $var !~ regexp ]]; then


Thank you very much for your help !!!

---

### Post by nothingspecial on 2011-10-07
You still need the =

eg

```
$ f=blah
$ if [[ "$f" = blah ]]; then echo "yay"; else echo "boo"; fi
yay
$ if [[ "$f" != blah ]]; then echo "yay"; else echo "boo"; fi
boo
$ f=blag
$ if [[ "$f" != blah ]]; then echo "yay"; else echo "boo"; fi
yay
```

---

### Post by matt_symes on 2011-10-07
Hi

> what would be the opposite of this statement?

if [[ $var =~ regexp ]]; then #do something fi

This is not working:

if [[ $var !~ regexp ]]; then

Thank you very much for your help !!!
You don't negate the operator that way. Have a look at these two examples

```
matthew@matthew-laptop:~$ cat test
#!/bin/bash

TESTER="hello world"

if [[ "$TESTER" =~ hello ]]; then
        echo "correct"
else
        echo "incorrect"
fi

matthew@matthew-laptop:~$ ./test 
correct
matthew@matthew-laptop:~$ 
``````

matthew@matthew-laptop:~$ cat test
#!/bin/bash

TESTER="hello world"

if [[ [COLOR=Red]**!**[/COLOR] "$TESTER" =~ hello ]]; then
        echo "correct"
else
        echo "incorrect"
fi

matthew@matthew-laptop:~$ ./test 
incorrect
matthew@matthew-laptop:~$ 
```BTW: Congrats nothingspecial! Well done on becoming forums staff.

Kind regards

---

