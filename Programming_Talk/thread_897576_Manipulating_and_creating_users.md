---
title: "Manipulating and creating users"
date: 2008-08-22
forum: Programming Talk
---

### Post by blooddrunk on 2008-08-22
Hi! Are there any libraries and commands in C with which a user can be manipulated and created?
 I am particularly looking for a way to change the values of the home directory,group and login shell (C command that corresponds to usermod). Also, I want to be able to create a local user(C command that corresponds to useradd)
Thanks in advance

---

### Post by Zugzwang on 2008-08-22
Is there any problem with calling useradd from your program?

---

### Post by blooddrunk on 2008-08-22
No,not at all. Useradd and usermod work perfectly. It's just that I am not sure whether every installation of Linux has these commands?

---

### Post by ghostdog74 on 2008-08-22
if you insist on C, you can roughly find out how its done by viewing [source code](http://www.koders.com/c/fidE189FCD5F4E86FF5ECFCB12CD5EF5AF5BCA6DA24.aspx)

---

### Post by blooddrunk on 2008-08-22
Thanks. I think I'm going to stick to useradd and usermod. Hopefully, they will not give me any trouble

---

