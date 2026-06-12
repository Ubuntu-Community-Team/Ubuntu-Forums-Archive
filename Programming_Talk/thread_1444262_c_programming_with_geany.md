---
title: "c programming with geany"
date: 2010-04-01
forum: Programming Talk
---

### Post by sinhanikhil.5 on 2010-04-01
I wrote a simple program to add two numbers and compiled, till here its fine.i have saved it as sum.c on my desktop, but when ever I run the program its giving an error msg:
./geany_run_script.sh: 5: ./sum: not found.

actually I am not able to run any program, coz it gives the same error msg.

---

### Post by MadCow108 on 2010-04-01
you have to press build to build an executable
by default geany then creates an executable with the same name as the file but without extension
the execute script looks for that name

compile just compiles and does no linking

if you look at the build commands in the dropdown menu you see what geany actually does.

For more complex build rules you need a makefile in geany

---

### Post by sinhanikhil.5 on 2010-04-01
[IMG]http://musician/desktop/screenshot.png[/IMG]

no its not working, m getting the same error. and also geany auutomatically builds that file and also after hitting build its giving same error

---

### Post by MadCow108 on 2010-04-01
what says in the compiler message window when building?
it should be something similar to this:

gcc -Wall -o "sum" "sum.c" (in directory: some/folder)
Compilation finished successfully.

this means compile sum.c and create executable named sum

maybe you have set your working directory for execute different to that of the build command?

btw you can use the command above to compile in command line and execute in a terminal.
I recommend doing it that way in the beginning, as you learn more
see man gcc for more details
the important flags are: -o -c -I -L -l

---

### Post by sinhanikhil.5 on 2010-04-01
Ok now I am trying to execute program using terminal, but getting 2 error messages:-
gcc: unrecognized option '-wall'
sum.c:2:19: errror: conio.h: No such file or directory

---

### Post by Zugzwang on 2010-04-01
> **sinhanikhil.5 said:**
> Ok now I am trying to execute program using terminal, but getting 2 error messages:-
gcc: unrecognized option '-wall'
sum.c:2:19: errror: conio.h: No such file or directory

First of all, mind the difference between compiling and executing a program. According to the error messages, what you tried was *compiling* the program. Note that the "conio.h not found" error message means that unlike you have written in your first post, the program *did not* compile fine, unless you used a different source file.

Second, it is "-Wall" instead of "-wall" - mind the capitalisation!

Third, trying to compile a program using "conio.h" won't work. This is an outdated Windows-only header file. What you can try however is using the header file and ".c" file found in this thread: [http://ubuntuforums.org/showthread.php?t=1353043&highlight=conio.h](http://ubuntuforums.org/showthread.php?t=1353043&highlight=conio.h) - it is a somewhat compatible replacement for the legacy conio.h file. If you do so, add the "conio.c" file to the list of source files to compile.

---

### Post by sinhanikhil.5 on 2010-04-01
and how to execute in terminal after compiling

---

### Post by kleskjr on 2010-04-01
write './sum ' in the terminal
the file 'sum' is your output executable file

---

### Post by sinhanikhil.5 on 2010-04-01
#include <stdio.h>


int main(void)

{
    int num1;
    int num2;
    int sum;
    
    printf("Enter the no: ");
    
    scanf("%d", &num1);
    
    scanf("%d", &num2);
    
    sum = num1 + num2;
    printf("The sum is %d", sum);
    
    return(0);
    
}

OK! everything looks fine apart from when i execute first it ask:
Enter the no: ok i give 1 then hit enter, then its blank, ideally it should again ask Enter the no:...

now i give 2(without asking)
then it gives The sum is 3, which is againg correct.

so wot to do to ask enter the no again for second no.??

---

### Post by kleskjr on 2010-04-01
you didnt tell it to ask second time:

> **sinhanikhil.5 said:**
> #include <stdio.h>


int main(void)

{
    int num1;
    int num2;
    int sum;
    
    printf("Enter the no: ");
    
    scanf("%d", &num1);
    
    [COLOR="Red"]printf("Enter the second no: ");[/COLOR]
    scanf("%d", &num2);
    
    sum = num1 + num2;
    printf("The sum is %d", sum);
    
    return(0);
    
}

OK! everything looks fine apart from when i execute first it ask:
Enter the no: ok i give 1 then hit enter, then its blank, ideally it should again ask Enter the no:...

now i give 2(without asking)
then it gives The sum is 3, which is againg correct.

so wot to do to ask enter the no again for second no.??

---

### Post by sinhanikhil.5 on 2010-04-01
actually no. its not working if u ask to printf ("enter the second no:");

---

### Post by sinhanikhil.5 on 2010-04-01
> **sinhanikhil.5 said:**
> actually no. its not working if u ask to printf ("enter the second no:");
left hand side bottom corner is program executed with out asking to enter 2nd time and right hand side is source code. If u can see, sorry just took screen shot

---

### Post by kleskjr on 2010-04-01
did u compile it after editing the source?

---

### Post by sinhanikhil.5 on 2010-04-01
yes i did, i changed the soource and ctrl+s and after that compiled and run, again the same error..

---

### Post by kleskjr on 2010-04-01
sure you haven't change the output file name?
for me its working

---

### Post by kleskjr on 2010-04-01
ok, so you are running it from geany.
seems you have to save, compile, **build** and then run

---

### Post by sinhanikhil.5 on 2010-04-01
_**SOLVED**_

Thanks i Am really happy. Gr8 ful to u.




[COLOR=White].[/COLOR]

---

### Post by kleskjr on 2010-04-01
have fun with c ;)

---

### Post by sinhanikhil.5 on 2010-04-04
[SIZE=2][B]hey all, 
As I am learning c and pretty impressed by my pace(I knew a little b4.).
I have covered few topics like:-
writting simple programs, adding , sub, division... two nos.
if , if else and while loops..
do we have some books which gives real time experience so that i can practise, i mean free obviously.



[COLOR=White].[/COLOR]:guitar:
[/B][/SIZE]

---

### Post by knightsrv on 2013-02-27
Hi, I m also a newbie on C programming. I can compile,build and run a basic program from the console using,
gcc -c myProgram.c
gcc -o myProgram myProgram.c
and then, ./myProgram commands.
but whenever I m using an IDE like sublime text 2 or geany, I m having a particular error msg. its saying,

./geany_run_script.sh: 5: ./geany_run_script.sh: ./d: Permission denied
------------------
(program exited with code: 126)

pls help

---

### Post by ramreddy502 on 2013-02-27
> 
#ifndef include
 #define include
 #include "header.h"
 #include "cstring.h"
 #include <cstdlib>


#endif

class wrdC {
  
  public:     

     int bst;  //begining state number      
     int est;  //ending state number
     int nst;  //no of states
     int wid;  //word id
     char nm[nmL];
     
     wrdC();
     void init(int, int, int, int, char*);  
     int getbst();
     int getest();
     int getnst();
};

int wrdC::getbst() { 
  return bst;
}

int wrdC::getest() { 
  return est;
}

int wrdC::getnst() { 
  return nst;
}

wrdC::wrdC() {

}
void wrdC::init(int t_bst, int t_est, int t_nst, int t_wid, char *t_nm) {
   
   bst = t_bst;    
   est = t_est;
   nst = t_nst;
   wid = t_wid;
   strcpy(nm, t_nm);
}


hello
 i have the got the compilation error as

hmmword.h: In member function ‘void wrdC::init(int, int, int, int, char*)’:
hmmword.h:87:19: error: ‘strcpy’ was not declared in this scope

in the above program

please can anyone help me
thanks in advance

---

### Post by r-senior on 2013-02-27
Assuming you are trying to use strcpy from the C standard library, you need [FONT="Courier New"]#include <cstring>[/FONT] instead of [FONT="Courier New"]#include "cstring.h"[/FONT].

Generally speaking, [FONT="Courier New"]strncpy[/FONT] is safer than [FONT="Courier New"]strcpy[/FONT] because it places a limit on how many characters are copied, thereby avoiding buffer overflows.

Next time you post a question, please could you create your own thread and wrap code and console error messages in code tags to retain the formatting. There is a '#' button in the posting toolbar for this purpose, or you can type the tags by hand once you see what to do.

---

### Post by r-senior on 2013-02-27
> **knightsrv said:**
> ./geany_run_script.sh: 5: ./geany_run_script.sh: ./d: Permission denied
Are you creating this project in an unusual place, e.g. a USB drive or NTFS share?

Please also refer to comments in the previous post about creating new threads -- you can see the problem happening here when old threads are used for new questions.

---

### Post by Sef on 2013-02-27
Locked. Necromancing. 

If a post is more than a year old, then start a new thread and link to the old one.

---

