---
title: "terminal result searching"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by GumboLinux on 2008-10-27
Is it possible to either to push like ctrl + f to browse the results of a command or is there a command that can find a string that the terminal found with last command. I mean there are like 500 lines of code how am I supposed to find one?

---

### Post by PmDematagoda on 2008-10-27
You could pipe the output of one command to something like grep which you can then use to search for a certain word.

So the command you would use would be:-
```
command-to-take-output-from | grep word-to-find
```

---

### Post by mcduck on 2008-10-27
Both of the things you asked for are possible.. :)

First, you can pipe the output of the command to another program that allows you to read it easily. For example you can run "ls -l | less" to pipe the output of "ls -l" to "less" which allows you to scroll the output up and down.

If know what you are looking for, you can also pipe the output to "grep" to search for lines that contain some word (actually grep can do a lot more than just simple word searches, read "man grep" for more info). Running "ls -l | grep searchword" would only output the lines that contain the word "searchword"

---

### Post by SanskritFritz on 2008-10-27
also, you can redirect the output into a file:
```
command-to-take-output-from > result.txt
``` and then open the file in your favorite editor and search.

---

### Post by reg4c on 2008-10-27
And to append to an already existing file with some content use TWO > instead of ONE.
Someone, please correct me if I am wrong.

Ow, and BTW what does 'grep' stand for? I mean, no one can count how many times they grepped a command, but what does it mean?

---

### Post by SanskritFritz on 2008-10-27
> **reg4c said:**
> Ow, and BTW what does 'grep' stand for? I mean, no one can count how many times they grepped a command, but what does it mean?[http://en.wikipedia.org/wiki/Grep](http://en.wikipedia.org/wiki/Grep)

---

