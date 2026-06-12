---
title: "command 'grep' question:  in what files the string exists?"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by adhg on 2008-06-12
I have a folder with 1000 files. I would like to know in which file I can find the string "the fox brown is here" 

using GREP (or other command) how can I loop throu all files and get the list of files that the sentence is there.

thank you

---

### Post by Vivaldi Gloria on 2008-06-12
cd to the folder and

```
grep "the fox brown is here" *
```

---

### Post by Cypher on 2008-06-12
Vivaldi's command will only search for the files in the current directory and not any subdirectories. To traverse the sub-dirs as well..you'd do
```

find . -type f -exec grep "fox brown is here" {} \;

```
or
```

find . -type f | xargs grep "fox brown is here"

```
I find the second command easier to remember, I tend to forget the exact syntax for the "-exec" argument..

---

### Post by erginemr on 2008-06-12
According to this man page:
[http://unixhelp.ed.ac.uk/CGI/man-cgi?grep](http://unixhelp.ed.ac.uk/CGI/man-cgi?grep)

"grep -r" should work recursively. I cannot check this as I am away from my Ubuntu, @Cypher, could you please do this for me?

---

### Post by sdennie on 2008-06-12
If you are just looking for a listing of the files in a single directory that contain that string (case insensitive):

```

grep -li "the quick brown fox" *

```

---

### Post by Vivaldi Gloria on 2008-06-12
> **erginemr said:**
> According to this man page:
[http://unixhelp.ed.ac.uk/CGI/man-cgi?grep](http://unixhelp.ed.ac.uk/CGI/man-cgi?grep)

"grep -r" should work recursively. I cannot check this as I am away from my Ubuntu, @Cypher, could you please do this for me?

Yes, it works.

---

### Post by Cypher on 2008-06-12
> **erginemr said:**
> According to this man page:
[http://unixhelp.ed.ac.uk/CGI/man-cgi?grep](http://unixhelp.ed.ac.uk/CGI/man-cgi?grep)

"grep -r" should work recursively. I cannot check this as I am away from my Ubuntu, @Cypher, could you please do this for me?

Yup, that works..but I believe (someone correct me if I'm wrong) find is faster at, well, finding the files..:)

So having grep look inside just a single file but get the best of both worlds..

---

### Post by sdennie on 2008-06-12
Actually, in this case, it looks like "grep -r" is about 10x faster than the equivalent find -exec grep.  I'm surprised too.

```

time find . -type f -exec grep "not going to be found" '{}' \;

real	0m4.145s
user	0m2.081s
sys	0m1.916s

```

```

time grep -r "not going to be found" *

real	0m0.549s
user	0m0.195s
sys	0m0.352s

```

I made sure the directory structure I was in was cached before getting the results by doing the first find twice (first one was 13 seconds).  I also made sure they got the same results on a string that was actually going to be found.

---

### Post by Cypher on 2008-06-12
Very curoious indeed..so I guess I've found a new way of doing my recursive greps now..:)

---

### Post by erginemr on 2008-06-12
Interesting outcome. I guess this may be attributed to the fact that find & grep have to work together here, that is; one has to finish its job before the other kicks in.

---

### Post by adhg on 2008-06-12
yes yes yes....thank you so much, I used this code:

grep -r "fox" * 

and it works just fine.

THANK YOU!

---

