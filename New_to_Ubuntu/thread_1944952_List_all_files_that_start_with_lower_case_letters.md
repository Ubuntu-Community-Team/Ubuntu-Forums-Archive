---
title: "List all files that start with lower case letters"
date: 2012-03-22
forum: New to Ubuntu
---

### Post by Kungal on 2012-03-22
Hi 

I know this seems like a very basic question. However, when I type in 

```
ls [a-z]*
```

I get a list of all files that start with upper and lower case letters. 

Is this normal? Can someone tell me how to get a list of just files starting with lower case letters??

Thanks

---

### Post by viipu on 2012-03-22
You could try 
```

find [path] -name '[a-z]*'
```

(Or navigate to the directory you want to search first and leave [path] empty, obviously)
Watch out though you're not searching any huge directory, command might take ages to run if you are.

You can add all sorts of conditions on what you want to display about the files, have a look at [https://help.ubuntu.com/community/find](https://help.ubuntu.com/community/find)

Hope that helps.

---

### Post by The Cog on 2012-03-22
In **man bash**, I find this explanation:
> [...]  Matches  any one of the enclosed characters.  A pair of characters separated by a hyphen denotes a range expression; any character that sorts between those two characters, inclusive, using the current locale's collating sequence and character set, is matched.
I guess that the sorting sequence would go AbBcC...z so that pretty-much all filenames would match. Only a* and Z* would fail to match.

Try this:
```
LC_COLLATE=C
ls [a-z]*
```
and use ```
LC_COLLATE=
``` to restore the normal setting.

---

### Post by papibe on 2012-03-22
Alternatively to The Cog's solution, you can also use the character classes:
```
ls [[:lower:]]*
```
Regards.

---

### Post by The Cog on 2012-03-23
Ah, thank you. That's better. 
Reading the man page, I tried "ls [:lower:]*" and it didn't work. It was not obvious to me that I needed to use nested brackets.

---

### Post by Kungal on 2012-03-23
Thanks, 

The [[:lower:]] command works. It's weird, because there are so many explanations on the internet saying that including the term [a-z] will return only lower case letters. 

That point about the order being aAbB... is useful

Thanks

---

