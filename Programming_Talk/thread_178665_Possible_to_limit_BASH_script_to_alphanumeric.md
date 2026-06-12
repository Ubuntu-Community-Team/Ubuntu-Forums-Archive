---
title: "Possible to limit BASH script to alphanumeric?"
date: 2006-05-18
forum: Programming Talk
---

### Post by pablored on 2006-05-18
If this isn't possible i'm probably going to have to learn Python or something... very quickly :/

My program is 'finished'... but because I can't figure out how to restrict the possible input for my 'read -sn 1 VARNAME' inputting strange combinations of ALT+CHAR and other buttons can produce bizarre results.  

In python could this be different?  I am assuming it is down to my inputrc/bashrc right now.  


Thought I was nearly done

Paul

---

### Post by pablored on 2006-05-18
Will a restrictive case statement be good enough?

I have been thinking about this all backwards I think.

---

### Post by unbuntu on 2006-05-18
[QUOTE=pablored]If this isn't possible i'm probably going to have to learn Python or something... very quickly :/

My program is 'finished'... but because I can't figure out how to restrict the possible input for my 'read -sn 1 VARNAME' inputting strange combinations of ALT+CHAR and other buttons can produce bizarre results.  

In python could this be different?  I am assuming it is down to my inputrc/bashrc right now.  


Thought I was nearly done

Paul[/QUOTE]

In python, there's a function ord(x) which takes in a char and outputs its ordinal (integer value)  Look in ASCII table, and figure out what values you want to include and put them in a case-like statement.

---

### Post by IYY on 2006-05-21
I think you could run your input stream through sed and filter it so that only alphanumeric characters get through.

---

