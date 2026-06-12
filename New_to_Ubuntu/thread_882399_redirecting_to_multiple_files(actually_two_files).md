---
title: "redirecting to multiple files(actually two files)"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by jualansandal on 2008-08-06
Hi there,
I would like to ask, how to make a process redirected to multiple files, right now I just want to redirect it into two files.

For Example, I have test.sh file that contains **echo "test"** , and I want to redirect it into file log1 and log2 at the same time.
How the command should be ?

Thanks

---

### Post by eightmillion on 2008-08-06
If I understand you right, you want to redirect output of a command to multiple files. If that's the case you can use **tee**. For example,

> ps -ax | tee processes.txt | more
outputs ps -ax to processes.txt and the more command.

---

### Post by jualansandal on 2008-08-06
wow, thanks

that was fast.

I will try it

---

### Post by jualansandal on 2008-08-06
--

---

### Post by jualansandal on 2008-08-08
Hi, 
there is another problem again,
if I access the second file, the process is stopped and both log file is stopped to be written by the process.

I access it with jsp script and show it automatically for 5 second with javascript in the browser.

Any suggestion ?

thanks

---

### Post by jualansandal on 2008-08-10
I see -i option for ignoring something, will it solve my problem ?

---

### Post by eightmillion on 2008-08-10
Looks promising. You should try it.

---

### Post by jualansandal on 2008-08-19
I tried it, and the result is the same without -i options, any other suggestion/idea

thanks

---

