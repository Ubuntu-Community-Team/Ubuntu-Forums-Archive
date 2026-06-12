---
title: "How to create new folder in usr/local"
date: 2011-11-07
forum: New to Ubuntu
---

### Post by shico90 on 2011-11-07
Hello, for a reason I want to create a new folder in usr/local. can u help please?

---

### Post by haqking on 2011-11-07
> **shico90 said:**
> Hello, for a reason I want to create a new folder in usr/local. can u help please?

Read [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo")

/usr is owned by root so you will need to use sudo (command line) or gksudo if done graphically

---

### Post by Elfy on 2011-11-07
In a terminal 

sudo mkdir /usr/local/*nameoffolder*

If you want to use nautilus - Alt+F2 then gksudo nautilus - navigate and create

---

### Post by shico90 on 2011-11-07
Thank you :)

---

### Post by Elfy on 2011-11-07
Welcome - there's a Mark Thread Solved tool in Thread Tools at the top ;)

---

