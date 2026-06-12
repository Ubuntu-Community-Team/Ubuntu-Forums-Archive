---
title: "First Time Script"
date: 2009-03-30
forum: Programming Talk
---

### Post by AndyGibo on 2009-03-30
Hi people,

I'm being very ambitious here. I am basically trying to turn the instructions from here([http://ubuntuforums.org/showthread.php?p=4963842]("http://ubuntuforums.org/showthread.php?p=4963842")) into a script.

Problems
[LIST=1]
[*]1) This is the first time I've EVER played around with scripts and I dont fully understand the language!
[*]2) I have discovered the command ***sed*** but one line I need to change (e.g. Enable=false) appears more than once and I'm not sure how to change just the one line I need to.
[/LIST]

Other than that I've stumbled around and managed to sort the rest out.

So...   any ideas anyone?!?!

---

### Post by AndyGibo on 2009-03-31
Bump Bump Bump

---

### Post by lakersforce on 2009-03-31
If you have a specific question, fire away.

---

### Post by AndyGibo on 2009-03-31
[*]2) I have discovered the command ***sed*** but one line I need to change (e.g. Enable=false) appears more than once and I'm not sure how to change just the one line I need to.


Any ideas on how to alter just the one line and not every line that matches??  Is it possible?

---

### Post by bapoumba on 2009-03-31
Moved to PT.

---

### Post by AndyGibo on 2009-03-31
Bump again

---

### Post by andrew.46 on 2009-03-31
Hi AndyGibo,

> **AndyGibo said:**
> 2) I have discovered the command ***sed*** but one line I need to change (e.g. Enable=false) appears more than once and I'm not sure how to change just the one line I need to.

Can you give the actual text? sed can certainly do this but you need to provide an exact copy of the text you wish to alter.

All the best,

Andrew

---

### Post by Arndt on 2009-03-31
> **AndyGibo said:**
> [*]2) I have discovered the command ***sed*** but one line I need to change (e.g. Enable=false) appears more than once and I'm not sure how to change just the one line I need to.


Any ideas on how to alter just the one line and not every line that matches??  Is it possible?

I'm guessing a little, maybe you want something like this:

```
sed '/\[xdmcp\]/,/^[\t ]*$/s/Enable=false/Enable=true/'

```
With the following input:

```
[xdmcp]
Enable=false

[xdmcp2]
Enable=false
```

My 'sed' command replaces the first Enabled=false, but not the second. What it does literally is replace Enabled=false with Enabled=true within a text block that starts with [xdmcp] and ends with a completely blank line (end of file works too).

With all the quoting and regexp removed, it does /first line/,/last line/s/line to be changed/changed line/

The s is the substitute command in 'sed'.

---

### Post by AndyGibo on 2009-04-01
Woo hoo!!

Had to split the total script into two halves but other than that it works!!  Now I really should learn how that line works!

Thanks loads!

---

