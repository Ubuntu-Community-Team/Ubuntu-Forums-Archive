---
title: "Python Syntax Error"
date: 2010-06-19
forum: Programming Talk
---

### Post by jeffymarts on 2010-06-19
First off I'm going to apologize for making a post with a dumb question, secondly I'll also apologize for taking up your time. Ok, but here's the problem I'm encountering. When I try to issue a print command in Python I get an error message which states "SyntaxError: invalid syntax". Here is an example.

```
>>> the_world_is_flat = 1
>>> if the_world_is_flat:
	print "Be careful not to fall off!"
	
SyntaxError: invalid syntax
```

Thank you for your time.

---

### Post by trent.josephsen on 2010-06-19
Are you using Python 3?  **print** is a function, not a statement, in Python 3.

```
print("Be careful not to fall off!")
```

---

### Post by jeffymarts on 2010-06-19
I am using Python 3. Thanks for the insight.

---

