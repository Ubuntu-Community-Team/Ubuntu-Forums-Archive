---
title: "Can I write this program using the shell?"
date: 2010-02-28
forum: Programming Talk
---

### Post by bradley002 on 2010-02-28
I know exactly what I would like a program to do. I would like it to read two text files; one would be a list of words (listed vertically one-by-one), and the other would be a novel-like document. I would like to write a shell program that can:

1. Read a word in document A.
2. Search for that word in Document B.
3. Paste the entire line that word occurs in plus 2 lines above and 2 lines below into doc C.
4. Move to the next word in doc A.
5. Search doc B for it
6. Paste the context in which it occurs below  the last entry in doc C.
7. Repeat steps 4-6 1,000 times.

Are there any steps in there that are not doable with shell commands? It seems pretty basic but I want to make sure before I spend unnecessary time learning how to do it. And, I appreciate any pertinent tips. ;) Thanks.

---

### Post by kaibob on 2010-02-28
The following is the basic framework of a shell script that will do what you want. You can enhance it in various ways. I don't understand where the "1,000 times" in your step 7 applies, unless file_a contains 1,000 words. 

```
#!/bin/bash

while read word ; do
   grep "$word" -B 2 -A 2 file_b >> file_c
done < file_a
```

---

### Post by falconindy on 2010-02-28
> **kaibob said:**
> The following is the basic framework of a shell script that will do what you want. You can enhance it in various ways. I don't understand where the "1,000 times" in your step 7 applies, unless file_a contains 1,000 words. 

```
#!/bin/bash

while read word ; do
   grep "$word" -B 2 -A 2 file_b >> file_c
done < file_a
```

You can combine the -A and -B flags with -C (context).

---

### Post by bradley002 on 2010-02-28
Haha, that was amazing! I can't believe such a small program did that. Thanks guys. I need to learn the shell better---what I want to learn is shell *scripts*, yea?

---

### Post by Goveynetcom on 2010-03-01
> **bradley002 said:**
> Haha, that was amazing! I can't believe such a small program did that. Thanks guys. I need to learn the shell better---what I want to learn is shell *scripts*, yea?

Well what the code that was given was a bash script as dictated by the ***#!/bin/bash ***line. I definitely don't know a lot about shell scripts, but I believe bash scripts aren't as powerful but are useful for doing small tasks or some simple large ones. They're really easy to learn, if you used Windows, think of them as more advanced batch files...

---

### Post by nvteighen on 2010-03-01
There is a constraint for this. Your files have to be ASCII text files, nothing else.

If you plan to manipulate ODF, PDF, DOC, whatever, you'll need to use a general programming language that supports an API to do it... (or write your own library, but I wouldn't do it).

---

### Post by bradley002 on 2010-03-07
This program is working well. But is there a way to modify it so that it also prints the search term adjacent to the result (and only if it found the term), so I know what it found?

---

### Post by matchett808 on 2010-03-07
bash has been my starting point....I have used it for everything from fan and cpu control to web crawlers....

....I have 'just' moved to ruby....and I must say bash is the best way to start and if you put alot of effort into the programmes you can end up with something that works VERY well.....

EDIT: standard disclaimer applies....I haven't 'even' started a software development course as of yet.....

---

### Post by kaibob on 2010-03-07
> **bradley002 said:**
> This program is working well. But is there a way to modify it so that it also prints the search term adjacent to the result (and only if it found the term), so I know what it found?

This should do what you want. 

```
#!/bin/bash

while read word ; do
   match=$(grep "$word" -C 2 file_b)
   if [ "$match" ] ; then
      echo "SEARCH TERM: ${word}" >> file_c
      echo -e "$match\n" >> file_c
   fi
done < file_a
```

---

### Post by bradley002 on 2010-03-08
Thanks again.

---

