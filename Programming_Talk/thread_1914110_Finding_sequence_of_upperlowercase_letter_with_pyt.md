---
title: "Finding sequence of upper/lowercase letter with python"
date: 2012-01-23
forum: Programming Talk
---

### Post by Neoncamouflage on 2012-01-23
So I'm currently working on the Python Challenges, and just got to level 3. In this level I, as far as I can tell at least, need to locate a lowercase letter surrounded by three uppercase letters on either side, in a massive text wall. Example: pEORndfRjsd>>EHDhKHO<<fslWdnjfDOndWnBuro

There's several of these, and I need a way to strip them all out of ~1,000 lines of text. I've searched google, I've searched the python docs, I've even looked at the python challenge forums, I cannot figure out what I need to do this. I can't seem to get my search term right so that it brings up what module/command I'm looking for, so I can't even attempt this right now. Anybody know what it is I'm needing?

---

### Post by CoffeeRain on 2012-01-23
This code is untested, but I would assume it is something like...
```

letters=*your letters here*
newletters=''
for char in letters:
  if char.islower():
    newletters=newletters+char

print newletters

```

---

### Post by Neoncamouflage on 2012-01-23
That takes out all the lowercase letters and gives them to me, right? Unfortunately, I only need the lowercase letters surrounded by three uppercase on both sides. Such as in my example, I need only 'h', and not the 'pndfjsdfsldnjfndnuro' it would also give me. Unfortunately I'm not familiar with any method to accomplish this.

---

### Post by Bachstelze on 2012-01-23
Regular expressions.

[http://docs.python.org/library/re.html](http://docs.python.org/library/re.html)

---

### Post by cgroza on 2012-01-23
You could loop through the string using a counter.
Then at each iteration, you could check the letters on the sides.

---

### Post by r-senior on 2012-01-23
Could you make a sliding buffer? Basically a queue of 7 characters? As you encounter a new character, you queue it and, if the queue was full, drop the last one off the end. It's then a simple matter to test the queue at each iteration to see if position 3 (counting from 0) is lower case and all the others are uppercase.

[http://docs.python.org/library/collections.html#collections.deque](http://docs.python.org/library/collections.html#collections.deque)

---

### Post by Neoncamouflage on 2012-01-23
Haven't had a chance at trying this yet, but the queue idea sounds really good. Thanks a lot for the link, if I can get it working, it sounds like the best plan.

Thank you cgroza for your idea, even though I've no idea how to implement it XD, and thanks Bach for the link, not sure what those are but I'll be sure and check it out as well.

---

### Post by Toz on 2012-01-23
Be careful and re-read the question. Its not a pattern of 7 characters that you are looking for.

---

### Post by Neoncamouflage on 2012-01-24
> **Toz said:**
> Be careful and re-read the question. Its not a pattern of 7 characters that you are looking for.

Well....I won't lie, that's not terribly helpful. XD

I suppose they're not designed as riddles to be easy, thanks for telling me I'm on the wrong track.

---

### Post by Toz on 2012-01-24
@Bachstelze is right, you need to use regular expressions.

At the risk of solving the problem for you, consider this:

XXXXxXXXX != XXXxXXX

(Read the question carefully)

---

### Post by Neoncamouflage on 2012-01-24
Thanks mate, I realized what I was thinking wrong about it as I read through the documentation on regular expressions. I gotta say, this module seems incredibly useful. Glad I found it.

---

### Post by simeon87 on 2012-01-24
> **Bachstelze said:**
> Regular expressions.

[http://docs.python.org/library/re.html](http://docs.python.org/library/re.html)

+1. Easiest way to solve this.

---

