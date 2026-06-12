---
title: "auto-format sourcecode in scite and/or commandline"
date: 2011-08-14
forum: Programming Talk
---

### Post by Pille456 on 2011-08-14
Hi!

Just a little question: Currently I'm using scite as my main editor (for nearly everything, but mostly C++ and Java code) and I would like to know, if there is a auto-format feature. 
Often when I copy/paste some example code or when I do major changes in my sourcode, I have to manually indent and correct everything, which is just annoying. In this case I do not only want to have a correct indention, but also the same "bracket-style" and so on.
E.g.
```

if (10 == 20) 
{
std::out << "hi" << std :: endl;
}
```should be
```
if (10 == 20) {
    std :: cout << "hi" << std :: endl;
}
```As far as I know, astyle should do the trick, so I installed it and tried it, but nothing happend. Everything runs fine without any error, but there are not changes in the file/sourcecode.
Do I have to set some more parameters for this option?
Or is there maybe another (command line) tool for solving this problem?


Greetings
Pille

---

