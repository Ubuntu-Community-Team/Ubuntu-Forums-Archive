---
title: "Command substitution problem with bash, sqlite3"
date: 2015-01-16
forum: Programming Talk
---

### Post by donsy on 2015-01-16
Scipt:
```

#!/bin/bash

cmd='sqlite3 test.db "select col1, col2 from table1;"'

result=$($cmd) # doesn't work

#result=$(sqlite3 test.db "select col1, col2 from table1;") # this works when uncommented

echo $result


```
When executed gives the following error:
```
sqlite3: Error: too many options: "col1,"
Use -help for a list of options.

```

However if I uncomment line 4 it works fine.

---

### Post by schragge on 2015-01-16
See [post=12519758]this post[/post] and [this answer]("http://unix.stackexchange.com/a/38441"). What you get after *$cmd* gets expanded to its value is equivalent of
```
result=$(sqlite3 test.db \"select col1, col2 from table1;\")
```
In bash, you should use an array for this to work as intended:
```

#!/bin/bash

cmd=(sqlite3 test.db 'select col1, col2 from table1;')
result=$("${cmd[@]}")

```
or use zsh instead of bash.

---

### Post by sisco311 on 2015-01-16
Why do you want to store the command in a variable? If you have to invoke it multiple times, then use a function.

---

### Post by donsy on 2015-01-16
> **schragge said:**
> See [post=12519758]this post[/post] and [this answer]("http://unix.stackexchange.com/a/38441"). What you get after *$cmd* gets expanded to its value is equivalent of
```
result=$(sqlite3 test.db \"select col1, col2 from table1;\")
```
In bash, you should use an array for this to work as intended:
```

#!/bin/bash

cmd=(sqlite3 test.db 'select col1, col2 from table1;')
result=$("${cmd[@]}")

```
or use zsh instead of bash.

@schragge: Thank you. It works.

@sisco311: That script was for illustrative purposes only, line 4 was commented.

---

### Post by sisco311 on 2015-01-16
> **donsy said:**
> @schragge: Thank you. It works.

@sisco311: That script was for illustrative purposes only, line 4 was commented.

I know. That's why I asked why do you want to store the sqlite3 command and its parameters in a variable. This seems like a strange problem to want to solve.

---

### Post by donsy on 2015-01-16
> **sisco311 said:**
> I know. That's why I asked why do you want to store the sqlite3 command and its parameters in a variable. This seems like a strange problem to want to solve.

I'm always open to suggestion. How would you do it?

---

### Post by sisco311 on 2015-01-17
> **donsy said:**
> I'm always open to suggestion. How would you do it?

Do what?

---

