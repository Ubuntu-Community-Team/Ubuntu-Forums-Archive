---
title: "Bash script sudo password"
date: 2007-06-11
forum: Programming Talk
---

### Post by satbobo on 2007-06-11
Hi everybody,
I want to create I script to update a small cluster of computers to install software and perform several tasks.
Sometimes it happens that I need to call commands with admin rights but of course in that case I need to prompt the password. 
Since I'd like to automate the all process I am wondering if there is a way to input the sudo password from a file or if there exist other workarounds.
Thanks in advance

---

### Post by FryerFox on 2007-06-11
The traditional way is to use public-private key authentication:

[http://www.ece.uci.edu/~chou/ssh-key.html](http://www.ece.uci.edu/~chou/ssh-key.html)

---

### Post by satbobo on 2007-06-11
Thank you very much for your reply... I will follow your advice...cheers

---

