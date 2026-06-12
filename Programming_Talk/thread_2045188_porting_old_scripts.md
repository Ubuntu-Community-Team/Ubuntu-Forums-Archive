---
title: "porting old scripts"
date: 2012-08-20
forum: Programming Talk
---

### Post by conradin on 2012-08-20
Hi all,
I am porting some old scripts, and one thing that I have seen is a colon
at the start of the script. From what I've read, the colon is a style of comment, but may have some other implications... of which I'm not sure about.

In some of the scripts, the first line is:
CODE]: '@(#)scriptname.sh 18.5'[/CODE]

What I want to know is the importance of @(#) in the comment? What is this nonsense?

---

### Post by steeldriver on 2012-08-20
looks like part of an SCCS Id / what string ?

---

### Post by conradin on 2012-08-21
I think you're right! Though i had never previously heard of an SCCS ID.
: '@(#)lsetacq.sh 18.5' 
is that what you mean by the string?

---

