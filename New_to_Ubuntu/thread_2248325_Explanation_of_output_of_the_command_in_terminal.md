---
title: "Explanation of output of the command in terminal"
date: 2014-10-14
forum: New to Ubuntu
---

### Post by rohit13 on 2014-10-14
I am new to linux and was trying out certain commands on the terminal.
When I tried 

wc < sfddfs |& wc
sfddfs: No such file or directory.
      0       0       0

Here sfddfs is a file which does not exist. Why does it give the output 0 0 0.
When contents of file of sfddfs is passed to wc, it finds the file does not exist, and it will give the error output which is passed through pipe to next wc. So shouldnt wc calculate the with the output on StdError?i.e. 1       6      34

---

### Post by Lars Noodén on 2014-10-14
wc reads stdout, not stderr. So the result of no input would be 0 0 0 ( no lines, no words, no characters )  You could redirect stderr to stdout though if you want.

---

### Post by rohit13 on 2014-10-16
Thanks!

---

