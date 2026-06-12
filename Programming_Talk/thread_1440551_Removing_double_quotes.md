---
title: "Removing double quotes?"
date: 2010-03-27
forum: Programming Talk
---

### Post by bartre on 2010-03-27
Hi, i'm working on an assignment for school, again.
we're doing a word counting program in Java using a linked list.
in the process we're supposed to alphabetize the words when we print them out.

on to the problem, we're supposed to remove double quotes, if any, from the words when we read them in.
i've just been using a standard removeChar method up until now, but it requires the piece to be removed to be a character, and i don't know how to send double quotes (") as a character.

here is the removeChar method i've been using, the end goal is to get a string like "hello" to be simply hello, with no quotes

```

public static String removeChar(String s, char c) 
{
    String r = "";

    for (int i = 0; i < s.length(); i ++) 
    {
    	if (s.charAt(i) != c) 
            r += s.charAt(i);
    }

    return r;
}
```

---

### Post by vtnerd on 2010-03-27
Well since this is a school project I won't give you a complete answer. There are couple of ways to provide escape sequences (*hint*). Also everything stored in a computer is a number, remember that point when viewing: [http://www.asciitable.com]("http://www.asciitable.com/")

---

### Post by n0dix on 2010-03-27
Using number of the ascii plus cast can be done.

---

### Post by myrtle1908 on 2010-03-28
Better to use the String class replaceAll() method.

---

