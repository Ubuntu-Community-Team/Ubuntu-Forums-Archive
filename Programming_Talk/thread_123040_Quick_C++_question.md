---
title: "Quick C++ question"
date: 2006-01-29
forum: Programming Talk
---

### Post by Mykas0 on 2006-01-29
when using "getline", how can I set the delimiters?

Is it *getline (file_here, delimiter)* ?

For example, for a single word, would it be getline (file.txt, " ") ?

---

### Post by stuporglue on 2006-01-29
The C++ IO getline? 

If that's the case, which is what I'm guessing, visit [http://www.cppreference.com/cppio/getline.html](http://www.cppreference.com/cppio/getline.html) . cppreference.com is my first stop for basic c++ syntax questions. 

So, I think it'd be something like:

file.getline(dest_buffer,buffer_size,delimiter);

where the variables are of the appropriate types.

---

### Post by Mykas0 on 2006-01-29
That was exactly what I wanted to know. Thanks.

---

