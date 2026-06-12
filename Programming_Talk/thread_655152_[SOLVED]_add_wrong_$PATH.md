---
title: "[SOLVED] add wrong $PATH"
date: 2008-01-01
forum: Programming Talk
---

### Post by donyfrosman on 2008-01-01
after i finished with my first shell scripts i want to make it run where ever directory where i work in so i add PATH with 
```
 export PATH=$PATH:directory 
```
but directory that i have added is wrong 
**can i delete that path and how to do that ?**

---

### Post by meindian523 on 2008-01-01
you can set path using 

echo $PATH='the correct path'

---

### Post by geirha on 2008-01-01
Did you type that in a terminal window? if so, it will only be set in that terminal window, and all programs spawned from it. Close the terminal window and open a new one, and the path is back to what it was before ...

---

### Post by donyfrosman on 2008-01-01
Thanks geirha that back again

---

