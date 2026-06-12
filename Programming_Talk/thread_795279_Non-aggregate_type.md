---
title: "Non-aggregate type"
date: 2008-05-15
forum: Programming Talk
---

### Post by markoklacar on 2008-05-15
Hi,

I have two problems.

I have a class a called Edit that contains the following:

Header
```
void setCharAt(int index,char ch);
void rubout(int index) const;
char text[];
```



Problem 1:
Now, the rubout function takes an index and it's supposed to do something with this index in the char text[]. To be more specific, it's supposed to remove the char at the index position and pack the array.

The thing is when I try to get the length of the char text[] I get this:

```
request for member `length' in `this->Edit::text', which is of on-aggregate type `char[0]'
```

Problem 2:
When I call the setCharAt(int index, char ch) it looks like this:

```
Edit::setCharAt(1,'v');
```

The error I get for this is:

```
passing `const Edit' as `this' argument of `void Edit::setCharAt(int, char)' discards qualifiers
```



What am I doing wrong? Do you need to 

Cheers.

---

