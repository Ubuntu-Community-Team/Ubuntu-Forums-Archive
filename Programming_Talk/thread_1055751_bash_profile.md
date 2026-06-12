---
title: "bash_profile?"
date: 2009-01-31
forum: Programming Talk
---

### Post by abhilashm86 on 2009-01-31
i am just in process of learning bash,so where is .bash_profile file, only .bashrc and .bash_logout files are found:), 
one more can some one tell a good programming bash, i'm following o'rille there's much of details rather than programs

---

### Post by GammaRay256 on 2009-01-31
If it's not there, you should just be able to create it.

---

### Post by geirha on 2009-01-31
If .bash_profile is not found, it will look for .profile, which you should have.

---

### Post by abhilashm86 on 2009-01-31
yes i have .profile in /home/abhilash, i guess i need to create .bash_profile on my own?

---

### Post by geirha on 2009-01-31
You may, but do note that if you create a .bash_profile, .profile will no longer be read. If you want both to be read, put the line ```
source .profile
``` in .bash_profile.

---

