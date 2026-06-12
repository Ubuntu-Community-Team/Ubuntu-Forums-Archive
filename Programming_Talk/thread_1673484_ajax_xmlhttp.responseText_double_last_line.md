---
title: "ajax xmlhttp.responseText double last line"
date: 2011-01-22
forum: Programming Talk
---

### Post by kuifje09 on 2011-01-22
Shure, the answer is on the web somewhere but cant find it.

This is my problem:

From a webpage I do a request :
document.getElementById("Prev").innerHTML=xmlhttp.responseText;

The result is displayed in a textarea with the id="Prev".     I get all the information requested.
But the result in the text area always shows the last line double.

So, 1 line info becomes 2 lines,
If 10 lines info.. it becomes 11 lines,
How can I solve this, what do I mis.


>>> Should have used shell_exec .

---

### Post by kuifje09 on 2011-01-22
I found the php script already shows the wrong contend for reply.

<?php
print(system('ls ../upload'));
?>

This already gives a double last output line...

aap.jpg
noot.jpg
noot.jpg
 
instead of 

aap.jpg
noot.jpg

---

### Post by kuifje09 on 2011-01-22
Okay, I read the PHP manual again, and tried some other functions.

passthru()    does is perfect.

System() gives a line too much , the last line.

exec ()  gives only the last line.

Solved for me, but not shure if I understand the difference between the commands.

---

