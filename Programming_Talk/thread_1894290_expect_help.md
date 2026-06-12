---
title: "expect help"
date: 2011-12-12
forum: Programming Talk
---

### Post by Drenriza on 2011-12-12
Hi all.

I have a simple bash script. Where at some point i use a little expect scripting.
IF! i put the expect scripting which is really simple
```
/usr/bin/expect - << EndMark
spawn echo "hi"
EndMark
```
inside a if statement i get the following error
syntax error: unexpected end of file


But if i take the same code
```
/usr/bin/expect - << EndMark
spawn echo "hi"
EndMark
```
outside of the if statement, then i get no error.

I dont understand, why cant u put it inside the if statement, but i can outside.
Edit. The if statement is a very simple
```
if [ "$something" == "y" ]; then
some-bash-command
/usr/bin/expect - << EndMark
spawn echo "hi"
EndMark
fi
```

Kind regards.

---

### Post by sisco311 on 2011-12-12
Make sure that the delimiter (EndMark) is on a line by itself, in the first column (no leading or traling whitespaces).

[http://mywiki.wooledge.org/HereDocument](http://mywiki.wooledge.org/HereDocument)

---

### Post by Drenriza on 2011-12-12
> **sisco311 said:**
> Make sure that the delimiter (EndMark) is on a line by itself, in the first column (no leading or traling whitespaces).

[http://mywiki.wooledge.org/HereDocument](http://mywiki.wooledge.org/HereDocument)

Argh thats foolish with the, no leading whitespaces.
I've been trying to solve this for ages, and then the solution is so simple.

Thanks.

---

### Post by sisco311 on 2011-12-12
You are welcome!

Don't forget to mark this thread as SOLVED.

---

