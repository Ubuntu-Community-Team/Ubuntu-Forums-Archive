---
title: "Grep help"
date: 2006-01-01
forum: Programming Talk
---

### Post by DaMasta on 2006-01-01
Writing a shell script. Need some grep help.
I wanted to see if had I an ices stream running. I ran **ps -ef | grep ices**. It found the ices stream as well as something with the word **services** in it. What can I do to only get the ices stream?

---

### Post by kabus on 2006-01-01
Try grep -w to match only whole words.

---

### Post by ape on 2006-01-01
try `ps -ef | grep -E "\bices\b"`

---

### Post by DaMasta on 2006-01-01
Awesome guys, thanks.

---

