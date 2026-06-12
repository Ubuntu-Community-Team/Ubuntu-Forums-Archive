---
title: "[SOLVED] error: expected ‘)’ before ‘;’ token"
date: 2008-05-16
forum: Programming Talk
---

### Post by VChief on 2008-05-16
So, I'm getting this error:

```
error: expected ‘)’ before ‘;’ token
``` 
referencing this line:
```
 while ( a = 0; a < 5; a++ ){
```


I'm confused. What's it talking about?

---

### Post by LaRoza on 2008-05-16
> **leeward said:**
> So, I'm getting this error:

```
error: expected &#8216;)&#8217; before &#8216;;&#8217; token
``` 
referencing this line:
```
 while ( a = 0; a < 5; a++ ){
```
I'm confused. What's it talking about?

```

for (a = 0; a < 5; a++)
{

}

```

In the future, tell what language you are using and what is giving the error.

---

### Post by VChief on 2008-05-16
> **LaRoza said:**
> ```

for (a = 0; a < 5; a++)
{

}

```

In the future, tell what language you are using and what is giving the error.

Thank you...and my apologies for not including the language (C ). Why is it that for worked but not while?

---

### Post by happyhamster on 2008-05-16
while takes only 1 expression.

```

    a = 0;
    while (a < 5) {
        do stuff;
        a++;
    }

```

---

### Post by robbo96 on 2010-05-03
Post deleted -- solved it myself!

---

