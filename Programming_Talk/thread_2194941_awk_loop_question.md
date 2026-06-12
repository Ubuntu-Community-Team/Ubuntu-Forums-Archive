---
title: "awk loop question"
date: 2013-12-21
forum: Programming Talk
---

### Post by sha1sum on 2013-12-21
Hello guys, I need help with this awk command.

In the book sed & awk by O'reilly press, 1997, it says that the syntax of the for command is like this:

```
for ( set; test; increment)
action
```

So I tried this

```
me@computer:~$ echo "Alice Bob Charlie Daniel Erica" | awk '{ for ( i = 1; i <= NF-2 ; i++ ); print $i }'
Daniel

```

What I want to have the awk command print all the fields except the last two. But instead it only prints the penultimate field.

If I simplify it even more, I see this behavior:

```
me@computer:~$  echo "Alice Bob Charlie Daniel Erica" | awk '{ for ( i = 1; i < 4 ; i++ ); print $i }'
Daniel

```
I've did some testing and what it appears to do is the following: It works through the loop and it prints the first value of i for which the test fails to give true, after which it exits. 

Why does it behave like that?

---

### Post by ofnuts on 2013-12-21
Remove the ";" after the for()... I assume that's like in C, the for  is followed by a (simple or compound) statement. If you put a semi-colon, this is an empty statement, so the loop is on that statement, and the print is executed when the loop exits.

As a matter of style, instead of testing for "<= NF-2",  test for  "<NF-1" ( the loop on all elements is typically written by testing for "<NF")

---

### Post by sha1sum on 2013-12-21
Thanks! Good explanation.

---

