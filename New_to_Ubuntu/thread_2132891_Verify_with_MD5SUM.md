---
title: "Verify with MD5SUM"
date: 2013-04-06
forum: New to Ubuntu
---

### Post by L Campbell on 2013-04-06
I have downloaded the 12.04.2 .iso file but I am not sure what I am doing wrong here.

Your help will be appreciated.

TIA



limeylew@limeylew-P9852A-ABA-753N:~$ cd ~/Downloads
limeylew@limeylew-P9852A-ABA-753N:~/Downloads$ md5sum ubuntu-12.04.2-desktop-i386.iso
md5sum: ubuntu-12.04.2-desktop-i386.iso: No such file or directory
limeylew@limeylew-P9852A-ABA-753N:~/Downloads$ ^C
limeylew@limeylew-P9852A-ABA-753N:~/Downloads$

---

### Post by r-senior on 2013-04-06
Could you show what ISO files are in the directory?

```
ls *.iso
```

---

### Post by Elfy on 2013-04-06
Alternatively you could use TAB once in the correct directory

```
md5sum <TAB TAB> 
```

you should then get the available files in the directory, you can also use tab to autocomplete the file name

```
md5sum ub<TAB>
```

---

### Post by L Campbell on 2013-04-06
Thank you.

limeylew@limeylew-P9852A-ABA-753N:~$ cd ~/Downloads
limeylew@limeylew-P9852A-ABA-753N:~/Downloads$ ls *.iso
ubuntu-12.04.2-desktop-i386.iso  ubuntu-12.10-desktop-i386.iso
limeylew@limeylew-P9852A-ABA-753N:~/Downloads$

---

### Post by L Campbell on 2013-04-06
limeylew@limeylew-P9852A-ABA-753N:~$ cd ~/Downloads
limeylew@limeylew-P9852A-ABA-753N:~/Downloads$ md5sum <TAB TAB>
bash: syntax error near unexpected token `newline'
limeylew@limeylew-P9852A-ABA-753N:~/Downloads$ md5sum ub<TAB>
bash: syntax error near unexpected token `newline'
limeylew@limeylew-P9852A-ABA-753N:~/Downloads$ 

Looks like I made an error here.

---

### Post by r-senior on 2013-04-06
When it says <TAB> it means press the tab key on your keyboard. If it matches part of a file name in the directory, the rest of it gets filled in without typing. It's more difficult to explain than it is to do.

---

### Post by L Campbell on 2013-04-06
OK, I tried with TAB TAB and this what I got:-

limeylew@limeylew-P9852A-ABA-753N:~$ cd ~/Downloads
limeylew@limeylew-P9852A-ABA-753N:~/Downloads$ md5sum ubuntu 12.04.2
md5sum: ubuntu: No such file or directory
md5sum: 12.04.2: No such file or directory
limeylew@limeylew-P9852A-ABA-753N:~/Downloads$

---

### Post by r-senior on 2013-04-06
OK, let's try a different approach:

```
md5sum ~/Downloads/*.iso
```

That should at least get you what you need.

---

