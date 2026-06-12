---
title: "Quick SQL question"
date: 2007-12-28
forum: Programming Talk
---

### Post by LeTenken on 2007-12-28
I am not too familiar with SQL, any help will be appreciated.
Lets say I wrote a select statement that returned something like this:
[LIST]
[*] Name x y
[*]Bob 1 2
[*]Bob 3 5
[*]Bob 10 10
[*] Frank 1 3
[*] Chris 2 2
[*] Chris 2 3
[/LIST]
how would i narrow my query down to only one instance of Bob and Chris where x+y is the largest total?
i hope to get a new query that will make this output:
[LIST]
[*] Name x y
[*]Bob 10 10
[*] Frank 1 3
[*] Chris 2 3
[/LIST]

please let me know if i should include any additional information.

---

### Post by LeTenken on 2007-12-28
nevermind, used DISTINCTROW

---

### Post by anbumanij on 2007-12-29
Hi goody,
[B]
select name,max(x),max(y) from name group by name;[/B]

Use this query this might very well solve your problem... 





Keep going ........... :guitar:

---

