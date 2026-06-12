---
title: "Python Question on Dictionaries and Classes"
date: 2010-07-27
forum: Programming Talk
---

### Post by xaegis on 2010-07-27
Hello all! I am having trouble removing and manipulating keys and enumerators I put into my dictionary files(for use other places in the program). Do I have to iterate over them and if so how? I'm still a little fuzzy on how it could help or what the code would look like. I also am assuming that the process is the same as it would be if I were trying to do the same thing from a class I create.


```

character = {'Inventory':{},'strength':10 , 'dexterity':10 , 'iq':10 ,'name':'Bingo'}

Name2 = character[name]


``` 

Why doesn't this work for me?

This is not a homework assignment it is my own personal project, so feel free to help. :)

thanks in advance,

-e

---

### Post by -grubby on 2010-07-27
.

---

### Post by schauerlich on 2010-07-27
The issue is that you're trying to access by a nonexistant variable name, when you want to access it with a string.

```
# wrong
character[name]

# right
character['name']
```

Also, from what I can see, you'd be much better off implementing a Character class than passing around dictionaries.

---

### Post by xaegis on 2010-07-27
Ooops, lol thanks a lot that was killing me!

:D

---

