---
title: "Easy i'm Sure; not for me though :-("
date: 2007-08-18
forum: Programming Talk
---

### Post by kast on 2007-08-18
Ok so I have Shell Programming book and at the end of every chapter there are exercises to help reinforce what you have learned up to that point. 

    So I usually pull my hair for a bit, but figure it out in the end, but I have one question for some reason I just get my head around!

  
  "Write a program call **suffix** the renames a file by adding the characters given as the second argument to the end of the name of the file given as the first argument. So 

* $* **./suffix memo1 .sv **

 should rename **memo1** to **memo1.sv**
 
so it would be Argument one = $1 and two $2 used in a little one-two lines script, that i can freaking get.

                          Thanks in advance!

---

### Post by cwaldbieser on 2007-08-18
> **kast said:**
> Ok so I have Shell Programming book and at the end of every chapter there are exercises to help reinforce what you have learned up to that point. 

    So I usually pull my hair for a bit, but figure it out in the end, but I have one question for some reason I just get my head around!

  
  "Write a program call **suffix** the renames a file by adding the characters given as the second argument to the end of the name of the file given as the first argument. So 

* $* **./suffix memo1 .sv **

 should rename **memo1** to **memo1.sv**
 
so it would be Argument one = $1 and two $2 used in a little one-two lines script, that i can freaking get.

                          Thanks in advance!
Does this give you an idea?
```

$ NAME=hello
$ SUFFIX=.txt
$ echo "$NAME$SUFFIX"

```

---

### Post by kast on 2007-08-18
Thank you! that was exactly what i needed, i have been struggling on this, and of course its something simple as three lines.

   thanks again!

---

