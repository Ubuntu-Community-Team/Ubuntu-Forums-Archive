---
title: "Bash command set giving unexpected results"
date: 2010-01-12
forum: Programming Talk
---

### Post by jamesisin on 2010-01-12
I am studying bash.

I understand that set is supposed to print (to screen) a list of variables and their values (similar to env which shows only exported variables).

If I run set on my Mac I see the expected results.  Running env on the Mac or my Ubuntu machines (8.10 and 9.10) also returns the expected results.

However, running set on my Ubuntu machines yields what appears to be a script of some sort.

Can someone tell me what's going on?

---

### Post by DaithiF on 2010-01-12
set also outputs any bash functions which have been defined.  these will be displayed after the evironment variables.  So maybe thats what you're seeing.  if you do:
```
set | less
```
it will page the results for you, you will (probably) see environment variables first, then at the at end any bash functions that have been defined.

---

### Post by jamesisin on 2010-01-12
You are correct.

Man, that's a lot of bash functions.  I trust the book I'm reading will discuss enough to help me understand what that's all about.

---

### Post by sisco311 on 2010-01-12
> **jamesisin said:**
> You are correct.

Man, that's a lot of bash functions.  I trust the book I'm reading will discuss enough to help me understand what that's all about.

Most of them are bash tab completion functions (/etc/bash_completion & /etc/bash_completion.d/*).

---

### Post by jamesisin on 2010-01-13
Well, that's a little confusing.  I thought bash had tab-completion built in.  What extra help does it need that would require so much additional code?

---

### Post by sisco311 on 2010-01-13
> **jamesisin said:**
> Well, that's a little confusing.  I thought bash had tab-completion built in.  What extra help does it need that would require so much additional code?

Custom completion options for different commands. i.e. username completion for chown

[http://www.debian-administration.org/article/An_introduction_to_bash_completion_part_1](http://www.debian-administration.org/article/An_introduction_to_bash_completion_part_1)

---

### Post by jamesisin on 2010-01-14
Thanks for that.  Looks like good reading.

---

### Post by lavinog on 2010-01-14
Imagemagik creates a bunch of them too.

---

