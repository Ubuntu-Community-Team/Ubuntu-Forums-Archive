---
title: "java linked list constructor question"
date: 2009-12-06
forum: Programming Talk
---

### Post by infestor on 2009-12-06
let's say i've written a simple constructor for a 2 fielded linked list node:

```

class UrlListNode{
String str;
UrlListNode next;

UrlListNode (String s, UrlListNode n){
str=s;
next=n;
 }
}

```

i can also write it with omitting next field in the constructor:

```

class UrlListNode{
String str;
UrlListNode next;

UrlListNode (String s){
str=s;

 }
}

```

...and it still works! what is the difference and how can i explain it to my teacher?

---

### Post by infestor on 2009-12-06
anyone?

---

### Post by dwhitney67 on 2009-12-06
to your teacher?  Oh, this is a homework problem...

You know the rules... or maybe not.

Anyhow, your two constructors are syntactically correct, but they do not yield the same result, unless you happen to pass (into your first constructor) a UrlListNode 'next' value equal to null.

Btw, what is the point of using CODE-tags for your code??  It doesn't appear that you have zippo wrt to indentation in your code.  Consider indenting your code statements by 2 or 3 white-spaces, or by a tab-space.

---

### Post by infestor on 2009-12-06
> **dwhitney67 said:**
> to your teacher?  Oh, this is a homework problem...

You know the rules... or maybe not.

Anyhow, your two constructors are syntactically correct, but they do not yield the same result, unless you happen to pass (into your first constructor) a UrlListNode 'next' value equal to null.

Btw, what is the point of using CODE-tags for your code??  It doesn't appear that you have zippo wrt to indentation in your code.  Consider indenting your code statements by 2 or 3 white-spaces, or by a tab-space.

thanks.
then using the second code will make more sense since i dont want to pass a null 'next' value to the constructor everytime.

---

### Post by Arndt on 2009-12-06
> **infestor said:**
> let's say i've written a simple constructor for a 2 fielded linked list node:

```

class UrlListNode{
String str;
UrlListNode next;

UrlListNode (String s, UrlListNode n){
str=s;
next=n;
 }
}

```

i can also write it with omitting next field in the constructor:

```

class UrlListNode{
String str;
UrlListNode next;

UrlListNode (String s){
str=s;

 }
}

```

...and it still works! what is the difference and how can i explain it to my teacher?

What's this "it" that works? How are your constructors called?

---

