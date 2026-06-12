---
title: "Beginner compiling and running c++ program"
date: 2011-05-09
forum: Packaging and Compiling Programs
---

### Post by ayeritsian on 2011-05-09
Hello
I am new to linux.
I want to compile and run a simple c++ hello word program, I use the following command
g++ hello.cpp -o ./hello
but it doesn't work.
I've also tried to run the executable separately but it keeps saying 
bash: ./hello: Permission denied
when I try the
sudo ./hello 
it says
sudo: ./hello: command not found

Thanks for your answers.

---

### Post by cipherboy_loc on 2011-05-09
What is the output of the g++?


Cipherboy

---

### Post by jerome1232 on 2011-05-10
If you have an executable then it sounds like the g++ command succeded, you may need to give your executable permission to execute with chmod

```
chmod +x hello
```

---

### Post by ayeritsian on 2011-05-10
If i run command
g++ hello.cpp -o ./hello
It will simple create executable hello
It doesn't output anything on the screen.

---

### Post by ayeritsian on 2011-05-10
The 
chmod +x hello 
also didn't work.

It doesn't output anything.

---

### Post by ayeritsian on 2011-05-12
I've solved the issue.There must be newline character after the string.

---

