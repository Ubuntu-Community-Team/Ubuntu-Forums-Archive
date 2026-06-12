---
title: "useradd -m not creating home directory"
date: 2012-01-17
forum: New to Ubuntu
---

### Post by SteveMHaupt on 2012-01-17
when I add a user using useradd it doesnt create the home directory even when I use -m. Also WHen I log out and try to log back in as that user it logs in but the GUI fails to load. I know adduser is easier but I really would like to do it with the useradd command. Please and help would be great.

---

### Post by llamabr on 2012-01-17
I use adduser.  What's the attraction to useradd?

---

### Post by SteveMHaupt on 2012-01-17
it's like buying a car that's transmission is both auto and  manual. Sometime you just want to sit back and let it shift for you, and then theres times when you wanna do it yourself.

---

### Post by CharlesA on 2012-01-19
> **SteveMHaupt said:**
> it's like buying a car that's transmission is both auto and  manual. Sometime you just want to sit back and let it shift for you, and then theres times when you wanna do it yourself.
I use useradd when scripting.

It works fine for me on Lucid:

```
charles@Atlantis:~$ sudo useradd -m user2
charles@Atlantis:~$ ls -ld /home/user2
drwxr-xr-x 2 user2 user2 4096 2012-01-19 14:54 /home/user2

```

---

### Post by Dangertux on 2012-01-19
```

sudo useradd -m -s /bin/bash -c 'This is my User' -G admin <username>

```

will give you a home directory a shell of bash a nifty little c omment and they'll be a sudoer.

Problem solved, don't forget to passwd afterwards or add the -p switch to set a password.

hope this helps.

---

