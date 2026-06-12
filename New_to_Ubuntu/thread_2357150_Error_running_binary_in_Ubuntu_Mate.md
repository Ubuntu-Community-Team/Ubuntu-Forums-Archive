---
title: "Error running binary in Ubuntu Mate"
date: 2017-03-30
forum: New to Ubuntu
---

### Post by jhernandezgarcia on 2017-03-30
Hi All

I am quite new using Ubuntu Desktop  and Ubuntu Mate for Raspberry Pi3

Currently I am trying to execute one binary in Ubuntu Mate for 64 bits that is running fine in Ubuntu Desktop.It is an agent.

My issue is when I try to execute this binary I get the following messages error in the log
   ./ucxjlx6: 1: ./ucxjlx6: ^?ELF^B^A^A^B: not found
   ./ucxjlx6: 2: ./ucxjlx6: Syntax error: ")" unexpected


The command I am try to execute is 
     ./ucxjlx6 1> ucxjlx6.log 2>&1 &

Please anybody could give me one clue about how to solve this?

Many Thanks in advance

---

### Post by Impavidus on 2017-03-30
It seems to me that you try to run an executable compiled for the amd64 architecture (like the Ubuntu desktop has) on the raspberry pi, which has an ARM chip. The software has to be compiled for the arm chip before it can run on the raspberry.

---

