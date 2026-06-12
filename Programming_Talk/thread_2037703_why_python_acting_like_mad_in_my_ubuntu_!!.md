---
title: "why python acting like mad in my ubuntu ?!!"
date: 2012-08-05
forum: Programming Talk
---

### Post by prismctg on 2012-08-05
when i type this ```
os.getenv('USERNAME')
``` it returns None ; so it does not return my username ; i m using ubuntu 12.04

---

### Post by greenpeace on 2012-08-05
> **prismctg said:**
> when i type this ```
os.getenv('USERNAME')
``` it returns None ; so it does not return my username ; i m using ubuntu 12.04

if you run this in the terminal on your box, what does it give you?

```
echo $USERNAME
```

---

### Post by raja.genupula on 2012-08-05
[http://stackoverflow.com/questions/842059/is-there-a-portable-way-to-get-the-current-username-in-python](http://stackoverflow.com/questions/842059/is-there-a-portable-way-to-get-the-current-username-in-python)

---

### Post by trent.josephsen on 2012-08-05
USERNAME isn't exported by default, so new programs can't see it. Don't use getenv for this, though.

```
>>> from getpass import getuser
>>> getuser()
'trent'
```

---

### Post by prismctg on 2012-08-05
> **greenpeace said:**
> if you run this in the terminal on your box, what does it give you?

```
echo $USERNAME
```

it returns nothing ; just blank !!!

---

### Post by prismctg on 2012-08-05
> **trent.josephsen said:**
> USERNAME isn't exported by default, so new programs can't see it. Don't use getenv for this, though.

```
>>> from getpass import getuser
>>> getuser()
'trent'
```

thnx :)

---

### Post by raja.genupula on 2012-08-05
actually command is  echo $USER

```
raja@badfox:~$ echo $USER
raja

```

Remember : you have to type as USER not user .

---

### Post by trent.josephsen on 2012-08-05
echo $USERNAME works for me (zsh) so I didn't bother to rethink the naming of the variable, but raja.genupula is right, $USER is the variable that you should use for this purpose.

---

