---
title: "Help with UNIX"
date: 2010-04-12
forum: Programming Talk
---

### Post by quista345 on 2010-04-12
[COLOR=#231F20][FONT=Arial]Write a command, assuming your home directory, to list all files that

[/FONT][/COLOR]    [COLOR=#231F20][FONT=Arial]Start with the letters b or f.[/FONT][/COLOR]
  [COLOR=#231F20][FONT=Arial] [/FONT][/COLOR]
    [COLOR=#231F20][FONT=Arial] Start with the letters a through k.[/FONT][/COLOR]
  [COLOR=#231F20][FONT=Arial] [/FONT][/COLOR]
    [COLOR=#231F20][FONT=Arial][/FONT][/COLOR] [COLOR=#231F20][FONT=Arial]Have a capital letter anywhere in their name[/FONT][/COLOR]

---

### Post by Dayofswords on 2010-04-12
Homework?

---

### Post by lisati on 2010-04-12
Moved to "Programming talk"

This looks a bit like homework. We won't actually do homework assignments for you, but feel free to ask for ideas if you get stuck.

---

### Post by quista345 on 2010-04-12
No this is not homework, we have new training going on at work and Im just trying to grasp the information.

---

### Post by lisati on 2010-04-12
> **quista345 said:**
> No this is not homework, we have new training going on at work and Im just trying to grasp the information.

Thank you for your explanation. 

By the way, I think I saw in one of your other threads that someone has already pointed out that this is a Linux forum, not a Unix forum. You might find that there are one or two differences.

---

### Post by matthew.ball on 2010-04-12
I think he should learn about [regular expressions]("http://en.wikipedia.org/wiki/Regular_expression").

---

### Post by jpkotta on 2010-04-12
> **matthew.ball said:**
> I think he should learn about [regular expressions]("http://en.wikipedia.org/wiki/Regular_expression").

He should learn regular expressions, but [shell globs]("http://en.wikipedia.org/wiki/Glob_(programming)") are really what we want here.

How about listing all the filenames that have a vowel as their second character?
```
ls ?[aeiouAEIOU]*
```

? means any single character
[...] means any of the characters enclosed in the brackets (the vowels)
* means any number of any characters, including none.

Hopefully you can see how this works.

---

### Post by lostinxlation on 2010-04-13
It depends on which regular expression you use, but if you're going to do it with the traditional UNIX regexp, it should be something like
 
find . -name "[bfBF][a-kA-K][a-kA-K]*" -print
 
It searches the files whose names start with b, f, B or F, and following charactors in the file names are those of a to k and A to K.
 
In your case, [bf].* represnts the file name that starts b or f, [a-k].* does with those starting with a through k, .*[A-Z].*  is the file names which contains at least one upper case.

---

