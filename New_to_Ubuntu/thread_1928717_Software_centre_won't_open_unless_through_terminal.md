---
title: "Software centre won't open unless through terminal."
date: 2012-02-20
forum: New to Ubuntu
---

### Post by rollcast on 2012-02-20
I can't open the software centre through the icon on the left bar of the screen or from the dash menu.

However if I use the following code in terminal it will open.

```
sudo software-center --enable-lp
```Thanks AL

---

### Post by rjarvis2010 on 2012-02-23
Same for me. I can run it under 'sudo', but not as my user. Running 11.10 (installed as upgrade from 11.04).

---

### Post by rjarvis2010 on 2012-02-23
Fixed after I removed '$HOME/.cache/software-center'.

(Found the solution while researching another problem, which this also solved: 'http://ubuntuforums.org/showthread.php?p=11636422#18'.)

---

### Post by cortman on 2012-02-23
> **rjarvis2010 said:**
> Fixed after I removed '$HOME/.cache/software-center'.

(Found the solution while researching another problem, which this also solved: 'http://ubuntuforums.org/showthread.php?p=11636422#18'.)

Thank you for taking the initiative to solve it yourself. A more detailed explanation will help the OP solve it as well.

And just a hint- if you need to run a GUI program with root permissions, it's smarter to use

```
gksu program_name
```

rather than sudo. Sudo should be only for CLI programs.

---

### Post by mcduck on 2012-02-23
> **cortman said:**
> Thank you for taking the initiative to solve it yourself. A more detailed explanation will help the OP solve it as well.

And just a hint- if you need to run a GUI program with root permissions, it's smarter to use

```
gksu program_name
```

rather than sudo. Sudo should be only for CLI programs.

...furthermore, you don't actually need to use sudo/gksudo at all with the Software Center. It's made to be executed as a normal user, and uses PolicyKit to gain the elevated privileges when needed.

---

