---
title: "java ignoring SIGPIPE signal"
date: 2014-06-27
forum: New to Ubuntu
---

### Post by brian8765 on 2014-06-27
Hi guys,
Lets say I have a java process, that just prints out lines and lines of text.
I want to head -n 10 that java program, so I do 
```
java test | head -n 10
```

This however, does not kill the java process, it hangs instead :
```

root@laptop:/path# java test | head -n 10
line 
line 
line 
line 
line 
line 
line 
line 
line 
line 


```

I want to be able to put in something like 
```
 trap "kill $$" SIGPIPE 
```

to kill the java process when the other end of the pipe closes

How would I do this or any better ways of doing it? 
Thanks  in advance.

---

### Post by brian8765 on 2014-06-27
I have this:
```

mkfifo /pipe; java test > /pipe & head -n 10 /pipe; lsof /pipe 2>/dev/null | awk '$2 ~ /[0-9]/ {print $2}' | xargs kill; rm /pipe

```

But its really really messy

---

### Post by brian8765 on 2014-06-27
i guess this is better.
```
mkfifo /pipe/ ;java test > /pipe & head -n 10 /pipe; kill $!; rm /pipe
```

Does anyone know how to do this with regular pipes??

---

