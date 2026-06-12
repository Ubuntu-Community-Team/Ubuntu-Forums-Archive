---
title: "Bash Script Question - Open Multiple Text Documents based on Filter"
date: 2009-09-04
forum: Programming Talk
---

### Post by SNYP40A1 on 2009-09-04
This question is actually related to Cygwin, but it's about the Bash shell so is relevant here too.  Not really a programming question.  Here it is:

Say I have a text editor that can be launched by ./textedit.  I navigate to a directory and then open all files in the text editor which match a specific pattern.

Such as ./textedit *PATTERN*

So that all file names containing "PATTERN" will be opened.  How do I do that?

---

### Post by DaithiF on 2009-09-04
well you won't want the './' before your textedit command as the editor presumably isn't located in the directory where the documents you want to open are.  If textedit is in your path, then just
```
textedit *pattern*

```

or if its not in your path, then give the full path to the editor
/path/to/textedit *pattern*

---

### Post by Can+~ on 2009-09-04
Bash already can manage [some expressions]("http://www.tuxfiles.org/linuxhelp/wildcards.html").

```
gedit mydirectory/[a-z]*.h
```

(Open files composed by lowercase characters from a to z, and ending in ".h" in folder "mydirectory").

If you need something more fancy, you could use find and xargs, or one of the many combos I'm sure will popup after my comment.

---

