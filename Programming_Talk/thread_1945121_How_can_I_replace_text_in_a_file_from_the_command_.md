---
title: "How can I replace text in a file from the command line?"
date: 2012-03-22
forum: Programming Talk
---

### Post by chandrakantpushkar on 2012-03-22
I am trying to do following

replace this 
/(48*al3*h^2*A1*R1^3+36*al3^2*h^2*A1*R1^2-6*al3*h^4*A1*R1-3*al3^2*h^4*A1)
by following
*( tay10+tay11   )

I tried with perl and sed but could not get it done..

Please help

---

### Post by Arndt on 2012-03-22
> **chandrakantpushkar said:**
> I am trying to do following

replace this 
/(48*al3*h^2*A1*R1^3+36*al3^2*h^2*A1*R1^2-6*al3*h^4*A1*R1-3*al3^2*h^4*A1)
by following
*( tay10+tay11   )

I tried with perl and sed but could not get it done..

Please help

How do you best identify the existing line? Listing all of it seems excessive.

The ^ and * characters have special meaning in the 'sed' searching commands, so you need to quote them.

```
sed -i '/^\/(48/s/$/\n\*(tay10+tay11)/' file
```

Here I matched just the beginning "/48".

---

### Post by chandrakantpushkar on 2012-03-22
I am successfully doing the following


replacing [ with u1:

sed -i 's/\[/u1:/g' epm1u1.mc

replacing al3^9 with 0
sed -i 's/al3^9/0/g' em1u2.mc

cant do

/(48*al3*h^2*A1*R1^3+36*al3^2*h^2*A1*R1^2-6*al3*h^4*A1*R1-3*al3^2*h^4*A1)

there is no problem with " ^ " caret sign

but how to handle " * "

---

### Post by Habitual on 2012-03-22
> **chandrakantpushkar said:**
> ...but how to handle " * "

Like all MetaCharacters using sed, the \escape\ key is your friend.

There may not be a "...problem with " ^ " but you should \escape\ it anyway.

---

### Post by chandrakantpushkar on 2012-03-22
yeh earlier i was considering ^ sign to be special character

now i got it done

like follows

sed -i 's/48\*A1^3\*R1^3\*T11\*T12^2-4\*h^2\*A1^3\*R1\*T11\*T12^2+96\*A1^3\*R1^3\*T11^2\*T12-8\*h^2\*A1^3\*R1\*T11^2\*T12+48\*A1^3\*R1^3\*T11^3-4\*h^2\*A1^3\*R1\*T11^3/c1\*A1^3/g' epm1u1.mc

---

### Post by sisco311 on 2012-03-22
@OP
Please don't BUMP old threads. Post moved to it's own thread.

---

