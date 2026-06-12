---
title: "Question to for in loop"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by hovzio on 2008-06-09
Hi, I've been learning about shell scripting and have been working on this the last few hours... :(
I'm new to shell scripts and this is my first bout with a for in loop.An example out of a book I'm working with:

```
for i in *
do 
     if [ -d "$i" ];then
             echo "$i"
     fi
done
```

I understand the concept of the example its just I wanted (for exp. purposes) to add another command  (example ls -l) in there and I noticed it didn't work.Why is this and how can I make it happen?

```
for i in *
do 
     if [ -d "$i" ];then
             echo "$i"
             ls -l "$i"  #doesn't work..
             echo `ls -l "$i"`  #dido, I know its far fetched
             ls -l "$i" 1>&2    # nope
     fi
done
```

How can I get the output of ls -l (or any command of that nature) to my screen. I know its a real simple answer...Any direction or help to any answer would be fully appreciated.

---

### Post by Cypher on 2008-06-09
I tried the following code in a file called 'foo' on my Kubuntu 8.04 and it worked fine.
```

for i in *
do
        if [ -d "$i" ]; then
                echo "$i"
                ls -l $i
        fi
done

```
I executed the command as
```

sh foo

```

---

### Post by hovzio on 2008-06-09
Thanks!!

---

