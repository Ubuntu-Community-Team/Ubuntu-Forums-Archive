---
title: "[Python] Do I have any chance of making it in a repository?"
date: 2010-08-24
forum: Programming Talk
---

### Post by Miyavix3 on 2010-08-24
[http://code.google.com/p/tabremover/](http://code.google.com/p/tabremover/)

I thought it was a pretty good idea at the time, but after making it I'm having second thoughts.

Basically it replaces tabs in source code (or any text document) with spaces.

Also, should I bother posting this on freshmeat. Should I have done that first?

---

### Post by myrtle1908 on 2010-08-25
I haven't looked at your tool but find and replace is a basic function of almost any text editor and this same functionality exists in the shell as well via sed or awk etc.

---

### Post by DaithiF on 2010-08-25
also most people writing python code will have their editor configured to expand tabs to spaces automatically.

---

### Post by worksofcraft on 2010-08-25
I've been learning Python and I much prefer to have tabs instead of spaces because I can change the tab width whatever way I feel like but once expanded I'm stuck with it :shock: So a tool to convert spaces back into tabs would be awesome!

Now I thought perhaps it was just me being a noob, but then I notice loads of tutorials and examples on the web all using tabs and others here in the forums prefer them too!

I'm currently wanting to learn how to create packages and there is a sticky about making .deb file and a whole forum devoted to MOTU packaging effort. So I'm using a project of my very own to experiment and learn how to package things properly.

Have you had a go at that with your application? You might want to check out this thread: [http://ubuntuforums.org/showthread.php?t=599473](http://ubuntuforums.org/showthread.php?t=599473)

Good luck and let us know how it goes :)

---

### Post by spjackson on 2010-08-25
> **Miyavix3 said:**
> Basically it replaces tabs in source code (or any text document) with spaces.

Also, should I bother posting this on freshmeat. Should I have done that first?

> **worksofcraft said:**
> I've been learning Python and I much prefer to have tabs instead of spaces because I can change the tab width whatever way I feel like but once expanded I'm stuck with it  So a tool to convert spaces back into tabs would be awesome!
As has been said, many editors have these facilities, but there are also *expand* and *unexpand* which are in the coreutils package, and have been around since the dawn of time.
```

$ man expand
$ man unexpand

```

---

### Post by kgarbutt on 2010-08-25
Hi Miyavix3,

The fact that you realized that you could do something better by writing a program, and then actually writing one is great. Most people only dream of doing what you did. Don't worry if your program never makes it into the repositories just keeping doing it. Great job on your python program. Keep up the great work, and call yourself a programmer.

Ken

---

### Post by KdotJ on 2010-08-25
> **kgarbutt said:**
> Hi Miyavix3,

The fact that you realized that you could do something better by writing a program, and then actually writing one is great. Most people only dream of doing what you did. Don't worry if your program never makes it into the repositories just keeping doing it. Great job on your python program. Keep up the great work, and call yourself a programmer.

Ken

+1
Everyone starts somewhere and the fact that you have created a program that you are going to use is great. Keep at it

---

### Post by Miyavix3 on 2010-08-25
Thank you everyone for your kind remarks.

You see, I layed the basic foundation out and put it into practice but I figure this use of regular expressions and a simple python script can be super effective for anything needed to be replaced at one time in a file.

For now, I only have tabs implemented but it's just as easy to add options ```
./tabreplacer.py --replace="\t" --with="    "
``` 
or what have you.

I feel that a program should start small, with small goals, and then expand onto higher grounds with the help of the open source community.

Also, this was my first try using optparse and I really like it.

---

### Post by KdotJ on 2010-08-25
> **Miyavix3 said:**
> 
I feel that a program should start small, with small goals, and then expand onto higher grounds...

Quite true in my opinion. I have a program that I built for myself a year a go, and I use it daily. Since then, I have continuously been developing it and adding more functionality to it as I think of new features it needs.. Now the program is much much bigger and better than the initial one

---

### Post by Miyavix3 on 2010-08-25
I'm also working on a program that takes files off of your iPod and renames them so they're not random letters and sorts them accordingly. 

Would anyone be interested in helping me out with this?

---

### Post by juancarlospaco on 2010-08-25
no

---

