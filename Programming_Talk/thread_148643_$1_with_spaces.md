---
title: "$1 with spaces"
date: 2006-03-22
forum: Programming Talk
---

### Post by lolcese on 2006-03-22
I wrote a very small script called gr with one parameter passed from bash:

grep -nri $1 *

Works well, but if the argument contains a space, the result is wrong. I tried to call using quotes gr "aaa bbb", but the space is the problem.
Any idea about what can I do?
Thanks

---

### Post by colo on 2006-03-22
You need to quote your actual argument, somewhat like the following:

```
yourscript.sh "first argument" "second argument" thirdargument fouthargument
```

---

### Post by lolcese on 2006-03-22
[quote=colo]You need to quote your actual argument, somewhat like the following:

```
yourscript.sh "first argument" "second argument" thirdargument fouthargument
```[/quote]

Thank you for your help, but doesn work, it pass only "first" in your example

---

### Post by engla on 2006-03-22
[QUOTE=lolcese]I wrote a very small script called gr with one parameter passed from bash:

grep -nri $1 *
[/QUOTE]
Quote it in the script, like so:
```
grep -nri "$1" *
```

Here is a nice link tip:
[Writing robust bash scripts]("http://www.davidpashley.com/articles/writing-robust-shell-scripts.html")

---

### Post by lolcese on 2006-03-22
I worked, but I have put 
grep -nri "$1" *
and also "aaa bbb" in the command line.
Many thanks to all

---

