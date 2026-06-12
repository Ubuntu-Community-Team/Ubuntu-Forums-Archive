---
title: "does find command can't recognize files with name [ ]...."
date: 2015-06-17
forum: New to Ubuntu
---

### Post by efonde on 2015-06-17
Hi,

So I have some archive files with name "[abc1] xxxx" .zip / .rar.
I tried using find command in terminal:
```
find ./ -iname '[abc1]*' 
``` 
the result was not what I expected, it listed all the files not related to the files I'm looking.

but if i use:
```
find ./ -iname '*abc1*' 
```
the result managed to find some files along with the files I'm looking for ("[abc1] xxx"). 

Could someone point out the right way to do it? thank you

---

### Post by steeldriver on 2015-06-17
The square brackets have special meaning in the match syntax (denoting a set or class of characters) - if you want to match *literal *brackets you need to 'escape' them e.g.

```

find . -iname '\[abc1\]*'

```

---

### Post by efonde on 2015-06-17
> **steeldriver said:**
> The square brackets have special meaning in the match syntax (denoting a set or class of characters) - if you want to match *literal *brackets you need to 'escape' them e.g.

```

find . -iname '\[abc1\]*'

```

thank you so much! Just what I need.

---

