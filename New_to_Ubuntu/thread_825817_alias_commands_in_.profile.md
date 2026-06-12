---
title: "alias commands in .profile"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by Zenze on 2008-06-11
Hello,

As I am brand new to Linux was messing around with the alias command. The guide I was reading said I could put alias commands in the .bash_profile file to allow me to use my custom commands every time I login. However I couldnt find the .bash_profile file in the home directory but instead I saw .profile and assumed it was the same thing. I put the alias commands in there but there they didnt work when I logged out and back in. Could Ubuntu using some file other than .profile or am I doing something else wrong?

Thanks for the help.

---

### Post by hyper_ch on 2008-06-11
bash aliases are in
```

~/.bashrc

```

---

### Post by KingTermite on 2008-06-11
I was reading "Ubuntu Linux Bible" when I first started and got the similar advice. It said to put the aliases in a .bash_aliases file. I created the .bash_aliases file, but still had trouble making it work.

I put everything in .bashrc instead, but recently I went back and got the other to work just because its cleaner. I put my aliases in the .bash_aliases file and at the bottom of my .bashrc I included "sh .bash_aliases" to read/execute that file.

---

### Post by Zenze on 2008-06-11
Awesome that worked great. Thanks for the help.

---

