---
title: "What is the difference between post and pre increments to a variable?"
date: 2009-10-10
forum: Programming Talk
---

### Post by s3a on 2009-10-10
(Java Programming Language)

I understand that x++; and ++x; have the same effect because they are alone but when they are not alone like:

y = ++x; or y = x++;      what is the difference?

Any input would be greatly appreciated!
Thanks in advance!

---

### Post by Bachstelze on 2009-10-10
y = x++; is equivalent to y=x; x=x+1;
y = ++x; is equivalent to x=x+1; y=x;

It's just syntactic sugar, you use one or the other depending on what you want to store in y.

---

### Post by s3a on 2009-10-10
That makes it clear! Thanks!

---

### Post by pbrockway2 on 2009-10-10
Another way of looking at it...

x++and ++x are both expressions and both lead to x being incremented: that is 1 is added to the value of x and the result is stored back into x.

But being expressions they also have a value.  And that value is important if you go on to do other things like assign that value to a variable.  The value of "x++" is the value x had before the new value was stored and the value of "++x" is the value x ended up with after the new value was stored.

That's a bit long winded, but I mention it because there are cases where a literal application of what Bachstelze posted might lead you into trouble.  I don't like to post an example because it's so contrived, but the thing to remember with things like

```

... = x++;

```

is that it means "assign to the left hand side whatever x used to be before the increment".

---

