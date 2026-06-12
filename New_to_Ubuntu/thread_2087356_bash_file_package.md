---
title: "bash file package"
date: 2012-11-22
forum: New to Ubuntu
---

### Post by sanjibarpi on 2012-11-22
if i want to run a fortran programme initiated by a .bash file. what package  I need to install

---

### Post by oldos2er on 2012-11-23
Post moved to its own thread. It's a little easier for others to help you when you confine each thread to a single problem or question.

---

### Post by 2F4U on 2012-11-23
If the .bash file is a shell script, you need no additonal software to run it. If you are in the same folder as the file, try to execute in a terminal

./file.bash

The .bash file should have the execute bit set. If it is not set, execute

chmod u+x file.bash

---

