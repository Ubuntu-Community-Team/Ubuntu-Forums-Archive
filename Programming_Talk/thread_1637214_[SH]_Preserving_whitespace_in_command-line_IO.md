---
title: "[SH] Preserving whitespace in command-line I/O"
date: 2010-12-04
forum: Programming Talk
---

### Post by skytreader on 2010-12-04
I created a little script that allows me to make that huge jump to where most of my work resides with a single command. I added some I/O to facilitate jumps straight to specific folder in my work folder.

```
echo "Where to in Cyberstudio my friend?"
read loc
cd ../../../
cd media/58BC7C55BC7C2F9C/Users/Andrei/Documents/Cyberstudio/
cd $loc
```

Problem is, I don't know how to preserve whitespaces in my input. So, for instance:

```
Where to in Cyberstudio my friend?
Computer Science
```

It only reads "Computer" (sans quotes) and returns an error. I've tried every input variation I can think of such as Computer\ Science, "Computer Science", 'Computer Science', "Computer\ Science" (as is)---all to no avail.

So, how do I make it jump to "Computer Science" (sans quotes)?

(Yep. I'm jumping to a Windows partition since I've already had a significant amount of (school) code written before I tried Ubuntu).

---

### Post by roccivic on 2010-12-04
try:

```
echo "Where to in Cyberstudio my friend?"
read loc
cd "/media/58BC7C55BC7C2F9C/Users/Andrei/Documents/Cyberstudio/$loc"
```

---

### Post by skytreader on 2010-12-04
Thanks roccivic!

---

### Post by Vox754 on 2010-12-04
> **roccivic said:**
> try:

```
echo "Where to in Cyberstudio my friend?"
read loc
cd "/media/58BC7C55BC7C2F9C/Users/Andrei/Documents/Cyberstudio/$loc"
```

The important part is double-quoting the variable.

```

cd $loc     #  cd Computer Science, two arguments

cd "$loc"   #  cd "Computer Science", one argument

```

In general, you should always double-quote variables.

---

