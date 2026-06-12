---
title: "[SOLVED] Need some help with sed"
date: 2008-03-11
forum: Programming Talk
---

### Post by Dr Small on 2008-03-11
I was never very talented with sed, and understanding it has always be tough. But I have a homemade script here and here is what my output is:

```
drsmall@darkghost:~$ netload | awk '/RX/ {print $2}'
bytes:905512961

```

Well, I want to take sed and remove "bytes:" from that output so only the numbers are the output and have tried this:
```
netload | awk '/RX/ {print $2}' | sed '/bytes:/ d'
```

But I don't get any output now. Is there anyone who knows sed that can help?

Dr Small

---

### Post by markd on 2008-03-11
It would be 

```
sed 's/bytes://'
```

i.e. substitute the string 'bytes:' with nothing.

---

### Post by Dr Small on 2008-03-11
Aha! That did the trick! Thanks :)
I was reading on other places, and the more I read, the less it worked and the more confused I became, but what you posted looks quite simple :)

Thanks again.

Dr Small

---

### Post by ghostdog74 on 2008-03-11
> **Dr Small said:**
> 
```
drsmall@darkghost:~$ netload | awk '/RX/ {print $2}'
bytes:905512961

```

Well, I want to take sed and remove "bytes:" from that output so only the numbers are the output and have tried this:

you can do everything in awk, why do the unnecessary?
```

netload | awk '/RX/ { sub(/bytes:/,"",$2);print $2}'

```

---

