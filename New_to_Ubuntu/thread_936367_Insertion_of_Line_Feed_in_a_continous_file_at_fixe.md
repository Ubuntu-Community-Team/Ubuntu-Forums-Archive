---
title: "Insertion of Line Feed in a continous file at fixed lengths"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by jchappel on 2008-10-02
I have a file that has continous data that I need to insert Line Feeds into the data at fixed point (position 132) in the file to create fixed length lines.

So I'm looking for a way to do this and output a new file with the fixed length lines.

---

### Post by cmnorton on 2008-10-03
I suggest you become familiar with the free-bees in the bash shell.

head -c will extract by bytes. Assuming this is an ASCII file, you should be able to pull your lines out that way, and then put a 0x10 at the end.

You could also use tail or combinations of both.

bash has character substring capability.

With whatever you do, start with a test shell script whose first line is:

#!/bin/bash

and make sure to protect it chmod +x <file-name>

---

