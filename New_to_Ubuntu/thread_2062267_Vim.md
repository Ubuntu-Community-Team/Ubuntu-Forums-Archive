---
title: "Vim"
date: 2012-09-24
forum: New to Ubuntu
---

### Post by JohnsonGamingTV on 2012-09-24
I started my programming in the terminal using vim, how do I control where it saves to? i.e a different folder?

---

### Post by agillator on 2012-09-24
In command mode use the command :w <filename> (see [http://www.tuxfiles.org/linuxhelp/vimcheat.html](http://www.tuxfiles.org/linuxhelp/vimcheat.html)).

---

### Post by JohnsonGamingTV on 2012-09-24
thats changing the name of the program, i want to change the directory.

---

### Post by Stovey on 2012-09-24
Heeeeey! I would use ":w" followed by the absolute filepath & name. ie ~/sandbox/textfile.txt insetad of just textfile.txt.

Also, have a look at the "vi for smarties" tutorial in my sig.  

[http://www.jerrywang.net/vi/](http://www.jerrywang.net/vi/)

---

### Post by JohnsonGamingTV on 2012-09-24
says "Python/game.py" E212: Can't open file for writing

---

### Post by Stovey on 2012-09-24
Whoooooaaa!  "Python/game.py" is not a valid absolute filepath.  <Fonz pulls comb from back pocket>.

Python must reside in some other directory.  In the terminal from which you started editing with vim, type "pwd" to find the full absolute filepath of where you current file exists.  pwd means "print working directory".

You might need to make a Python directory with "mkdir Python".

Also, maybe look at the BASH tutorial link in my sig.  Heeeey!  <Fonz combs hair>.

---

### Post by JohnsonGamingTV on 2012-09-24
it worked, thanks :)

---

### Post by Stovey on 2012-09-24
Heeeeey!

---

