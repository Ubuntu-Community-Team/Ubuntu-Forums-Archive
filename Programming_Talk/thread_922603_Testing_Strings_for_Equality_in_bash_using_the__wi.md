---
title: "Testing Strings for Equality in bash: using the * wildcard"
date: 2008-09-17
forum: Programming Talk
---

### Post by flummoxed on 2008-09-17
Hello,

I'm trying to figure out how to match part of a word in a shell script using the * wildcard... Here is some example code showing what I'm trying to achieve:

```

word=aSuperWord
if [ $word == *Super* ]
then
echo "Yes"
else
echo "No"
fi

```

I want the code to check to see if the substring "Super" part of the string variable that it's evaluating. However, I don't seem to be able to use the * wildcard to mean *any other characters*. Why doesn't this work?

---

### Post by adamkane on 2008-09-17
You need to use regular expressions (regex). You won't use '='. Regex is like a filter. You pass the string, and check to see if you get 'super' at the end. I'm at school. I'll respond with a better answer tonight.

---

### Post by Martin Witte on 2008-09-17
You need regular expresons indeed, e.g.
```

martin@toshibap200:~$ word=aSuperWord
martin@toshibap200:~$ echo $word
aSuperWord
martin@toshibap200:~$ [[ $word =~ .*Word ]]
martin@toshibap200:~$ echo $?
0
martin@toshibap200:~$ 
```

---

### Post by lswb on 2008-09-17
Try using this form instead, note the double brackets:

if [[ $word == *Super* ]]

---

### Post by flummoxed on 2008-09-17
> **lswb said:**
> Try using this form instead, note the double brackets:

if [[ $word == *Super* ]]

This method worked... what is it about the double brackets that makes this work?

---

### Post by adamkane on 2008-09-17
It's just another regex. Regex uses [[ ]]. The problem with comparators like == != with wildcards like *, etc. is that you will get false matches. It's better avoid it, but it's up to you of course.

---

### Post by ghostdog74 on 2008-09-17
no need to use regular expression.
```

case $variable in
 *Super* ) echo "found";;
 * ) echo "not found";;
esac

```

---

### Post by lswb on 2008-09-17
> **flummoxed said:**
> This method worked... what is it about the double brackets that makes this work?

The single [] will not use regular expressions, however, if anything inside it has a * or ? it will try to do filename expansion it it; probably not what you want in this case!

The [[ ]] form is used for regular expressions as adamkane noted above, and no filename expansion takes place inside [[ ]]

---

