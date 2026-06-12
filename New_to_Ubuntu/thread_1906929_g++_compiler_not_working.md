---
title: "g++ compiler not working"
date: 2012-01-10
forum: New to Ubuntu
---

### Post by uabhi12 on 2012-01-10
[FONT=Times New Roman][SIZE=3]I have unpacked some tar files in the usual way and it has created a new direc[/SIZE][/FONT][SIZE=3]tory .When I go to that directory and give the 'make' command a long message is coming which ends with 
    make:g++:command not found
Can anyone tell me what is happening?[/SIZE]

---

### Post by lechien73 on 2012-01-10
Hi & welcome to the forums,

Have you made sure g++ is installed? Try:

```
sudo apt-get install build-essential g++
```

and let us know if that solves it :)

---

### Post by uabhi12 on 2012-01-10
[SIZE=3]This is what I get when I give sudo apt-get install build - essential g++

abhijit@abhijit:~/P8157/pythia8157$ sudo apt-get install build - essential g++
[sudo] password for abhijit: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'build' has no installation candidate
E: Unable to locate package essential
  One more thing - is the sudo password always invisible and is it my ubuntu password[/SIZE]?

---

### Post by bouncingwilf on 2012-01-10
It appears you have inserted spaces where you should not have! what you require (as advised) is :

sudo apt-get install build-essential g++
Not sudo apt-get install build - essential g++ ; the extra spaces indicated you were trying to install a package called build whereas you require build-essential.

Try without the spaces and it should work.

Bouncingwilf

PS yes, the password is not echoed; yes, it is your normal Ubuntu password.

---

### Post by dsmo223 on 2012-01-10
Also, in a  linux command line enviroment whenever you type your password, it will stay invisible.

---

### Post by uabhi12 on 2012-01-11
[SIZE=3]Thanks lechien 73 and bouncingwilf. My 'make' command is now working in your suggested method. But next I need the 'gmake' command to work. But it is not working. Specifically I am trying to run a program main04 by tthe command 'gmake main04' which will make an executable file main04.exe according to the README file of the program. But the computer response is: gmake command not found. How can I solve this?[/SIZE]

---

### Post by lechien73 on 2012-01-12
'gmake' is called 'make' on Linux systems, so:

```
make main04
```

should work :)

---

