---
title: "shell script BASIC: multi line commentary"
date: 2007-04-06
forum: Programming Talk
---

### Post by eldersoares on 2007-04-06
thats it: how to make multi line commentaries with bash script?
thanx

---

### Post by WW on 2007-04-06
What are "multi line commentaries"?

---

### Post by slimdog360 on 2007-04-06
I assume he is looking for the /*  */ equivalent for bash. Which I wouldn't have a clue about since I know zero bash scripting.

---

### Post by nguyenniit1911 on 2007-04-06
I've known this way:

> 
: <<text
Enter comments here.
text
...scripts

"text" may be any text but top and down are same.

Hope helping you!

---

### Post by Jucato on 2007-04-07
I don't think there's a way to make multi-line comments in BASH. You have to put # at the beginning of each comment line.

---

### Post by -Rick- on 2007-04-07
If you use a KDE editor such as Kate or KDevelop you can easily comment multiple lines by pressing ctrl+d and uncommenting by pressing ctrl+shift+d. With bash scripts it will add a '#' at the beginning of every line.

---

