---
title: "Beginner Question about python."
date: 2008-05-19
forum: Programming Talk
---

### Post by rlameiro on 2008-05-19
Hi everyone!

I am a little question about python, I am trying to find a function that replace letters in a string, but it is hard to find. I just started to learn python, maybe I don't know where to search.

well an example:

a string called  


text = " This es a emport function"

The objective is to replace the "e" in the string for "i"

I already search the __doc__ for string and string.replace but is not what i want

Thanks in advance

---

### Post by pmasiar on 2008-05-19
yes it is. look:
[php]
>>> text = " This es a emport function"
>>> new = text.replace('e', 'i')
>>> new
' This is a import function'
>>> text
' This es a emport function'
[/php]

text was not changed - strings are immutable, changed string is returned as different object

---

### Post by rlameiro on 2008-05-19
Well pmasiar thank you very much, indeed is what i want. but is his the replace inside the string lib? I searched the doc inside the string lib, and this I think is in the standard lib. well either way I have a way to make it!!! the people in this forum are amazing!!! That's why i changed to opensource software!!!!!

---

### Post by Bichromat on 2008-05-19
This method is a builtin method for string objects, you do not need to import the 'string' module. You can list all the methods of an object with 'dir':
```

>>> dir("abc")
[..., 'replace', ...]

```

---

### Post by geirha on 2008-05-19
The builtin string object is called str, so help(str) should show you what you can do with a string.

dir(__builtins__) and help(__builtins__) will show you all the builtins.

---

