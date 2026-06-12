---
title: "How can I run matlab directly in terminal?"
date: 2011-07-24
forum: Packaging and Compiling Programs
---

### Post by JackyChao on 2011-07-24
[SIZE=1]When it is in the folder ~/matlab64/bin/, I type the executive file "matlab" in teminal, but it shows[/SIZE][SIZE=2][COLOR=Red][SIZE=1] [/SIZE]"exec: 1: /home/villa/Documents/matlab64/bin/glnxa64/MATLAB: Permission denied"[/COLOR][/SIZE][COLOR=Black][SIZE=1]. I don't konw what I should do.[/SIZE][/COLOR]
[SIZE=1]Anyway, I have set the PATH up in ~/.profile, but when I type matlab, it desn't work ether. 
Please help me. Thanks a lot
[/SIZE]

---

### Post by MadCow108 on 2011-07-25
you probably don't have executable permission on the MATLAB file.
add it with:
```
chmod u+x /home/villa/Documents/matlab64/bin/glnxa64/MATLAB
```

---

