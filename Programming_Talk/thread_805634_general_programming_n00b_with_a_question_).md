---
title: "general programming n00b with a question :)"
date: 2008-05-24
forum: Programming Talk
---

### Post by eragon100 on 2008-05-24
Hi all!

VERY new to programming (except for html), learning python by writing a multiple choice test for english in stani's python editor. How do I save the contents/value of a variable to a text file? I want to save the valuable name (name of the student) and the answers to the questions (all yes or no, typed in at the command line) to a text file, each variable's value starting on a new line so it is readable.

How do I do that :confused:

---

### Post by njkt on 2008-05-24
Check the documentation, the tutorial has a section titled Input Output which has the information you need.

---

### Post by eragon100 on 2008-05-24
thanx, I will check it out :)

---

### Post by Majorix on 2008-05-24
You can do that with this little snippet:
[php]file_to_edit = open("test.txt", "w") # use "a" to append and "r" for reading
file.write("put whatever you want to write here")
file.close()[/php]
It is pretty intuitive I believe.
Hope it helps, good luck.

---

### Post by rye_ on 2008-05-24
I think maybe in leet speek, you're a newb rather than a n00b?

---

### Post by smartbei on 2008-05-24
Unless I am missing something, I believe Majorix meant 'open' rather than 'file_to_edit'. A working piece of code:
```

fd = open("name_of_file_to_edit", "w") # as he says, "r" for reading and "a" for appending.
fd.write("anything")
fd.close()

```

---

### Post by Majorix on 2008-05-24
smartbei, you are correct indeed. Sorry for misleading :(

---

### Post by pmasiar on 2008-05-24
Little more advanced way to do this is to use pickle. You can create say a dictionary, 'pickle' it as a file, and then later 'unpickle' and all the keys and values are restored. Just FYI. So you don't have to parse input and laboriously restore variables and values - all happens automagically. But pickle file will not be readable (and you should not edit it).

---

### Post by smartbei on 2008-05-24
If you do want it to be readable, check out ConfigParser - it reads and writes user-editable ini files with a pretty simple API:

Code to write:
```

import ConfigParser
conf = ConfigParser.ConfigParser()
conf.add_section("General")
conf.set("General", "Whatever", 3)
conf.write(open("test.txt", "w"))

```

Code to read:
```

import ConfigParser
conf = ConfigParser.ConfigParser()
conf.read("test.txt")
value = conf.get("General", "Whatever")

```

---

