---
title: "read(2) in c"
date: 2013-05-13
forum: Programming Talk
---

### Post by ferizhandi on 2013-05-13
i want to take some data from user! so i use **read** function in a loop. but i have a problem. please see this example:
while(1)
    {
        countRead=read(0,buffer,strlen(buffer));
        write(2,"READ",9);
   }

when i'am entering a text in command line and press return, write function run for count of charachter of user text.

for example: when i'm entered 12 and press Enter , in command line write:
READ READ READ
for each char write READ.

please help me.

---

### Post by dwhitney67 on 2013-05-13
Use fgets() to read input from the user.  Use the return value of fgets() to ensure that you have a non-NULL string, and then strlen() to determine how many characters have been read.  From there, you can use a for-loop to print out READ for the number of characters that are in the string.

---

### Post by ferizhandi on 2013-05-14
i can't use this function because i have to use system call function, but tank you.

---

### Post by dwhitney67 on 2013-05-14
What do you mean by "system call"?  Why must you use only read()?

---

### Post by ferizhandi on 2013-05-14
i have a operating system project so i can use only  [these functions]("http://linux.die.net/man/2/").

---

### Post by dwhitney67 on 2013-05-14
Ahh.. schoolwork.  It makes sense now why you are restricted to using a low-level function.

Have you read the man-page for read (section 2)?  It clearly states that the number of bytes that are read are returned by the function.  Of course, you also need to take into account any errors that may occur (while fetching input from a user).  Thus you should not assume that read() always returns a value greater than zero.

---

### Post by ferizhandi on 2013-05-14
yeah i read it , and solved my problem , tank you

---

