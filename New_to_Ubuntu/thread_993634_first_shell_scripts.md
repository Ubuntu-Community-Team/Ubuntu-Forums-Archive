---
title: "first shell scripts"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by hyburn on 2008-11-25
hey guys,

im in the mood to make my ubuntu a little more efficient when it comes to getting help from you guys.

I am trying to write little shell scripts that give me info, to be faster in response time for your helping me.

here is what I have so far, but it doesnt hold the results in a window. 

#!/bin/sh
echo &#8220;here are your dmesg results&#8221;
dmesg

please help me finish this.

-drew
the warrior sheep

---

### Post by Falcorian on 2008-11-26
I'm not really sure what you're asking... "Hold the result in a window"?

If you're looking for an easy way to save the output somewhere, you can redirect it to a file like this:

```
user@computer:~$ ./hyburn.sh > file
```

Where 'file' is whatever file name you want (even if the file doesn't yet exist).

> redirects to a file and overwrites it. >> appends to the end of a file.

---

### Post by jemate18 on 2008-11-26
> **hyburn said:**
> hey guys,

im in the mood to make my ubuntu a little more efficient when it comes to getting help from you guys.

I am trying to write little shell scripts that give me info, to be faster in response time for your helping me.

here is what I have so far, but it doesnt hold the results in a window. 

#!/bin/sh
echo “here are your dmesg results”
dmesg

please help me finish this.

-drew
the warrior sheep


I think your script just added "here are your dmesg results" before displaying the dmesg output

you may do this


```
dmesg
```

This will diplay the output

---

### Post by jemate18 on 2008-11-26
ok your script is complete. you just have to make it executable

suppose your filename is mydmesg.sh

Go to the directory where it is located

```
chmod 750 mydmesg.sh
``` 

then to run it
```
sh mydmesg.sh
```

or
```
./mydmesg.sh
```

---

