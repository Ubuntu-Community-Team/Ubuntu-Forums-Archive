---
title: "Aliasing error"
date: 2012-10-08
forum: New to Ubuntu
---

### Post by imadeitmyself on 2012-10-08
I have an executable of Foldit and want to alias it. I moved it to /opt/Foldit and edited my ~/.bash_aliases file to include the line 
```
alias foldit='/opt/Foldit/Foldit'
```and ran
```
source ~/.bashrc
```as I have done many times before for aliasing other programs. However, while "./Foldit" and "foldit" both run perfectly when I'm in its directory, running "foldit" from anywhere else produces the following error:
```
Cannot open local version file: version-binary.txt.
Foldit Error: The game has previously not started up correctly.
If this problem persists, please install the latest version.
Foldit Error: Could not load library: cmp-binary-00000000000000000000000000000000/game_library.so: cannot open shared object file: No such file or directory.
```Does anyone know why this would happen, or what I could do to fix it? It seems very strange to me.

---

### Post by Cheesemill on 2012-10-08
It looks like Foldit expects you to be in it's directory when running the executable.
Have you tried:
```
alias foldit='cd /opt/Foldit && ./Foldit'
```

---

### Post by imadeitmyself on 2012-10-08
Hey, thanks! I didn't know that could be done. I stuck in a "&& cd -" at the end too, to bring me back to my working directory when it's done.

---

