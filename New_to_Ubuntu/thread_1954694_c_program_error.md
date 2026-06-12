---
title: "c program error"
date: 2012-04-08
forum: New to Ubuntu
---

### Post by sreeharitk on 2012-04-08
Hi all
I am new to linux and new to C i have  a problem in the below program hope some one will help me
Problem
In the below program, if I dont enter y or n it should display 'invalid data' and repeat the loop and display enter y or n.  It is working properly but the problem is  it displays 2 times!! instead of just one time

 enter y or n
m
invalid data
 enter y or n
invalid data
 enter y or n

Here is the code
#include <stdio.h>
main()
{
char inp, valid='n' ;
while (valid=='n')
{
valid=' ';
puts (" enter y or n");
inp=getchar ();
fflush (stdin);
if (inp=='y')
puts ("valid point");
else if (inp=='n')
puts ("validinput");
else
{
puts ("invalid data");
valid='n';
}
}
}

---

### Post by TeoBigusGeekus on 2012-04-08
[You can't use stdin with fflush.]("http://www.velocityreviews.com/forums/t731285-fflush-not-flusing-stdin.html")
Flush your input buffer with a while loop:
```
#include <stdio.h>
 main()
 {
     char inp, valid='n' ;
     while (valid=='n')
     {
         valid=' ';
         puts (" enter y or n");
         inp=getchar ();
         while (getchar() != '\n');
         if (inp=='y')
             puts ("valid point");
         else if (inp=='n')
             puts ("validinput");
         else
         {
             puts ("invalid data");
             valid='n';
         }
     }
 }
```

---

### Post by sreeharitk on 2012-04-08
Dear Brother
Hope you are celebrating life there.
great to hear from you.Thanks for the help 
It works out great!!
nice meeting you too

---

### Post by TeoBigusGeekus on 2012-04-08
You're welcome and hope you're well yourself.
Don't forget to mark the thread as solved.

---

### Post by sreeharitk on 2012-04-08
Hi Sir
thanks for your help. I just need to know if my understanding abouf fflush is correct. 
Fflush:fflush is a function in C which is used to clear the buffer. A  buffer is  a temporary storage area which contains characters typed in  by the  user. The use of fflush clears this storage area and allows new   characters to be stored into it.
is it correct?? if this is correct, then why did it cause to run the loop twice in my program?
and what exactly
"while (getchar() != '\n'); " does?
Hope you will reply me..

---

### Post by TeoBigusGeekus on 2012-04-08
fflush works only for output streams; otherwise, its behaviour is uncertain.
If you're just starting to learn C, forget about fflush.

```
while (getchar() != '\n');
```
This part of the code takes characters from the buffer until it meets an end of line character. Since the last character you gave after pressing m, or whatever, was enter (new line), this command clears the buffer.

---

### Post by sreeharitk on 2012-04-08
Thanks once again :):)

---

### Post by TeoBigusGeekus on 2012-04-08
You're welcome mate.

---

