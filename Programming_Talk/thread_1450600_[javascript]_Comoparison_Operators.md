---
title: "[javascript] Comoparison Operators"
date: 2010-04-09
forum: Programming Talk
---

### Post by lovinglinux on 2010-04-09
I was wondering what is the correct way of declaring a negative condition in a  function: **[COLOR="Red"]!=[/COLOR]** or **[COLOR="Red"]!==[/COLOR]**? I have been using **[COLOR="Red"]!==[/COLOR]** on my code without issues, but I have seen codes out there with **[COLOR="Red"]!=[/COLOR]** and [W3Schools shows only **[COLOR="Red"]!=[/COLOR]**](http://www.w3schools.com/JS/js_comparisons.asp).

Would be any problems by using **[COLOR="Red"]!==[/COLOR]**?

---

### Post by Compyx on 2010-04-09
Use !== when you need to compare types as well. For example:
```

0 != ""

```
would return false (types do not get checked so "" is converted to 0), which is equal to 0, but:
```

0 !== ""

```
would return true, since 0 and an empty string do not have the same type.

In PHP, which also uses the 'nonidentity' operator (!==), you have a function strpos(), which returns the first occurence of a substring in a string. It returns false when no substring was found.

Now, if you used != to check whether the substring was present in the string, you would get a false positive for a substring at position 0, since 0 translates to false when using !=, so you'd have a bug in your code. Using !== checks types as well and would have spotted the difference between 0 and false and would have avoided the bug.


I hope this clears things up for you, if not, feel free to ask for more details and/or examples.

---

### Post by lovinglinux on 2010-04-09
> **Compyx said:**
> Use !== when you need to compare types as well. For example:
```

0 != ""

```
would return false (types do not get checked so "" is converted to 0), which is equal to 0, but:
```

0 !== ""

```
would return true, since 0 and an empty string do not have the same type.

In PHP, which also uses the 'nonidentity' operator (!==), you have a function strpos(), which returns the first occurence of a substring in a string. It returns false when no substring was found.

Now, if you used != to check whether the substring was present in the string, you would get a false positive for a substring at position 0, since 0 translates to false when using !=, so you'd have a bug in your code. Using !== checks types as well and would have spotted the difference between 0 and false and would have avoided the bug.


I hope this clears things up for you, if not, feel free to ask for more details and/or examples.

Thanks a lot. That clears up everything.

---

