---
title: "Recursively list all files in array - python"
date: 2011-10-26
forum: Programming Talk
---

### Post by MG&amp;TL on 2011-10-26
Hi-I'm writing a program in python- I need to recursively list all files (but not directories) in a directory.

I'd like to have them in an array, and be able to feed said array to a function like so:

```

myfunc(var[x])

```
Any ideas/tutorials/help/links are very much appreciated.

PS-How do you get a return value from nautilus-as in a file-chooser dialog?

---

### Post by 11jmb on 2011-10-26
I'm not 100% sure what you're asking

Do you want to iterate through your list of files, and if that file is a directory, recurse into that directory? or do you want to just recursively run through a single list?

If its option one, we'll talk, but if its option 2, I must ask: Why?

---

### Post by ofnuts on 2011-10-26
> **MG&TL said:**
> Hi-I'm writing a program in python- I need to recursively list all files (but not directories) in a directory.

I'd like to have them in an array, and be able to feed said array to a function like so:

```

myfunc(var[x])

```Any ideas/tutorials/help/links are very much appreciated.

PS-How do you get a return value from nautilus-as in a file-chooser dialog?
See:

[LIST]
[*] os.listdir(*path*)
[*] os.walk(*top*[, *topdown=True*[, *onerror=None*[, *followlinks=False*]]])
[/LIST]
 
Doc: [http://docs.python.org/library/os.html](http://docs.python.org/library/os.html)

---

### Post by MG&amp;TL on 2011-10-26
Thank you, both of you- ofnuts' documentation is kinda useful-11jmb, I want to recursively list all files (*tree*-style) in a directory.

I have found a solution here: [http://www.linuxforums.org/forum/miscellaneous/46693-how-shred-entire-directory-tree.html]("http://www.linuxforums.org/forum/miscellaneous/46693-how-shred-entire-directory-tree.html")

But it's not exactly what I want. I'll try working with the os library and see how far I get.

Any clues on nautilus?

---

