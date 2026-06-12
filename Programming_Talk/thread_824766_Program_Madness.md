---
title: "Program Madness"
date: 2008-06-10
forum: Programming Talk
---

### Post by spadewarrior on 2008-06-10
Hi all. I've been writing a program that asks the user to input names and exam results for 6 pupils. It goes quite wrong; after entering results for the second pupil it no longer prints out text properly, and eventually gives me a 'stack smashing detected' error. 



Additionally, the results are between 0-100% but the program won't accept 0. 

Here's the error:

```
*** stack smashing detected ***: ./exams terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7e5d138]
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x0)[0xb7e5d0f0]
./exams[0x804886e]
[0x3]
./exams[0x8048651]
======= Memory map: ========
08048000-08049000 r-xp 00000000 08:03 3080211    /home/sean/programming/c/exams
08049000-0804a000 rw-p 00000000 08:03 3080211    /home/sean/programming/c/exams
0804a000-0806b000 rw-p 0804a000 00:00 0          [heap]
b7d5f000-b7d69000 r-xp 00000000 08:02 798176     /lib/libgcc_s.so.1
b7d69000-b7d6a000 rw-p 0000a000 08:02 798176     /lib/libgcc_s.so.1
b7d6a000-b7d6b000 rw-p b7d6a000 00:00 0 
b7d6b000-b7d6d000 r-xp 00000000 08:02 864057     /lib/tls/i686/cmov/libdl-2.7.so
b7d6d000-b7d6f000 rw-p 00001000 08:02 864057     /lib/tls/i686/cmov/libdl-2.7.so
b7d6f000-b7d70000 rw-p b7d6f000 00:00 0 
b7d70000-b7eb9000 r-xp 00000000 08:02 864051     /lib/tls/i686/cmov/libc-2.7.so
b7eb9000-b7eba000 r--p 00149000 08:02 864051     /lib/tls/i686/cmov/libc-2.7.so
b7eba000-b7ebc000 rw-p 0014a000 08:02 864051     /lib/tls/i686/cmov/libc-2.7.so
b7ebc000-b7ebf000 rw-p b7ebc000 00:00 0 
b7ebf000-b7eec000 r-xp 00000000 08:02 798192     /lib/libncurses.so.5.6
b7eec000-b7eef000 rw-p 0002c000 08:02 798192     /lib/libncurses.so.5.6
b7f03000-b7f05000 rw-p b7f03000 00:00 0 
b7f05000-b7f06000 r-xp b7f05000 00:00 0          [vdso]
b7f06000-b7f20000 r-xp 00000000 08:02 798131     /lib/ld-2.7.so
b7f20000-b7f22000 rw-p 00019000 08:02 798131     /lib/ld-2.7.so
bfb2c000-bfb41000 rw-p bffeb000 00:00 0          [stack]
Aborted

```

and here's the program:

[PHP]#include <ncurses.h>
#include <string.h>
#include <stdlib.h>
#include <ctype.h>

int main(void)
{
	initscr();
	float average[6];
	char passFail[6][2];
	char student[6][31];
	char examStr[31];
	char *notInteger;
	int result[6][4];
	int count = 0;
	int exam, n = 1;
	
	for(n=1; n<7; n++) { //get names of students
		printw("\nPlease enter the name of student %i \n", n);
		refresh();
		getnstr(student[count], sizeof(student));
		for(exam=1; exam<4; exam++) { // for each student we ask to input the result of all 3 exams
			do{
				printw("Please enter the result of exam %i \n", exam);
				refresh();
				getnstr(examStr, sizeof(examStr)); 
				result[count][exam] = strtol(examStr, &notInteger, 10);
				fflush(stdout);
			} while(	(result[count][exam] < 0 || result[count][exam] >100)  || result[count][exam]=='\0'); 
		count++;
		}
		refresh();
	}
	
		
	endwin();
	return 0;
}
[/PHP]

Any suggestions? I thought that maybe I'm using ncurses or strtol() incorrectly but I can't work out how.

Thanks.

---

### Post by nvteighen on 2008-06-10
Er... Are you sure the algorithm is right? I get

1. Student name 1
2. Result exam 1
3. Result exam 2
4. Result exam 3
5. Result exam 3 (**again**)
6. (Eternally looping on exam 3...)

I'm going to take a look on it and see if I can help a little. (*EDIT* Ah! Each student has 3 done three exams...)

---

### Post by nvteighen on 2008-06-10
Ignore my last post. I misunderstood your code (so, it is intended to loop if you don't enter the right data).

Issues I could find:
0. strtol() returns a long integer, but you're storing it into an integer. Yes, they're the same in some architectures, but not in others. Use **atoi()**, which converts strings into integers (and is a way much simpler to use!) or transform "result" into a long int array.
1. Real programmers count from zero. Start your loops with n = 0, end with n < (whatever) and you'll save yourself from future headaches regarding lengths. When you're printing to screen, use **printw("Please enter the result of exam %i \n", exam + 1)**.
2. Is there a reason to use ncurses? In the current code's state, you could stick yourself with the standard library using printf() and friends.

If you still get the smashing error, compile your code with the -g flag and run it under gdb, so we see where the error is.

---

### Post by pmasiar on 2008-06-10
> **nvteighen said:**
> Real programmers count from zero.

... and smart beginners start with Python :-)

[php]
scores = {}
exams = []

exam = ''
print "Please eneter exams:"
while 1:
    exam = raw_input("enter exam, q when done: ")
    if exam == 'q':
        break
    if exam in exams:
        print exam, "already exists"
        continue
    exams.append(exam)
    
print "Please enter students:"
name = ''
while 1:
    name = raw_input('enter student name, q when done: ')
    if name == 'q':
        break
    if name in scores:
        print name, "already exists"
        continue
    if name in exams:
        print "that's exam name you joker!"
        continue
   
    scores[name] = {}
    for exam in exams:
        score = raw_input('enter score for %s in %s: ' % (name, exam))
    scores[name][exam] = score        
[/php]

I bet my version checks for more input errors :)

---

### Post by issih on 2008-06-10
```
#include <ncurses.h>
#include <string.h>
#include <stdlib.h>
#include <ctype.h>

int main(void)
{
    initscr();
    float average[6];
    char passFail[6][2];
    char student[6][31];
    char examStr[31];
    char *notInteger;
    int result[6][4];
    int count = 0;
    int exam, n = 1;
    
    for(n=1; n<7; n++) { //get names of students
        printw("\nPlease enter the name of student %i \n", n);
        refresh();
        getnstr(student[count], sizeof(student));
        for(exam=1; exam<4; exam++) { // for each student we ask to input the result of all 3 exams
            do{
                printw("Please enter the result of exam %i \n", exam);
                refresh();
                getnstr(examStr, sizeof(examStr)); 
                result[count][exam] = strtol(examStr, &notInteger, 10);
                fflush(stdout);
            } while(    (result[count][exam] < 0 || result[count][exam] >100)  || result[count][exam]=='\0'); 
        count++;
        }
        refresh();
    }
    
        
    endwin();
    return 0;
}  
```

Given I am a c++ rather than c person, so there are a few functions I am not entirely au fait with, I can see a few likely problems here.

The immediate cause of your first problem is the line:

   getnstr(student[count], sizeof(student));

here (I presume) you think you are reading 31 characters into the array pointed to by student[count]. Actually, as 'student' is the full array of 6*31 you are reading 186 characters. for the first student this works ok, as you have room from the first memory block pointed to by student[0] allocated. Once you cycle round to the second student however you start at student[1] which is 31 elements in, and trying to put in 186 elements flys past the end of the allocated memory for student.

   getnstr(student[count], 31);

or

   getnstr(student[count], sizeof(student[count]));

would probably sort that out.

You also allocate room for 4 results not 3 for each pupil, one of which you never allocate as your exam variable runs from 1 to 3 never entering into result[0][x].

As suggested above you would be much better off to get used to running loops from 0,e.g:

int array[n];
for(int i =0; i<n; i++)
{
    array[i] = i;
}

using 0 as the start point and ending at n-1 allows you to directly use the loop variable to access arrays of the same length. Its also just the normal way these things are done, and therefore good programming practice

Hope that helps

---

### Post by nvteighen on 2008-06-10
> **pmasiar said:**
> 
... and smart beginners start with Python :-)

You're essentially claiming I'm not a smart beginner!... Well, we both agree on that! ;)

Seriously talking, is there any other issue in the OP's code? (*EDIT* Too late, I see. Nice code, pmasiar)

---

### Post by Can+~ on 2008-06-10
> **pmasiar said:**
> ... and smart beginners start with Python :-)

[php]
scores = {}
exams = []

exam = ''
print "Please eneter exams:"
while 1:
    exam = raw_input("enter exam, q when done: ")
    if exam == 'q':
        break
    if exam in exams:
        print exam, "already exists"
        continue
    exams.append(exam)
    
print "Please enter students:"
name = ''
while 1:
    name = raw_input('enter student name, q when done: ')
    if name == 'q':
        break
    if name in scores:
        print name, "already exists"
        continue
    if name in exams:
        print "that's exam name you joker!"
        continue
   
    scores[name] = {}
    for exam in exams:
        score = raw_input('enter score for %s in %s: ' % (name, exam))
    scores[name][exam] = score        
[/php]

I bet my version checks for more input errors :)

Hmm.. that with sqlite3 could do a sweet database.

To the OP: The code itself, is quite hard to understand, besides the variable names and such, I don't know what exact algorithm you are trying to accomplish, are you requesting 3 exams from each student? Then why examstr is 31?

Also, this case is perfect for using a simple structure

[PHP]typedef struct {
	bool passed;
	unsigned char name[30];
	unsigned char exams[3]; // If it is between 0 and 100, a char fits better, right?
	float average;
}student;[/PHP]

(And bool requires stdbool.h, in C++ this is already included)

---

### Post by pmasiar on 2008-06-10
> **Can+~ said:**
> Hmm.. that with sqlite3 could do a sweet database.

Even simpler: you can just pickle exams and scores :-)

---

### Post by spadewarrior on 2008-06-10
Wow, lots of replies!

Firstly, sorry I wasn't very clear. I've been programming about a month and need to comment my code properly...

issih - Thanks for pointing that out. I've adjusted my code. Unfortunately I still have the problem with the program stopping displaying text after student 2, and '0' is still not allowed as a result. Thankfully the crash has stopped.

nvteighen - I'm using ncurses because I need to display the text in a certain way after I've got it working. 



Thanks for all the help so far!

 

And here's the altered code:

[PHP]#include <ncurses.h>
#include <string.h>
#include <stdlib.h>
#include <ctype.h>

int main(void)
{
	initscr();
	float average[6];
	char passFail[6][2];
	char student[6][31];
	char examStr[31];
	//char *notInteger;
	int result[6][4];
	int count = 0;
	int exam, n;
	
	for(n=0; n<6; n++) { //get names of students
		printw("\nPlease enter the name of student %i \n", n+1);
		refresh();
		//getnstr(student[count], sizeof(student)); [this doesn't work]
		getnstr(student[count], sizeof(student[count]));
		for(exam=0; exam<3; exam++) { // for each student we ask to input the result of all 3 exams
			do{
				printw("Please enter the result of exam %i \n", exam+1);
				refresh();
				getnstr(examStr, sizeof(examStr)); 
				//result[count][exam] = strtol(examStr, &notInteger, 10);
				result[count][exam] = atoi(examStr);
				//fflush(stdout);
			} while(	(result[count][exam] < 0 || result[count][exam] >100)  || result[count][exam]=='\0'); 
		count++;
		}
		refresh();
	}
	
	endwin();
	return 0;
}
[/PHP]

---

### Post by issih on 2008-06-10
I think I can tell you why you can't enter 0 as an answer. I think this line is the problem:

```
while(    (result[count][exam] < 0 || result[count][exam] >100)  || result[count][exam]=='\0');
```
The array result is typed as an int, and almost certainly initialises to a lot of 0's, as you never initialise it explicitly.

You then try and compare it to '/0' which is clearly a character (I'm guessing NULL). The only way this can be done is if the compiler performs an implicit conversion from the character to an int, which I'm assuming converts NULL to 0, and therefore makes 0 an invalid entry.

I'm guessing a fair bit here, but I'd be surprised if I was wrong.

You need to initialise the results array to a value out of the valid range early on with something like:

```
for(int i = 0;i<6;i++)
{
   for(int j=0;j<3;j++)
   {
       result[i][j] = 1000;
   }
}

```

and remove the final coomparison in the offending while loop.

Not sure why the output is stopping, but I've never programmed for ncurses, I'd start by doing it with simple standard out commands, to ensure the design pattern works then migrate over to ncurses.

I would also comment that the suggestion to use a struct is very sensible, and would potentially make things much neater, but then I would say that,I like objects :)

---

### Post by thornmastr on 2008-06-10
"Firstly, sorry I wasn't very clear. I've been programming about a month and need to comment my code properly...

issih - Thanks for pointing that out. I've adjusted my code. Unfortunately I still have the problem with the program stopping displaying text after student 2, and '0' is still not allowed as a result. Thankfully the crash has stopped.

nvteighen - I'm using ncurses because I need to display the text in a certain way after I've got it working. "

Obviously, this problem has a number of requirements we do not know. Would you mind posting the problem as it was given to you so we can give you a viable solution?

---

### Post by spadewarrior on 2008-06-10
issih - 


You're absolutely correct. I've now declared the array results[][]. I was using strtol() to make sure only numbers were being input. I thought about using isnum() but couldn't get it to work. I'm now thinking of using sscanf() for this. Is there anything I should know?

I've also just ditched ncurses for now. It seems to have helped with the erractic behaviour. Hopefully someone else can spot what is going wrong in the code.

thornmastr - 

I basically need to use ncurses to print the information in a table-like manner, i.e. student on y axis, exams across x. That's the only reason for using it.

---

