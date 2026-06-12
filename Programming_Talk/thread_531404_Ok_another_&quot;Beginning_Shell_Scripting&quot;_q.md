---
title: "Ok another &quot;Beginning Shell Scripting&quot; question"
date: 2007-08-21
forum: Programming Talk
---

### Post by kast on 2007-08-21
Ok so i'm at the end of another chapter :) and stuck on a Exercise

Exercise - Write a program called **unsuffix ** that removes the characters given as the second argument ($2) from the end of the name of the file given as the first argument ($1). So

**unsuffix memo1.sv .sv **

Should rename memo1.sv to memo1. be sure that the characters are removed from the end,so

**unsuffix test1test test **

should result in test1test being renamed to test1. (Hint: use sed and command substitution.)

Ok so i have my Exercise and i write this 

########################
########################

   ** file="$1"**

    **   suff="$2"**

         ** unsuff=$( echo $file | sed '/$suff/d')**     # [I]my command 
substitution
[/I]
       **echo $unsuff**

########################
########################
         
 Obviously this isn't correct, it just  echo's back the first argument whether its the test1test example or one i create on my own.

When i look at it  is seems ok, but then i realized how is sed going to know where to take test ($2) from, both arguments have test in them, whether its test1test or test. it states to use sed and command substitution so I'm going by that when trying to figure this out.

                        Thanks in advance!

(Exercise taken from "Unix Shell Programming: Third Edition"
Stephen G. Kochan
Patrick Wood

---

### Post by sacherjj on 2007-08-21
Do you have to use sed?

Seems like this would be easiest with using bash string functions:

```
echo ${file%"$suff"}
```

Removes first occurrence of $suff from right side of $file.

---

### Post by kast on 2007-08-21
The way the book is written it takes you threw the very basic commands first so i think they like you to use what you have learned up to that point. If there is one thing i have noticed learning scripting is there is always a few different ways to do everything.

So I'm trying to just use what the book says i can to get the job done.

---

### Post by sacherjj on 2007-08-21
I'm not too good with sed, but I think you need something in the form: s/[get suff]//

The last slash creates the "nothing" that it is replacing the suff that it finds.

---

### Post by kast on 2007-08-21
I will mess with that, ill post back in a while. 

            thanks!

---

### Post by Mr. C. on 2007-08-21
The problem occurs because you have your sed expression in single quotes, where variable interpolation does not occur:

```
'/$suff/d'
```

should be

```
"/$suff/d"
```

Prove this to yourself with **echo '/$suff/d'** and **echo "/$suff/d"**.

Yet, this still is not correct.   The d flag in sed deletes the line that matched the pattern, and that is not what you want.  You want to substitute text instead:

```
"s/$suff//"
```

Now, while that will seem to work for you, it too isn't correct.  See what happens when you try:

```
unsuffix memo1-sv .sv 
```

Until you know how to escape metacharacters reliably, use **basename** or internal shell pattern matching.

Your book was written long ago, and primarily for ksh if I recall correctly.  Bash has evolved a long way since then, and has become the defacto standard.

Here are some additional lessons that I wrote to supplement your text book:

[http://cis68b1.mikecappella.com](http://cis68b1.mikecappella.com)

MrC

---

### Post by Chaotic Thought on 2007-08-21
If you're allowed to use **sed**, can you just use **basename**? It already does what the problem describes. For example, **basename index.html .html** will return simply "index"

---

### Post by Mr. C. on 2007-08-21
> **Chaotic Thought said:**
> If you're allowed to use **sed**, can you just use **basename**? It already does what the problem describes. For example, **basename index.html .html** will return simply "index"

The goal is to learn about scripting by exploration; it is not merely to have an answer.

MrC

---

### Post by kast on 2007-08-21
I would like to thank everyone that replied, and helped me on this

 Mr C thanks for the reply that did the trick, even if it was an outdated one. I will take a look at your  lessons. 

The book I'm reading while in its third edition,  is going over  things that are most likely out dated.  I seen a few good reviews on this book as a beginners guide, do you think learning some older stuff is going to hurt rather then help in the long run?

I have "Mastering Shell Scripting" but it kinda expected me to already know certain things going into it.

                     Again thanks everyone! If I didn't shave my head I would have pulled all my hair with this one. :-)

---

### Post by Mr. C. on 2007-08-21
The basics in sh, ksh, and bash are all the same, so the lessons from the book are fine.  You may notice in the syllabus on the site I gave that i used the same edition.

Enjoy the learning!
MrC

---

