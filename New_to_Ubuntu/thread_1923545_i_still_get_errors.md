---
title: "i still get errors"
date: 2012-02-10
forum: New to Ubuntu
---

### Post by sheplus3 on 2012-02-10
first my error read: 'command not found'  in the terminal of my virtual box ubuntu, when i tried to compile my first 'HELLO WORLD' program. then i applied lisati's code: sudo apt-get install build essential g++; then tried my program again <g++hello.cpp> but i got the following response: command not found. i tried spacing my code out like this : <g++ hello.cpp> and got this response: g++: error: hello.cpp: no such file or directory, g++: fatal error:no input files compilation terminated. i am really confused what can i do? thank you.

---

### Post by Paqman on 2012-02-10
Before you compile anything you need to install the package [build-essential]("apt:build-essential"). It contains g++, but also some other good stuff like the utility "make" that you're getting the error message on.

---

### Post by Fayaz427 on 2012-02-10
open your terminal and type this.....
sudo apt-get update

---

