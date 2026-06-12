---
title: "mv command. - move only filed with selected word"
date: 2012-03-03
forum: New to Ubuntu
---

### Post by mferarri on 2012-03-03
Hi UbuntuForums,

i have a lots of files. i want to use the terminal to move any files containing the word "space" (disregarding the file type) into a folder that i made called space.

how do i do this?

(btw, i know that: mv *.jpg space ,will move any jpg files into the space folder)

how do i indicate code in my posts in ubuntu forums?

---

### Post by mferarri on 2012-03-03
i've found a link that might help me but i cant seem to apply this to the example that i gave above.
help anyone?

[http://linuxcommand.org/lts0050.php]("http://linuxcommand.org/lts0050.php")

---

### Post by diesch on 2012-03-03
First thing to know: Unlike in Windows in Linux the file name extension (like .jpg) is just a normal part of the file name without any general special meaning (but some programs take it as a hint).

By "*files containing the word 'space'*" I think you mean "*any number of characters follows by 'space', followed by any number of character*". Then "*any number of chacaters*" can be replaces by "***" , and so "*any number of characters follows by 'space', followed by any number of character*" becomes "**space*"*.

So
```
mv *space* space
```should do what you want.

---

### Post by JC Cheloven on 2012-03-03
> **mferarri said:**
> how do i indicate code in my posts in ubuntu forums?

When editing the post, click in the icon that looks like # at the top of the typing area.

As for your main question, diesch told you.

Cheers

---

### Post by mferarri on 2012-03-03
thanks diesh you solved my problem.:p

---

