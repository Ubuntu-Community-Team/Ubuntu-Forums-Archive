---
title: "Python: re module"
date: 2009-09-06
forum: Programming Talk
---

### Post by filifunk on 2009-09-06
A book I have says this:

'You can also denote a range of characters using the '-' character.  The pattern '[1-5]' matches any character from 1 to 5 inclusive.

And this is the code in the book:

```


In [51]: grocery_list = "Milk  2\nEggs  12"

In [60]: re.sub('[^0-5]', '*', grocery_list)
Out[60]: '******2*******12'



```

Why does it substitute text characters, intuitively I would think that it would replace any numbers that are 1,2,3,4,5...because those are the numbers [1-5] right?  Why does it take out all the text characters?

---

### Post by Mirge on 2009-09-06
> **filifunk said:**
> A book I have says this:

'You can also denote a range of characters using the '-' character.  The pattern '[1-5]' matches any character from 1 to 5 inclusive.

And this is the code in the book:

```


In [51]: grocery_list = "Milk  2\nEggs  12"

In [60]: re.sub('[^0-5]', '*', grocery_list)
Out[60]: '******2*******12'



```Why does it substitute text characters, intuitively I would think that it would replace any numbers that are 1,2,3,4,5...because those are the numbers [1-5] right?  Why does it take out all the text characters?

Using ^ inside of square brackets [] means "NOT", so you're basically saying to replace anything that's NOT 0,1,2,3,4,5 with an asterisk *.

---

### Post by filifunk on 2009-09-06
ahhh!  yes the book says this: "Lastly, follow up with a '^' after the left bracket to negate the range...I didn't understand that...you said it much more concisely =)

---

### Post by Mirge on 2009-09-06
> **filifunk said:**
> ahhh!  yes the book says this: "Lastly, follow up with a '^' after the left bracket to negate the range...I didn't understand that...you said it much more concisely =)

Happy to help.

---

