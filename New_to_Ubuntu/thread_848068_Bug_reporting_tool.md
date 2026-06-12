---
title: "Bug reporting tool"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by mailtwogopal on 2008-07-03
Hi guys,

   I have  ubuntu hardy heron in my box. Recently i installed "Bug reporting tool" from "Add/remove" gateway. But when i try to open the tool it prompted me an error that "required component not loaded: Failed". Please help me and thanks in advance.

---

### Post by hyper_ch on 2008-07-03
try to run it from the command line. That should give you more clues about errors.

---

### Post by mailtwogopal on 2008-07-06
hi hyper,

  i cannot find the exact commannd to run this in terminal. please help me.

---

### Post by hyper_ch on 2008-07-06
well, have a look at the menu entry and then you have the command for running it also in the cli

---

### Post by mailtwogopal on 2008-07-06
hi hyper,

  i pressed "alt+F2" to run the app named in menu entry as "bug report tool". In run window i checked the box "run in terminal" it prompted the error "could not open file:///home/gopal/bug-buddy". and also told that "bug buddy" is a child process. i typed "bug-buddy" in terminal but i got a message as "cannot find". it also prompts to install so i typed "sudo apt-get install bug-buddy" and i got following o/p:

```

gopal@gopal-desktop:~$ sudo apt-get install bug-buddy
[sudo] password for gopal: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

```

---

### Post by hyper_ch on 2008-07-06
find in the mneu properties the name of the binary that is executed

---

### Post by mailtwogopal on 2008-07-07
hi hyper,

   i installed bug-buddy using "sudo apt-get install bug-buddy". this time it worked. but after installing i again open the same in terminal by typing "bud-buddy" but it prompted me an error "either --appname or --package is required". wat to do, please help me.

---

### Post by hyper_ch on 2008-07-07
well, all i can say is to read the man pages on how to use it.

---

### Post by Canis familiaris on 2008-07-07
> **mailtwogopal said:**
> hi hyper,

   i installed bug-buddy using "sudo apt-get install bug-buddy". this time it worked. but after installing i again open the same in terminal by typing "bud-buddy" but it prompted me an error "either --appname or --package is required". wat to do, please help me.

I think it is a CLI software. I think you have to enter bug-buddy firefox for example to debug firefox say.

EDIT: I'm only guessing

---

