---
title: "Hypothetical problem involving integral promotion  from &quot;The C book&quot;"
date: 2011-10-03
forum: Programming Talk
---

### Post by V for Vincent on 2011-10-03
Hi, I'm currently in an embedded systems course and the lecturer recommended that we brush up on C. I'm going through the C book (available online [here]("http://publications.gbdirect.co.uk/c_book/chapter2/expressions_and_arithmetic.html")), trying to get the dirty details as well, but I'm a bit stuck on the final paragraph of section 2.8.1.2. I don't see the problem the author is trying to outline. I see that you might expect integral promotion to be applied, but as long as the value of the right operand is unchanged when it is hypothetically promoted, it should still fit in the char type, shouldn't it?

I can see that there shouldn't be a problem with this kind of assignment when integral promotion is not applied, but I don't see why it would be harmful if it was. Any help?

---

### Post by karlson on 2011-10-03
> **V for Vincent said:**
> Hi, I'm currently in an embedded systems course and the lecturer recommended that we brush up on C. I'm going through the C book (available online [here]("http://publications.gbdirect.co.uk/c_book/chapter2/expressions_and_arithmetic.html")), trying to get the dirty details as well, but I'm a bit stuck on the final paragraph of section 2.8.1.2. I don't see the problem the author is trying to outline. I see that you might expect integral promotion to be applied, but as long as the value of the right operand is unchanged when it is hypothetically promoted, it should still fit in the char type, shouldn't it?


The author is describing a problem in next to last paragraph of the following:
```

char c = 1024;

```
The result of doing this is implementation defined according to the book.

> 
I can see that there shouldn't be a problem with this kind of assignment when integral promotion is not applied, but I don't see why it would be harmful if it was. Any help?

See the case I mentioned above.  Calculate the number of bits on the left and the right side of the assignment and try to think of what should happen.

---

### Post by V for Vincent on 2011-10-03
The left hand operand can hold at least 8 bits, but to represent the right hand operator as a signed int, 12 bits are needed (and my machine actually uses 64). So you would get an implementation defined conversion. But I'm afraid I still don't see the problem if the right hand operand is a char, as stated in the last paragraph. Even if the right hand operand was converted to an int before the assignment took place, the value represented by that int should still fit in the 8 or more bits provided by the left operand.

---

### Post by karlson on 2011-10-03
> **V for Vincent said:**
> The left hand operand can hold at least 8 bits, but to represent the right hand operator as a signed int, 12 bits are needed (and my machine actually uses 64). So you would get an implementation defined conversion. But I'm afraid I still don't see the problem if the right hand operand is a char, as stated in the last paragraph. Even if the right hand operand was converted to an int before the assignment took place, the value represented by that int should still fit in the 8 or more bits provided by the left operand.

If the right hand operand is a char then there is no conversion necessary. e.g.
```

char c = 'A';

```
If, however, the right hand side is not a char  but for example an int then the behavior of this code
```

char c = (int)65;

```
would be implementation defined according the author.  You would need to consult the C standard to see if there are any definitions with regards to conversions like this.

What author actually says is bit confusing because he is describing a case of the following:
Char cast to and int using conversion
Int cast down to a char using conversion
and then assigned to a char.
What he states is that it doesn't actually happen this way.

---

### Post by Bachstelze on 2011-10-03
> **karlson said:**
> 
[/code]
If, however, the right hand side is not a char  but for example an int then the behavior of this code
```

char c = (int)65;

```
would be implementation defined according the author.

Well, this is wrong.

> 6.3.1.3 Signed and unsigned integers

1. When a value with integer type is converted to another integer type other than _Bool, if the value can be represented by the new type, it is unchanged.

65 can be represented as a char, so the value is just carried over.

---

### Post by karlson on 2011-10-03
> **Bachstelze said:**
> Well, this is wrong.



65 can be represented as a char, so the value is just carried over.

Didn't have the standard in front of me to confirm.

---

### Post by V for Vincent on 2011-10-03
You're right, Karlson, the way the author puts it is pretty confusing. I thought what comes after the semicolon in the final paragraph was building on the scenario where a legitimate char is assigned to another. But I'm pretty confident that I get it now.

---

