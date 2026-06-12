---
title: "Retaining variable info if no input"
date: 2013-02-15
forum: Programming Talk
---

### Post by cbillson on 2013-02-15
I'm wanting to have defaults to some questions in a test script so i can just press enter if no data changes - currently though it sets the variable to blank... any help on how i can stop it doing this?

In this example i want $testvar to remain as no, however it sets it blank
[INDENT]testvar=no

read -p "change a setting $testvar : " testvar

echo $testvar

[/INDENT]

---

### Post by steeldriver on 2013-02-15
Have a look at the [FONT=Courier New]${parameter-default}, ${parameter:-default}[/FONT] constructs here

[http://tldp.org/LDP/abs/html/parameter-substitution.html](http://tldp.org/LDP/abs/html/parameter-substitution.html)

---

### Post by cbillson on 2013-02-18
That worked great - thanks

---

### Post by Bucky Ball on 2013-02-18
*Thread moved to **Programming Talk**.*

---

