---
title: "[C] conflict of 2 if-else instructions"
date: 2013-10-29
forum: Programming Talk
---

### Post by ppplayer80 on 2013-10-29
Hi,

I'm sorry if this problem was already discussed here. I don't know what to type in Google to find it.

Here is a fragment of my code:
```
if (var/900==1 || var/400==1)
    {
        var2[i] = 'C';
        i++;

        if (var/900==1)
        { 
           var2[i] = 'M';
            var = var - 900;
        }
        else 
        {
            var2[i] = 'D';
            var = var - 400;
        }

        i++;
    }
```
And I think I know why this generates problem. Parser think that "else" instruction refers to the first if, but it doesn't. As a result, if my 'var' variable doesn't match the first condition, it goes to the ' var2[i] = 'D' ' line and breaks whole program (because it should completely leave this fragment of code if it doesn't match the first condition).

I'm a new Linux user and I use Terminal's 'gcc' command to compile my programs. I also use c99 standard.

Can you please help me?

EDIT//
Problem was in an int conversion (for example 700/400 = 1)

---

### Post by spjackson on 2013-10-29
Welcome to the forums.

You are mistaken. If the expression on the first line evaluates to false, then none of the rest of the posted code is executed. You can demonstrate this either with the aid of a debugger or with printfs.

---

### Post by ppplayer80 on 2013-10-29
> **spjackson said:**
> Welcome to the forums.

You are mistaken. If the expression on the first line evaluates to false, then none of the rest of the posted code is executed. You can demonstrate this either with the aid of a debugger or with printfs.
Well, of course I will check this, but I'm 99% sure it does work as I described in a first post. Are you sure about this?
I will check this a bit later, I cannot do it right now.

Thank you for the answer though!

---

### Post by bak&#305;r on 2013-10-29
Else statement applies to the nearest if, if something does not force it to do otherwise, even if you did not use the outer paratheses. If the first condition is not true, nothing will be executed. Could you explain your problem more specifically?

---

### Post by ofnuts on 2013-10-29
See above posts... but your code is rather contrived and dangerous since you are really testing the variables twice for the same values. This should be equivalent:
```

if (var/900==1) {
        var2[i++] = 'C';
        var2[i++] = 'M';
        var = var - 900;
}
else if (var/400==1) {
        var2[i++] = 'C';
        var2[i++] = 'D';
        var = var - 400;
}
else {} /* nothing done */

```

Otherwise, google around for Roman numerals conversions...  this is such a cliché exercise...

PS : the tests var/400==1 should really be var >= 400. Normally when you want these tests to be true you have already subtracted the bigger values so there is no chance that var/400 will return 2.

---

