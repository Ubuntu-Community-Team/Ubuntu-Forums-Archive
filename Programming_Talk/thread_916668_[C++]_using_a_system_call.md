---
title: "[C++] using a system call"
date: 2008-09-11
forum: Programming Talk
---

### Post by StOoZ on 2008-09-11
when I do this :
> system("wget http://www.somesite/txt.html")

how can I check when the file is fully downloaded??

---

### Post by Zugzwang on 2008-09-11
Try to find out if you can obtain the return value of wget somehow.

Second possibility: Execute that program using popen(...) and parse its output to look for a success message.

---

### Post by amo-ej1 on 2008-09-11
man system will tell you:

```

RETURN VALUE
       The value returned is -1 on  error  (e.g.   fork(2)  failed),  and  the
       return  status  of the command otherwise.  This latter return status is
       in the format specified in wait(2).  Thus, the exit code of the command
       will  be  WEXITSTATUS(status).  

```

Easy as that thus 

```

int ret = system("my_magical_command");
if(WEXITSTATUS(ret)==0) 
{
   printf("Everybody is happy now\n");
}

```

---

### Post by cmay on 2008-09-11
i am seaching trough inet.h trying to find a routine already writtten for this. but this is how i would have done.do not know if it helps at all.
[PHP]#include<stdio.h>
#include<stdlib.h>
int main(int argc,char **argv)
{

if(system("wget http://start.ubuntu.com/8.04/")==0)
{
printf("ok\n");
/* insert a file rutine that checks if file exist and do something with file here*/

}
else printf("not ok\n");
/* return error message instead*/
return 0;
}[/PHP]

---

### Post by StOoZ on 2008-09-11
cool folks!! thanks a lot!
btw , eventually I decided to use libcurl for that , the reason : since im quite new to C++ , i want to learn how to use more libs , even though libcurl is C.

thanks!

---

