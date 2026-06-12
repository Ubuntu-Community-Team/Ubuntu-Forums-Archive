---
title: "[SOLVED] Getting a path to the file in bash"
date: 2007-10-05
forum: Programming Talk
---

### Post by MiCovran on 2007-10-05
I'm new to bash scripting, but I find it very handy when dealing with simple tasks like calling several programs to process a file.

So I'm writing a script that takes one file as an argument. It will be much simpler to write this script if it "cd"s to the same directory as the files. However, I suck at googling and I just can't find a simple way to extract "foo/temp/" from "foo/temp/file".
I can remove the path simply by using "basename" command, but I don't know how to remove the filename.

Any help?
Thanks.

---

### Post by olejorgen on 2007-10-05
dirname

---

### Post by MiCovran on 2007-10-05
Thank you very much. Works perfectly.

---

