---
title: "c syntax if conditional"
date: 2009-12-22
forum: Programming Talk
---

### Post by monkeyking on 2009-12-22
Can anyone clarify why the following makes a difference

[PHP]
if(a=b()<0) //doesnt work
if((a=b())<0) //does work
[/PHP]

A full example here,

[PHP]
#include <stdio.h>
#include <stdlib.h>
#include <err.h>
#include <fcntl.h>
#include <sysexits.h>
#include <unistd.h>

int
main()
{
  int fd;
  size_t bytes_read, bytes_expected = 1000*sizeof(double);
  char *data=new char[bytes_expected];
  char *infile = "tst.cpp";

  if ((fd = open(infile,O_RDONLY)) < 0) // <- why is the parenthesis needed here
    err(EX_NOINPUT, "%s", infile);
  printf("fd is:%d\n",fd);
  bytes_read = read(fd, data, bytes_expected);
  fprintf(stderr,"%s\n",data);


  exit(EX_OK);
}
[/PHP]
Does parenthesis around an assignment in a conditional mean that the return value of the rval is returned?

Thanks in advance

---

### Post by not_a_phd on 2009-12-22
I think it is an order of operations thing between the = operator and the < operator.

[COLOR=#000000][COLOR=#007700]if([/COLOR][COLOR=#0000BB]a[/COLOR][COLOR=#007700]=[/COLOR][COLOR=#0000BB]b[/COLOR][COLOR=#007700]()<[/COLOR][COLOR=#0000BB]0[/COLOR][COLOR=#007700]) [/COLOR][COLOR=#FF8000]//doesnt work 

because you are effectively evaluating:
a = (b()<0)

and then interpretting as a boolean inside the if statement.


[/COLOR][COLOR=#007700]if(([/COLOR][COLOR=#0000BB]a[/COLOR][COLOR=#007700]=[/COLOR][COLOR=#0000BB]b[/COLOR][COLOR=#007700]())<[/COLOR][COLOR=#0000BB]0[/COLOR][COLOR=#007700]) [/COLOR][COLOR=#FF8000]//does work  [/COLOR][/COLOR]

Because you first evaluate (a=b()). The lval, a, is then returned from the inner parenthesis set and compared with 0.

I think.

---

### Post by lisati on 2009-12-22
I don't know about the rval stuff but suspect it could be something to do with operator precedence. Without the parenthesis there's a certain ambiguity: should the compiler generate code based on assigning a value to fd based on the result of open(infile,O_RDONLY) < 0 or should it evaluate the condition based on (fd = open(infile,O_RDONLY)?

edit: in other words, what not_a_phd said.

---

### Post by ankur1990 on 2009-12-22
i think the if condition suntax is :
if(a==b) insted of if(a=b)

---

### Post by lisati on 2009-12-22
> **ankur1990 said:**
> i think the if condition suntax is :
if(a==b) insted of if(a=b)

I think what the OP was trying to do was open a file and evaluate if the open worked all in one go, in which the (a=b) would be correct. 


[COLOR="White"]edit: I just noticed that fd is delcared as int. Hmmmmm..... isn't it more usual to declare it as FILE * ?????[/COLOR]

---

### Post by kwyto on 2009-12-22
guys, guys,
 
i don't in PHP but in C /C++ functions return -1 if there is an error. just compare the return value to -1.
 
[FONT=Courier New][COLOR=#007700]>  
[FONT=Courier New][COLOR=#007700]if (([/COLOR][COLOR=#0000bb]fd [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]open[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]infile[/COLOR][COLOR=#007700],[/COLOR][COLOR=#0000bb]O_RDONLY[/COLOR][COLOR=#007700])) < [/COLOR][COLOR=#0000bb]0[/COLOR][COLOR=#007700]) [/COLOR][/FONT][FONT=Courier New][COLOR=#ff8000]// <- why is the parenthesis needed here 
    [/COLOR][COLOR=#0000bb]err[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]EX_NOINPUT[/COLOR][COLOR=#007700], [/COLOR][COLOR=#dd0000]"%s"[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]infile[/COLOR][/FONT][FONT=Courier New][COLOR=#007700]); 
  [/COLOR][COLOR=#0000bb]printf[/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]"fd is:%d\n"[/COLOR][COLOR=#007700],[/COLOR][COLOR=#0000bb]fd[/COLOR][/FONT][FONT=Courier New][COLOR=#007700]); 
  [/COLOR][COLOR=#0000bb]bytes_read [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]read[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]fd[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]data[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]bytes_expected[/COLOR][/FONT][FONT=Courier New][COLOR=#007700]); 
  [/COLOR][COLOR=#0000bb]fprintf[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]stderr[/COLOR][COLOR=#007700],[/COLOR][COLOR=#dd0000]"%s\n"[/COLOR][COLOR=#007700],[/COLOR][COLOR=#0000bb]data[/COLOR][/FONT][COLOR=#007700][FONT=Courier New]); [/FONT]
[/COLOR] 

 
the parenthesis are needed, like lisati said, to avoid ambiguity. 
also  = is not the same ==[/COLOR][/FONT]

---

### Post by monkeyking on 2009-12-22
thanks for your fast response people.

Maybe I didn't clarify my question enough.
I am indeed trying to open a file using a filedescriptor,
The filedescriptor should be a int, 0=stdin,1=stdout,2=stderr

So what I'm trying to do is logically equivalent to


[PHP]
fd=open(filename,RD_ONLY)
if(fd<0)
  fprintf(stderr,"some error")
[/PHP]

And my question, was that it looks like putting paranthesis around an assignment in a conditional will actually force the assigned value to be used in the comparison, is that correct?

like

[PHP]
if((a=b)<c)
  fprintf(stderr,"we are comparing b<c")
[/PHP]
and the assignment is actually a sideeffect


Thanks again for you replies

---

### Post by lisati on 2009-12-22
> **monkeyking said:**
> 
I am indeed trying to open a file using a filedescriptor,


OK, that makes sense. I'm closer to being on the same page......I was thinking in terms of another way of accessing files..... (/me wanders off to fix earlier post)

---

