---
title: "How can I format the results of the &quot;who&quot; command?"
date: 2018-08-06
forum: Programming Talk
---

### Post by Paddy Landau on 2018-08-06
I need to extract some information from the "[FONT=&amp]who[/FONT]" command, specifically the username and the display variable.

Unfortunately "[FONT=lucida console]who[/FONT]" returns different results, specifically the time, depending on the locale. I read that the way to solve this is to use a fixed locale using the variable LC_TIME, but this doesn't work. The following three commands all return the same results.
```
who
LC_TIME=C who
LC_TIME=en_GB.UTF-8 who
```
This is a problem, because two users running the same command get different results, leading to programmatic problems in extracting information.

How can I get "[FONT=&amp]who[/FONT]" to display the time in a consistent format?

Alternatively, if there's another way to find every logged-in user's username and display code, that would be great!

---

### Post by Paddy Landau on 2018-08-06
I've been searching for ages, and now that I've posted the question, I've found the answer!

The solution is to use LC_ALL instead of LC_TIME.
```
LC_ALL=POSIX who
```

---

### Post by Paddy Landau on 2018-08-08
I've now discovered that "who" can be wildly inconsistent. Here are three results from three different machines.
```
paddy    tty7         Aug  7 07:27 (:0)
paddy    :1           2018-08-07 19:52 (:1)
paddy    tty7         2018-08-07 19:55 (:0)
```
I have changed to using "w", which is more consistent.

---

