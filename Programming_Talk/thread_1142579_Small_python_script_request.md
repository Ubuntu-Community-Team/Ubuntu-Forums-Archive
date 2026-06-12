---
title: "Small python script request"
date: 2009-04-29
forum: Programming Talk
---

### Post by Free Thinker on 2009-04-29
I've only just started learning python and was wondering whether someone could help me with my first program, by writing a short script that can find and remove all punctuation, spaces, indentations, capitalisation etc from a text file and produce a new one with every word printed on an individual line in lowercase. 

This could be a nice little (I *think* it would be a short script) project for someone still learning python (but further ahead than me), while also providing me with a script to learn from and use.

---

### Post by ghostdog74 on 2009-04-29
so what have you tried?

---

### Post by grepgav on 2009-04-29
This sounds kinda like a homework assignment.

What kind of functions do you think would be useful for getting this done?

---

### Post by simeon87 on 2009-04-29
[http://ubuntuforums.org/showpost.php?p=7159208&postcount=16](http://ubuntuforums.org/showpost.php?p=7159208&postcount=16)

"I needed ..."? Are you sure it's a a goal you've set for yourself? We're not going to do homework.

---

### Post by Free Thinker on 2009-04-29
Computing wasn't even an option at my college. I'm learning this myself using thenewboston's tutorials on youtube...

This thread can be deleted.

---

### Post by grepgav on 2009-04-29
Well you could attack that a couple of ways. If you were doing it in standard c style, you could just iterate over each character and load the correct chars into a buffer.

If you want to learn about python libraries however, check out 
[http://www.python.org/doc/2.3/lib/module-string.html](http://www.python.org/doc/2.3/lib/module-string.html)

Functions such as strip and lower are a place to start, but experiment with them a little bit to see what result you can get.

---

### Post by raydeen on 2009-04-29
I'd bet use of the .split function/method along with .lower would make it criminally easy. And then just checking to see if the ascii values are between a and z would strip out the punctuation. I'm just starting to get my feet wet in Python.

Edit: Shoot. grepav beat me to it.

---

### Post by Reiger on 2009-04-29
Well last time I looked even English contains non ASCII characters. Matching punctuation is probably best done by actually matching punctuation and not trying to use a blanket match case which is bound to fail in just about every language. Much easier and reliable to just split around punctuation/whitespace.

---

### Post by raydeen on 2009-04-29
> **Reiger said:**
> Well last time I looked even English contains non ASCII characters. Matching punctuation is probably best done by actually matching punctuation and not trying to use a blanket match case which is bound to fail in just about every language. Much easier and reliable to just split around punctuation/whitespace.

Right. I just meant checking to see if the character in question was in the value range between lowercase 'a' and lowercase 'z' and then throwing it out if it wasn't. I think the OP said something about stripping out punctuation. 

I'm a noob so I might still be missing your point.

---

### Post by ibuclaw on 2009-04-29
Have a look at the regular expression page. [http://docs.python.org/library/re.html](http://docs.python.org/library/re.html)

The function you should be looking at is **re.split()**

ie:
```

import re;
mystring = "Hello, World";
re.split('\W+', mystring);

```

That should push you in the right direction.

Regards
Iain

---

