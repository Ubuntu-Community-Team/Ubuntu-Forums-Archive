---
title: "Simple Python Question..."
date: 2011-03-07
forum: Programming Talk
---

### Post by kevin11951 on 2011-03-07
I am sure I am doing this wrong, but at the end of my script, I have this line:

```
input('\nPress enter to exit...')
```

However, when you press enter it complains that the user didn't input anything...  What is the right way to do this?  (In case you couldn't tell, I want to prompt the user to press enter before the script exits)

---

### Post by xpow on 2011-03-07
you could try 

```
raw_input('\nPlease enter to exit ...')
```

---

### Post by kevin11951 on 2011-03-07
> **xpow said:**
> you could try 

```
raw_input('\nPlease enter to exit ...')
```

That worked perfectly!  Wasn't "raw_input" deprecated in Python 3?

---

### Post by Vox754 on 2011-03-08
> **kevin11951 said:**
> That worked perfectly!  Wasn't "raw_input" deprecated in Python 3?

Are you perhaps running your program with Python 2?

Did you think of that? Eh?

---

### Post by MadCow108 on 2011-03-08
> **kevin11951 said:**
> That worked perfectly!  Wasn't "raw_input" deprecated in Python 3?

yes but it is a case easily handled by the 2to3 tool.
It replaces raw_input with input and input with eval(input())

---

