---
title: "universalindentgui seg faults"
date: 2009-02-23
forum: Programming Talk
---

### Post by Dooley on 2009-02-23
Has anyone tried the fantastic sounding univeralindentgui?

I'm using 8.10 and installed it from the repos, but seg faults after it creates a few config directories.

I also tried the sourceforge deb and had no luck with that either.

Anyone have a work-around or solution, would be much appreciated.

Dooley

---

### Post by Dooley on 2009-02-26
Does anyone have any idea or has gotten this working?

My terrible looking code would be much appreciated. :p

---

### Post by Vadi on 2009-02-26
Yes, 8.10's version crashes. There is some other one (maybe in 9.04) that works, I don't remember.

The I found the "indent" program better suited anyway as it could be used within Geany as a keybinding. No need to go to an external app.

---

### Post by Dooley on 2009-03-02
Any chance there's an alternative of indent for php scripts?

---

### Post by Vadi on 2009-03-02
Try this *random python script of the day*: [http://indentphp.googlecode.com/svn/trunk/indentphp.g](http://indentphp.googlecode.com/svn/trunk/indentphp.g)

---

### Post by Dooley on 2009-03-02
Cheers, 
That might do the job. Also I discovered this neat little trick on the interwebs for vim users.

```
:source $VIMRUNTIME/indent/whateverlanguage.vim
```
So for php it's 
```
:source $VIMRUNTIME/indent/php.vim
```
then press
```
gg=G
``` 
to auto-indent the whole file or use visual mode to highlight what you want tabbed then press =

---

