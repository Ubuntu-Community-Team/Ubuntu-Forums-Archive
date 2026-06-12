---
title: "Can't launch XAMPP application"
date: 2024-06-01
forum: New to Ubuntu
---

### Post by nadri on 2024-06-01
I am new in ubuntu linux OS , I am looking to install wordpress on XAMPP but I have an error which is when I click on "Go to Application" button or on "Get Started " button I have no result and I got an error message on Terminal :

" mkdir: cannot create directory ‘/run/user/0’: Permission denied
Authorization required, but no authorization protocol specified
Error: cannot open display: :0   "

Please help me to work with XAMPP normally.
Thanks in advance.

---

### Post by currentshaft on 2024-06-01
How do you get an error message in Terminal from clicking on something else? Are you running a command? Which instructions have you found and followed to set up XAMPP? It appears to be missing elevated privileges to start.

---

### Post by nadri on 2024-06-01
Yes , When I clicked on button I was seeing what was happening on the Terminal , That's why I noticed this error message.
It appears to be missing elevated privileges to start ? How to elevate privileges please ??

---

### Post by filiprybar on 2024-06-07
run sudo your-application, or if it shows error command not found type sudo -i
 and then type your-application

---

