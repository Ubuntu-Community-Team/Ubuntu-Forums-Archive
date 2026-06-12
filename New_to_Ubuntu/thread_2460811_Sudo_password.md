---
title: "Sudo password"
date: 2021-04-19
forum: New to Ubuntu
---

### Post by einsteiner on 2021-04-19
Hey all, I am new to Ubuntu, and I am wondering why Terminal will not let me enter a sudo password. After putting in Sudo commands, it asks me for my sudo password, but it won't let me type anything. I am pretty sure I am just an idiot and am missing some crucial element, but if anyone could help, that would be great!

---

### Post by The Cog on 2021-04-19
It's just not echoing the password as you type. Type it anyway.
It's to stop you being "shoudler-surfed" - people behind you reading it as you type.

Oh, and welcome to the forum.

---

### Post by Holger_Gehrke on 2021-04-19
'sudo' will not echo the entered password - not even as a line of placeholder characters - to protect you; by seeing a line of characters an attacker would know the length of the password, which would simplify a brute force attack immensely. Just type in the password 'blind', it will register.

Holger

---

### Post by rsteinmetz70112 on 2021-04-19
If you get it wrong you will get an error message. I have some strong passwords that require contortions to type and I usually have to put them in more than once.

---

### Post by ActionParsnip on 2021-04-19
Just type your password and press ENTER. It is being accepted

---

