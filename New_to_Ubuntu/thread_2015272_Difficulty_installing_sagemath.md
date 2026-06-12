---
title: "Difficulty installing sagemath"
date: 2012-07-03
forum: New to Ubuntu
---

### Post by Ubuabaubu on 2012-07-03
Hello.  I do not have a lot of experience with ubuntu.  I'd like to install a program called Sagemath (notebook).  Every guide and install manual and advice bit I see assumes a level of experience with which I am not equipped.  Here is an example: 
[https://help.ubuntu.com/community/SAGE](https://help.ubuntu.com/community/SAGE)

I have downloaded a binary (for 12.04) yet these suggested terminal commands return a message reading "no such file or directory".  From downloading the binary to running the installed software I need very explicit advice.  I will answer any questions to help narrow and clarify my situation.  Thank you!

---

### Post by Ubuabaubu on 2012-07-03
Perhaps I should clarify, the "no such file or directory" message is currently my only snag point.  Still I am so very confused by the process and instructions that I do not know if I have a specific issue or a more general problem of inexperience.

---

### Post by anewguy on 2012-07-03
Which command from that link, for the binary section, is returning the error?

---

### Post by Ubuabaubu on 2012-07-03
> **anewguy said:**
> Which command from that link, for the binary section, is returning the error?


tar --lzma -xvf /path_to_sage_package/sage-?.?.?-linux-ubuntu-...lzma

---

### Post by anewguy on 2012-07-07
I assume that in the line you show:

tar --lzma -xvf /path_to_sage_package/sage-?.?.?-linux-ubuntu-...lzma 

you:

replaced "path_to_sage_package" to the actual path - perhaps something like ~/Downloads?

replaced "sage-?.?.?" with the actual release numbers

replaced ...lzma with something (I'm thinking there is part of the statement not showing)

---

