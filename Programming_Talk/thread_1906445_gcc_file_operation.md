---
title: "gcc file operation"
date: 2012-01-09
forum: Programming Talk
---

### Post by sree88 on 2012-01-09
hi all
i have to code to which has file operations.

i have got 2 issues

**1.** i want to get the file name from the user> append the file extension> and mention that file name in the fopen() command.

2. the file that i want to open is in a folder from where the C program is run.

ie if i have a file named 123.txt in a folder "jkl"
   i ll get the name 123 from the user append .txt to the name and mention that name in
   the fopen command.
  i used the strcat() function to append, if the variable that holds the name is "fn", how can i mention it in the fopen command?
  
  can u  help me doin this??

---

### Post by MartijnNL on 2012-01-09
Perhaps someone here can help you, but wouldn't it be easier asking this on some C programming forum? Or post it the [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39") forum instead. 

Absolute Beginner Talk (and General Help) aren't really intended for programming questions.

---

### Post by nothingspecial on 2012-01-09
Moved to Programming talk.

---

### Post by Zugzwang on 2012-01-09
> **sree88 said:**
> 
  i used the strcat() function to append, if the variable that holds the name is "fn", how can i mention it in the fopen command?
  

Ok, so which type is "fn" of? I preesume that since it holds a string that was obtained using "strcat" that it is "char*". Now have a look at the documentation for the standard library what the parameters for "fopen" are (see, e.g., [http://linux.die.net/man/3/fopen](http://linux.die.net/man/3/fopen)) - for the first variant of the function, the parameter "path" is of type "const char*", which speaks for compatibility. So try to fill in "fn" as your first parameter to the "fopen" function.

---

### Post by sree88 on 2012-01-09
thanks all... now it is cleared..

---

### Post by Tony Flury on 2012-01-10
I am glad you got this solved, though to me this sounded very much like a homework or college assignment - in future you wont normally get help with such assignment. 

To be honest your question was very basic (using a variable vs a string constant), and if your tutor/professor has not covered that in your classes then you maybe need a better tutor, or a better textbook.

If in future you provide code which you have attempted to write, but which does not work in some specific way, then someone may well be willing to help you, when you post the code and a specific question.

---

