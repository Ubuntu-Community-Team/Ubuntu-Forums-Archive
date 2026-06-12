---
title: "Root Terminal"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by atmu5fear on 2008-06-24
Hi, I've posted earlier about my german keyboard... problem solved. New issue. I want to install my wireless card drivers. I have read the thread on how to. My problem is when I go into the Terminal i'm in user@xubuntu :~$ but i need to be logged in as root. I can't figure out how to find root terminal. I run ubunutu on my desktop and there is a terminal in accessories, and a root terminal under system tools. but on xubuntu there is only terminal in accessories, and no root terminal. Please help

---

### Post by Methuselah on 2008-06-24
You can preface everything you need to do as admin with 'sudo'.
However, if for some reason that's not suitable try

```

sudo su

```

after you bring up the terminal.
You'll be root for the rest of the session until you 'exit' so be careful.

---

### Post by iaculallad on 2008-06-24
> **atmu5fear said:**
> Hi, I've posted earlier about my german keyboard... problem solved. New issue. I want to install my wireless card drivers. I have read the thread on how to. My problem is when I go into the Terminal i'm in user@xubuntu :~$ but i need to be logged in as root. I can't figure out how to find root terminal. I run ubunutu on my desktop and there is a terminal in accessories, and a root terminal under system tools. but on xubuntu there is only terminal in accessories, and no root terminal. Please help

If you configured your Root account, you could login as root by typing **su** in your terminal and input the root password.

```
su
```

Or, if you did not configure the root account (By default, Ubuntu had disabled it), try to type **sudo -i** in your terminal instead and **input your own password**.

```
sudo -i
```

To login as root on your terminal.

---

### Post by atmu5fear on 2008-06-24
so i'm entering "sudo" at the command prompt (windows talk) and that will allow me to be logged into root? thanks for the quick response

---

### Post by atmu5fear on 2008-06-24
okay got it figured out... thanks guys

---

