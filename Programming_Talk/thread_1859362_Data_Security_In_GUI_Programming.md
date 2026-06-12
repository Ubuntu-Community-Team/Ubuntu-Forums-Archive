---
title: "Data Security In GUI Programming"
date: 2011-10-13
forum: Programming Talk
---

### Post by uahmed on 2011-10-13
Hi 

I am having a situation like i want to make a GUI Application which will fetch data from remote database . and for accessing database i need to write user name and password . 

I want that through my GUI application the data security of user name and password should remain . As python dont make exe file so i tried freeze and py2exe but it through me error of importing Qt Library . 

What Language should i use to make GUI so my data security of user name and password  remains . 

Thank You

---

### Post by Vaphell on 2011-10-13
language is a secondary issue at best. If you store user/password somewhere locally it can be extracted no matter what (if program can read data, hacker can look what program does and repeat the process or simply read data from program memory). Best solution - authorize every time (either with database login data or indirectly from some passworded encrypted file that stores the data) and make program 'forget' the details right after opening the connection. And make sure that the connection to the database is encrypted so it can't be eavesdropped.

---

### Post by uahmed on 2011-10-13
hi 

Thank you for the reply , it is helpful . I just want to cover the basic security like in python i will be defining all user id and password in code and i cant make the exe of that file so code remains there and id and password can easily be seen .

What i want that i make gui which will be in the form exe and user cant see the code . I tried using the py2exe and freeze but it give me errors of libraray . So any other way of doing this ?

---

### Post by DangerOnTheRanger on 2011-10-14
> **uahmed said:**
> hi 

Thank you for the reply , it is helpful . I just want to cover the basic security like in python i will be defining all user id and password in code and i cant make the exe of that file so code remains there and id and password can easily be seen .

What i want that i make gui which will be in the form exe and user cant see the code . I tried using the py2exe and freeze but it give me errors of libraray . So any other way of doing this ?

It's still possible to find the DB username and password, even if you use one of those sorts of tools. The fact that you need both the username and password stored on the client-side GUI suggest a fundamental design error, so I suggest trying to design that part of your program again.

---

### Post by Vaphell on 2011-10-14
when you have data stored in client, you can only obfuscate it at best, but not make it completely unavailable to a dedicated attacker. It's like giving a locked box, providing a key (program has it somewhere as it has to be able to open the box) and expecting that the box will stay locked. Ok, the key may be hidden but once it's found it's game over.
Just like DOTR said - it's a design flaw and there is no way around it.

how does your system look like and how tough the security is supposed to be? (there is no absolute security, it's all about risk balance)

---

