---
title: "How can I force my PC to just work on my project and nothing else ( fasterest speed e"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by just_linux on 2008-08-09
I want to download many files as fastest as possible . 
I do not care about any other programs  ( [I want to force the PC to just work on my code ):lolflag:

Also for downloading, I use axel? Do you know if we have any other program that does it faster 
For some reason axel keeps disconnecting is it any solution to it? ( like wget that you can set -w to a number to foo the server ????

Also: if I am reading a text from a file, everyline will have a "\n" newline at the end of the string
How should I get ride of those?
any code?
Thanks :guitar:  
Thanks

---

### Post by tamoneya on 2008-08-09
find the pid of your program in "top" and then run this code:```
sudo renice -19 <pid>
```

---

### Post by just_linux on 2008-08-09
> **tamoneya said:**
> find the pid of your program in "top" and then run this code:```
sudo renice -19 <pid>
```

what is pid?:lolflag:

---

### Post by Crafty Kisses on 2008-08-09
> **just_linux said:**
> what is pid?:lolflag:

I'm guessing process ID.

---

### Post by WRDN on 2008-08-09
> **just_linux said:**
> what is pid?:lolflag:

PID = Process ID

Have a look in the System Monitor under the Processes tab, or type "top" in the Terminal to list the processes and their corresponding PID.

---

### Post by tamoneya on 2008-08-09
in top the pid is the column all the way on the right.  It is most likely for you a 4 or 5 digit number.

---

### Post by sdennie on 2008-08-09
> **just_linux said:**
> Also: if I am reading a text from a file, everyline will have a "\n" newline at the end of the string
How should I get ride of those?
any code?


You can use dos2unix to remove those:

```

dos2unix name_of_misbehaving_file

```

---

