---
title: "git question"
date: 2009-01-02
forum: Programming Talk
---

### Post by christoforever on 2009-01-02
just a quick question if anyone knows off the top of their heads. I'm using git in a java program and want to return as a String the current working branch. using git branch lists all branches with the working branch having a star infront of it. So i've tried using git grep but cant seem to return the line... I thought maybe something like     git grep "*" branch  but that just returns the next line. So if anyone has any ideas that would be cool.

Thanks in advance,

Christopher Dancy

---

### Post by christoforever on 2009-01-02
I did solve it this way, however I wanted it to be cross platform seeing as how some version of git is working on windows and the pipe operator I dont believe works on windows. I could use java's regular expression to pull out the line but I was wondering if there was a simple way in git to do it.

Solved: Unix Style

git branch | grep "*"

---

### Post by christoforever on 2009-01-02
sorry I posted in wrong spot in wrong tab.

---

### Post by christoforever on 2009-01-02
I did solve it this way, however I wanted it to be cross platform seeing as how some version of git is working on windows and the pipe operator I dont believe works on windows. I could use java's regular expression to pull out the line but I was wondering if there was a simple way in git to do it.

Solved: Unix Style

git branch | grep "*"

---

### Post by overdrank on 2009-01-02
> **christoforever said:**
> sorry I posted in wrong spot in wrong tab.

Hi and you can just use the report button and asked it to be moved :)

---

