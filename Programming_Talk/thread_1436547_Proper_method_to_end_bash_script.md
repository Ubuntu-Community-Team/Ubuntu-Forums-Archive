---
title: "Proper method to end bash script"
date: 2010-03-22
forum: Programming Talk
---

### Post by cubeist on 2010-03-22
I have always ended my bash scripts with an ```
exit 0
``` but was recently told the best way is to leave it blank...ie, add nothing to the last line.

Is there a proper way to end a bash script?

---

### Post by Goveynetcom on 2010-03-23
Well, I personally leave it blank, but I don't think there is a proper way to end them, exit 0 might be a better way to end it, but then again there are many ways to do the same thing in any aspect of programing. Do what you see is comfortable if you can't find an answer.

---

### Post by falconindy on 2010-03-23
If a bash script reaches EOF, it'll exit with 0 regardless.

I personally leave it blank. Exit values are for when something goes wrong (and C).

---

### Post by diesch on 2010-03-23
No, id the script reaches EOF it will exit with the exit value of the last program that it has called.

So if you should use exit 0 or not depends on what exit value you want.

---

### Post by cubeist on 2010-03-23
So the consensus is there is no consensus! It's hard to win an argument when there is no right answer.

Thanks for your replies!

---

