---
title: "Using ls incrementally?"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by 655 on 2008-06-19
How can I print the contents of a directory incrementally, similar to the dir /p command in DOS, rather than all at once?  I would like ls or a similar command to print partial contents, with more visible upon pressing a key.

---

### Post by Eclipse. on 2008-06-19
Tab is exactly the button your looking for.;)

---

### Post by 655 on 2008-06-19
Well, yes, but is there a way to print the contents incrementally with a switch applied?  
Say I wanted to to use the -l switch but see those results incrementally.
It seems that he use of tab precedes the complete expression and is used to just see the raw contents.

---

### Post by flowevd on 2008-06-19
try

ls | more

you can use | more after any command

---

### Post by 655 on 2008-06-19
That does the trick.  Thank you.

---

### Post by tukuyomi on 2008-06-19
I think ```
~$ ls | more
``` is what you're searching for. [SPACE] allows you to scroll the page.
Try ```
~$ ls | less
``` and you'll be able to move forward/backward with the arrows; press h to get more help ;)
If you get a "less: Command not found", just ```
~$ sudo apt-get install less
```
[More Information]: command1 | command 2 allows you to pass the output of command1 (ls) to command 2 (less); hope it will help ;)

flowevd was quicker ^^

---

### Post by 655 on 2008-06-19
Yeah, but you expanded on flowevd's input :D

This is good to know.  I always use less to plainly read text files, but I can't believe it never dawned on me to use it with pipes.  Brilliant!  The keyboard functionality is great.  Thanks to both.

---

### Post by Dedoimedo on 2008-06-19
Hello,

Here's another nice trick:

ls -la > dir-listing-file

Then you can view the file in your spare time, drinking a cup of roasted Ubuntu beans.

Dedoimedo

---

### Post by flowevd on 2008-06-22
> **tukuyomi said:**
> I think ```
~$ ls | more
``` is what you're searching for. [SPACE] allows you to scroll the page.
Try ```
~$ ls | less
``` and you'll be able to move forward/backward with the arrows; press h to get more help ;)
If you get a "less: Command not found", just ```
~$ sudo apt-get install less
```
[More Information]: command1 | command 2 allows you to pass the output of command1 (ls) to command 2 (less); hope it will help ;)

flowevd was quicker ^^
i was.. but you just told me something more!

---

