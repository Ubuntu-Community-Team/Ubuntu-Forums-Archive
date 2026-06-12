---
title: "About indentation"
date: 2007-04-13
forum: Programming Talk
---

### Post by janfsd on 2007-04-13
Hi, the other day I was trying to use Indent so it will format some code in a particular style I want, so it will look like this:

```
function1 () {
  dostuff
  do more stuff
  }
```

This is called Banner Style (taken from wikipedia). Well the problem is in the first bracket, it should appear on the same line of the function declaration. By default indent will format it like this:
```
function1 () 
{
  dostuff
  do more stuff
  }
```

Is there a way within the options of indent to make it look like the 1st example? I've read the documentation and so far, I didn't find anything that would help me, there was just something like this but for conditions and for structures (-br and -brs).

Please, can someone help me?

---

### Post by phossal on 2007-04-13
Your editor is placing the opening bracket on a new line? What editor are you using?

---

### Post by janfsd on 2007-04-13
I use gedit, I was using "Indent" for formatting the files.

---

