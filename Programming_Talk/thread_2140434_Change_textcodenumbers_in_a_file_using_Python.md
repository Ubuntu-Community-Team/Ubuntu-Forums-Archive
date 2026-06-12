---
title: "Change text/code/numbers in a file using Python"
date: 2013-04-29
forum: Programming Talk
---

### Post by sudo san on 2013-04-29
Hi, I am using python 3.2.3 and also a beginner in python programming.

I would like to know how to go about changing words (or a string of words/numbers) in a file to something else.
I can do this in bash
For example:
```
sed -i 's/text_in_file/new_text/g' 'path_to_file'
```

I know that there is some way to do this but I don't want to use os.system as a substitute.

Any ideas?

Thanks in advance.

---

### Post by ofnuts on 2013-04-29
[LIST]
[*]read the file line by line (see open() built-in, and then "for line in file")
[*]for simple editing, use the replace() method on strings, for more complex things, see the "re" module for regexps.
[*]write output to another file.
[*]optional: when done and if everything went OK, erase the original file and rename output file to original file name
[/LIST]

---

### Post by sudo san on 2013-04-30
Ok, thanks. I will try later today.

---

### Post by sudo san on 2013-04-30
Sorry, but can you please explain a little further please as I cannot find anything in the python documentation about replace().

---

### Post by Bodsda on 2013-04-30
> **sudo san said:**
> Sorry, but can you please explain a little further please as I cannot find anything in the python documentation about replace().

It's a string method
[http://docs.python.org/2/library/stdtypes.html#string-methods](http://docs.python.org/2/library/stdtypes.html#string-methods)

```

line = "This is foo"
line.replace("foo", "bar")

```

---

