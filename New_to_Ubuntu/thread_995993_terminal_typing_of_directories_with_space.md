---
title: "terminal: typing of directories with space"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by melrokz on 2008-11-28
Suppose I have to cd to this directory: /Documents/My Docz
the o/p will be:
directory not found: My
directory not found: Docz
How will I do it?

---

### Post by Tony Flury on 2008-11-28
try 
```

cd /Documents/My \Docz

```

---

### Post by Kai-vana on 2008-11-28
try cd /Documents/"My Docz"

---

### Post by x1a4 on 2008-11-28
> **Tony Flury said:**
> try 
```

cd /Documents/My \Docz

```

The backslash should be before the space:
/Documents/My\ Docz

---

### Post by theozzlives on 2008-11-28
> **Tony Flury said:**
> try 
```

cd /Documents/My \Docz

```

That don't work, I typed :
```
cd /Download/CD-DVD \Images
```
and it said invalid directory CD-DVD

---

### Post by theozzlives on 2008-11-28
> **x1a4 said:**
> The backslash should be before the space:
/Documents/My\ Docz

you're right that worked

---

### Post by sdennie on 2008-11-28
Tab completion is also smart about spaces.  You may be able to type "My" and then hit tab to get the right name.

---

