---
title: "run cron job now"
date: 2021-02-13
forum: New to Ubuntu
---

### Post by rburkartjo on 2021-02-13
looked on google but could not find answer
lets say i have a bunch of scheduled cron jobs and i want to run one of them now
example  30 11 14 * */home/ray/test
is there a way 
tks

---

### Post by TheFu on 2021-02-13
/home/ray/test

---

### Post by rburkartjo on 2021-02-13
fu tks that was simple. lots of web sites said could not be done. that is why i asked here

---

### Post by TheFu on 2021-02-13
Glad it helped. I considered my answer a little snarky.

There are many caveats for it working like which crontab file? There are at least 3 different locations and formats for crontabs. 

The question probably led others to think of ways that cron commands could be used to solve it. Leading questions can lead to bad or no answers.  I originally was thinking to use '**at**' or parse the **crontab -l** output with **sed** or **perl** or **nawk** to run commands.  Decided to offer a snarky answer and wait for clarification.  ;)

---

### Post by Impavidus on 2021-02-14
Note that when you run your command from command line, it will run in a different environment than when you let cron run it.

---

### Post by rburkartjo on 2021-02-14
yup imp noticed that tks

---

