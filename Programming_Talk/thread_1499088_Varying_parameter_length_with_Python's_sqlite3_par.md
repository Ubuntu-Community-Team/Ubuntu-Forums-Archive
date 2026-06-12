---
title: "Varying parameter length with Python's sqlite3 parameter substitution."
date: 2010-06-01
forum: Programming Talk
---

### Post by Spike the Dingo on 2010-06-01
This is an issue that has nearly driven me mad, and the solution is: 
A) very simple and I'm not seeing it, or 
B) going to require a lot more coding.

This involves Python's sqlite3 module and parameter substitution. I'm currently using v2.6.5, but this is an issue on anything post-v2.5.

Lets say I'm trying to do
```
curs.execute("SELECT * FROM table WHERE site NOT IN (?)", whatever)
```
By this time, 'whatever' is a tuple.
Now, this works fine if I only want "?" to be one, single thing. But, I'm ambitious, apparently. And this creates a problem when 'whatever' is greater than one value because I need more "?"s. In other words, I need this line of code to be flexible so that the user can substitute the placeholder for any number of arguments (because this is all wrapped in a cozy function). So, sometimes I need this to look like:
```
SELECT * FROM table WHERE site NOT IN ('this', 'that', 'andYourMum')
```
and other times I need it to look like:
```
SELECT * FROM table WHERE site NOT IN ('this', 'that', 'andYourMum', 'andDad', 'andSister', 'blahBlah', 'andSoOn)
```

The only realistic way to do this is create a bunch of 'if' blocks that check the length 'whatever' and adjust the number of "?"s accordingly... Please say it ain't so. I'm being stupid and have missed something obvious, right?

Thanks for your help. :KS

---

### Post by DaithiF on 2010-06-01
Hi, create the sql statement with a variable number of '?' placeholders based on the number of params, and then you just supply the params tuple as normal.
e.g.:

```
params = ('this', 'that', 'andYourMum', 'andDad', 'andSister', 'blahBlah')

curs.execute("SELECT * FROM table WHERE site NOT IN (%s)" % ','.join('?'*len(params)), params)
```

---

### Post by Spike the Dingo on 2010-06-02
Aha! I was so close, and yet, so far. Thanks, DaithiF! :-)

---

