---
title: "Help with for loop"
date: 2008-07-10
forum: Programming Talk
---

### Post by maybeway36 on 2008-07-10
Here is one of the for loops I want to use in my script:
```
for i in *.img; do
 echo `echo $i|sed s/.img//`
done
```
However, when there are no img files in the directory, it simply lists all the files in the directory instead of listing nothing.

---

### Post by forger on 2008-07-10
how about:
```

a=(`ls -1 *.[Ii][Mm][Gg]`)
for i in "${a[@]}"; do
  echo $i | sed 's/\.img//i'
done

```

---

### Post by maybeway36 on 2008-07-10
Thanks, but now I'm trying to iron out another problem. When I run my script, it gives me an error on this bit of code:
```
if [ -e *.lzm ];then
 echo "Copying Slax modules..."
fi

for i in $( ls -1 *.lzm 2> /dev/null ); do
  cp $i multicd/slax/modules/
  if [ $VERBOSE = 1 ];then
    echo \(Copied $i\)
  fi
done
```
The error is:
```
[: 325: nano-2.0.6.lzm: unexpected operator

```
(Line 325 is the third line I pasted in the top text box: "fi".)
The script doesn't stop and everything ends up fine, but I'd like to know what's causing it.

---

### Post by ghostdog74 on 2008-07-10
> **maybeway36 said:**
> Here is one of the for loops I want to use in my script:
```
for i in *.img; do
 echo `echo $i|sed s/.img//`
done
```
However, when there are no img files in the directory, it simply lists all the files in the directory instead of listing nothing.

there's no need to use echo. Also, using find may be a better option
```

find . -type f -name "*.img" | while read FILE
do
 # do processing with $FILE
done

```

---

### Post by forger on 2008-07-11
your problem is this:
> if [ -e *.lzm ]; then

I'd do like so:
```

b="`ls -1 *.lzm`"
if [[ $b != "" ]]; then echo "Copying Slax modules..."; fi

```

---

### Post by ghostdog74 on 2008-07-11
> **forger said:**
> your problem is this:


I'd do like so:
```

b="`ls -1 *.lzm`"
if [[ $b != "" ]]; then echo "Copying Slax modules..."; fi

```

the above can be shortened by using find.

---

### Post by maybeway36 on 2008-07-11
> **forger said:**
> your problem is this:


I'd do like so:
```

b="`ls -1 *.lzm`"
if [[ $b != "" ]]; then echo "Copying Slax modules..."; fi

```
The problem was that the [ command was expanding my wildcard to:
```
[ -e kdegames-3.5.9-additional.lzm  nano-2.0.6.lzm ]
```
Which would explain the extra parameter problem. Your suggestion did this too at first, but I figured out moving the quotes to the next line would help:
```
b=`ls -1 *.lzm 2> /dev/null;true`
if [ "$b" != "" ]; then echo "Copying Slax modules..."; fi

for i in $b; do
  cp $i multicd/slax/modules/
  if [ $VERBOSE = 1 ];then
    echo \(Copied $i\)
  fi
done
```
Now it seems to work perfectly. Thanks everyone for all your advice. :)

---

