---
title: "Bash variable assignment within a loop"
date: 2008-02-26
forum: Programming Talk
---

### Post by nickoli_02 on 2008-02-26
I'm trying to assign 7 different variables within a loop like so:

[PHP]  i=0
  while [ $i -le 7 ]; do
    bus$i = $(...some command i'm not at liberty to disclose...)
    let i+=1
  done[/PHP]

Bash doesn't seem to like dereferencing a variable within another variable assignment like what I'm trying to do. The error is "-bash: bus1: command not found", so dereferencing i makes bash think it's a command instead of another variable assignment. If I replace "bus$i" with "bus1" all is well. Any ideas?

Nick

---

### Post by volanin on 2008-02-26
```
  i=0
  while [ $i -le 7 ]; do
    **export** bus$i=$(...the secret commands that will change the world...)
    let i+=1
  done

```

Add the **export** (or **set**) command.
Remove the whitespaces near the = sign.

---

### Post by Martin Witte on 2008-02-26
another option
```
#!/bin/sh
i=0
while [ $i -le 7 ]
do
    i=`expr $i + 1`
    eval bus$i=`expr $i + 2`
done

```

sounds very mysterious, that undisclosed command :)

---

### Post by nickoli_02 on 2008-02-26
genius. Thanks, works like a charm. Now, say I want to compare two variables within a loop and an if statement like so:

[PHP]  while [ $i -le 7 ]; do
    export bus$i=$(...mysterious commands...)
    if [ "$smb$i" = "$bus$i" ]; then 
      echo "true"; 
    else 
      echo "false"; 
    fi
    let i+=1
  done[/PHP]

Any more brilliant ideas? :)

---

### Post by volanin on 2008-02-26
Variable names in shell are not designed to be dynamically created.
Your best option, to avoid problems, would be using arrays.
Example:

```
while [ $i -le 7 ]; do
    **bus[$i]**=$(...black magic incantations...)
    if [ "**${smb[$i]}**" == "**${bus[$i]}**" ]; then 
        echo "true"; 
    else 
        echo "false"; 
    fi
    let i+=1
done
```

This way you can even remove the export command.
Give it a try.

---

### Post by nickoli_02 on 2008-02-26
*smacks self in forehead* 

Thanks a lot. Now if only bash supported two-dimensional arrays, I'd be set. That's another problem, though.

---

### Post by chenel on 2008-06-11
Wow.  I can't believe I didn't think of that either.

Well, at least I'm not alone. :)

Good work, volanin.

---

