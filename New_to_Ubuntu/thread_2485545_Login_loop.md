---
title: "Login loop"
date: 2023-04-01
forum: New to Ubuntu
---

### Post by vermiou on 2023-04-01
Hello :)

Here is my problem: when I try to login, it won't let me login. Instead, I'm invited again to login. So it's a loop. But it's not a problem of wrong password

Here is what I have done before the problem arrived:
-installing miniconda3
-trying to add a path to the PATH variable, successively in 2 files (one of which is .profile, the other I don't remember the name)

I searched the solution on internet. I saw that this problem may be caused by PATH conflicts between two files. So what I did is I deleted the lines that I added in .profile, via the command line version of Ubuntu (Ctrl+Alt+F3 from the login prompt). But it didn't solve the issue. I don't remember the name of the other file so I wasn't able to modify (or delete) it. I might be wrong but I think the said file starts like ".param..."

Thank you very much for your help! :)

EDIT: I managed to find the name of the second file : ~/.pam_environment. I deleted it and it solved my problem! :)

---

