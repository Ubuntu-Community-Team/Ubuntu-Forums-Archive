---
title: "python loop question"
date: 2011-08-15
forum: Programming Talk
---

### Post by b0whunter on 2011-08-15
So here i have this function in C that removes every instance of a specific character in a string:

```
void squeeze(char s1[], char c)
{
    int i, j;

    for (i = j = 0; s1[i] != '\0'; i++)
        if (s1[i] != c)
            s1[j++] = s1[i];
    s1[j] = '\0';
}

```How would I do that in python2? I really like the C for loops and I'm not sure how to go about doing the same in python2. Any help will be appreciated!

---

### Post by Bachstelze on 2011-08-16
string.translate(None, char)

---

### Post by b0whunter on 2011-08-16
> **Bachstelze said:**
> string.translate(None, char)

And to think I liked "for loops" in C... Python is quite amazing!

---

