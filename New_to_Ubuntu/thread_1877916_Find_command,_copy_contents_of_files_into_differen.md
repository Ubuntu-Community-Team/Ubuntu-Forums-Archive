---
title: "Find command, copy contents of files into different file"
date: 2011-11-08
forum: New to Ubuntu
---

### Post by skyline131313 on 2011-11-08
I'm trying to do something like this:

```

find . -exec cat {} > ~/files/{} \;

```

the only problem is that it puts all the contents into a file named '{}'. I need to use cat so that the contents of the files gets put into text and than put somewhere else.

---

### Post by papibe on 2011-11-08
A few pointers:

[LIST]
[*]'cat' a file into another, is equivalent to copy it (or using cp). It does not translate a binary file into text.
[*]The > redirection is ending your find command. The code after that is fixed and not part of the find.
[*]By default 'find' also reports directories. You can specify just files using the option '-type f'.
[/LIST]
If I understand what you are trying to do, this should work:
```
find . -type f -exec cp '{}' ~/files/  \;
```
Does that help?
Regards.

---

### Post by skyline131313 on 2011-11-08
It is not a binary file and I've attempted copying the files like you've suggested. Something weird is going on and I need to output the contents to an external source (buffer in this case) and than put the buffer into a new file. I've tested it with one file and cat does work, for some reason cp isn't.

---

### Post by papibe on 2011-11-09
I don't understand that, but if you want to use cat there's a way. Instead of executing a command, try executing bash with a string parameter as the instructions you want to execute:
```
find . -type f -exec bash -c 'cat "$1" > ~/files/"${1##*/}"'  _  '{}'  \;

```
${1##*/} is just like using the command basename ('find' returns the files with its path relative to where you start the find, so the redirection won't be able to create the path).

Tell us if that works for you.
Regards.

---

### Post by skyline131313 on 2011-11-09
Yes it worked thank you.

---

### Post by papibe on 2011-11-09
:D Glad is working for you! Please mark the thread [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") when you have the chance.

Regards.

---

