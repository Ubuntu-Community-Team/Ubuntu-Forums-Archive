---
title: "how to add a space as prefix through bash script ?"
date: 2008-12-30
forum: Programming Talk
---

### Post by change.chases.me on 2008-12-30
i am trying to achieve the following transformation through sed command :
hello -->   <a href="xxx">hello</a>

but the space between 'a' and 'href' is creating problems, as the arguments of sed command are themselves separated by spaces.
thanks.

---

### Post by jpkotta on 2008-12-30
Quoting.

```
echo hello | sed "s#\(.*\)#<a aref=\"xxx\">\1</a>#"
```

---

### Post by snova on 2008-12-30
Either quote the regexp, or escape the space by putting a backslash before it.

---

### Post by change.chases.me on 2008-12-31
thanks for the solutions, but i still cant get my stuff working.
the actual problem is that, i am calling a shell script from java program. here is the code of the script i am running through the program:
```
sed -i "s/$2/$3$2$4/g" $1
```
and this is a part of the java code, the string s is being executed through the program :
```
String s = "sh usesed ./* hello <a href=\"hello.html\"> <\\/a>";
```

the purpose of the system is to scan all the files in the current folder, look for a dynamic word (in above cases i have taken "hello") and make it an html link to dynamic_word.html ("hello.html" in above case). 
PS : This is not a homework problem (as some of the people may think).

---

### Post by ghostdog74 on 2008-12-31
you should look into Java's own substitution functions or regular expression libraries.

---

### Post by change.chases.me on 2008-12-31
> **ghostdog74 said:**
> you should look into Java's own substitution functions or regular expression libraries.

I have done it that way, it is just that I want to try this way too.... something new.

---

