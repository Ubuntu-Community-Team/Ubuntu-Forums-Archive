---
title: "batch files in linux?"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by melrokz on 2008-08-05
Hi! I'm Melvin from India.
How to create and save batch files that run in terminal just like windows .bat files that run in cmd?

---

### Post by estyles on 2008-08-05
Basically, you can put your commands into a text file, save it, then use ```
chmod u+x *filename*
``` to make it executable.  It's customary to put "#! /bin/bash" as the first line in the file, but it's funny - I have no idea whether that's just a comment, or if it tells the shell something useful.  I'm assuming because of the '!' character, it probably actually does something, so I tend to attach it to the beginning of any shell scripts.

---

### Post by Oldsoldier2003 on 2008-08-05
> **estyles said:**
> Basically, you can put your commands into a text file, save it, then use ```
chmod u+x *filename*
``` to make it executable.  It's customary to put "#! /bin/bash" as the first line in the file, but it's funny - I have no idea whether that's just a comment, or if it tells the shell something useful.  I'm assuming because of the '!' character, it probably actually does something, so I tend to attach it to the beginning of any shell scripts.

The shebang  ( #! ) tells Linux that it is a bash script to be interpreted (run) by /bin/bash

---

### Post by Roger Mudd on 2008-08-05
I believe you're looking for something like BASH scripting. You may want to check out [this guide]("http://tldp.org/LDP/abs/html/").
I think any scripting language will work, however, so you may want to look into Python as well. You can find a good guide for that [here]("http://www.greenteapress.com/thinkpython/").

---

