---
title: "install veracrypt"
date: 2017-07-07
forum: New to Ubuntu
---

### Post by k28 on 2017-07-07
[https://ubuntuforums.org/showthread.php?t=2300683in](https://ubuntuforums.org/showthread.php?t=2300683in) post nr 4 he explains how to install it.unfortunalty i dont have the option: run or run in console i have the newest ubuntu. thx!

---

### Post by k28 on 2017-07-07
unfortunaly i cant edit the old thread: [https://ubuntuforums.org/showthread.php?t=2365520](https://ubuntuforums.org/showthread.php?t=2365520)

i managed to run the extractet file. i just ran the terminal(which is the console, ubut had no runin terminal option in contect menu...nervermind)
just drag and drop it in a terminal window.

it installed as it should but when i try to start it from the launcher it blinks a few time and nothing happens....whats the problem?

---

### Post by coffeecat on 2017-07-07
Threads merged. 

When you say you can't edit the old thread, it's not quite clear whether you mean the post that is now #1 in this thread, or [this thread](https://ubuntuforums.org/showthread.php?t=2300683) from nearly two years ago. If you mean the former, there's nothing stopping you from editing your own post. Just click on the "edit post" button. If you mean the two-year old thread, you can't. There are no posts of yours in it. If you meant by edit, that you can't post to the old thread, it's been long closed. You are far better off starting a new thread, as you have done, than necromancing a moribund one.

Good luck in finding a solution.

---

### Post by FATALERROR0x0x on 2017-07-08
Hello, i had the same proble and i have the solution in my thread itself.

[https://ubuntuforums.org/showthread.php?t=2365118](https://ubuntuforums.org/showthread.php?t=2365118)

---

### Post by k28 on 2017-07-09
so basicly 

sudo add-apt-repository ppa:unit193/encryption
sudo apt-get update



solved your problem? unfortunalty the problem still exist...

---

### Post by k28 on 2017-07-11
push?

---

### Post by deadflowr on 2017-07-11
> **k28 said:**
> so basicly 

sudo add-apt-repository ppa:unit193/encryption
sudo apt-get update



solved your problem? unfortunalty the problem still exist...

Then you need to install veracrypt.
```
sudo apt-get install veracrypt
```

---

### Post by k28 on 2017-07-13
thx that seems to work. next problem: veracrypt does nto decrypt the drive. i alsways get the error that the password is wrong. when i try it on windows 7 id works like a charme. any idea? maybe the password is complicated? :D

---

### Post by k28 on 2017-07-16
no one? :(

---

### Post by k28 on 2017-10-03
use zulumount instead

---

