---
title: "gdb issues no such file or directory"
date: 2011-09-30
forum: Programming Talk
---

### Post by bedroomCod3r on 2011-09-30
Hi,

I'm having a problem regarding gdb. The gdb keeps on displaying no such file or directory every time I use step command in printf();. This surprise me because I don't have this problem on my previous installation (lucid).  I don't know whats going on. 

Below is the log of the session.

```

******@g****:~/programs/any$ gdb ./myprg

 GNU gdb (GDB) 7.1-ubuntu

 Copyright (C) 2010 Free Software Foundation, Inc.

 License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>

 This is free software: you are free to change and redistribute it.

 There is NO WARRANTY, to the extent permitted by law.  Type "show copying" and "show warranty" for details.

 This GDB was configured as "i486-linux-gnu". 
For bug reporting instructions, please see: 
<http://www.gnu.org/software/gdb/bugs/>... 
Reading symbols from /home/carl/programs/any/myprg...done. 
(gdb) list 
1	/* This simple program purpose is to test the debugger */ 
2	#include <stdio.h> 
3	#define MAX 32 
4	int main() 
5	{ 
6	  int num = 0; 
7	  int i, ch; 
8	  char name[MAX]; 
9	 
10	  printf("%s", "Enter String here: "); 
(gdb)  
11	  for(i = 0;(ch = getchar()) != '\n' && i < 32;++i) 
12	      name[i] = ch; 
13	  name[i] = '\0'; 
14	 
15	  printf("%s", "Enter number: "); 
16	  scanf("%d", &num); 
17	 
18	  printf("%s%s\n", "Your name is ", name); 
19	  printf("%s%d\n", "Your inputed number is ", num); 
20	 
(gdb)  
21	 return 0; 
22	} 
(gdb) break 10 
Breakpoint 1 at 0x80484c1: file myprg.c, line 10. 
(gdb) run 
Starting program: /home/****/programs/any/myprg  

Breakpoint 1, main () at myprg.c:10 
10	  printf("%s", "Enter String here: "); 
(gdb) step 
__printf (format=0x8048650 "%s") at printf.c:29 
29	**printf.c: No such file or directory.** 
	in printf.c 
(gdb) q 
A debugging session is active. 

	Inferior 1 [process 1948] will be killed.  
Quit anyway? (y or n) y 
***@****:~/programs/any$

```

 
Tried some simple troubleshooting by adding -d flag but no luck 


```

****@*****:~/programs/any$ gdb -d /usr/include/ ./myprg 
GNU gdb (GDB) 7.1-ubuntu 
Copyright (C) 2010 Free Software Foundation, Inc. 
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html> 
This is free software: you are free to change and redistribute it. 
There is NO WARRANTY, to the extent permitted by law.  Type "show copying" 
and "show warranty" for details. 
This GDB was configured as "i486-linux-gnu". 
For bug reporting instructions, please see: 
<http://www.gnu.org/software/gdb/bugs/>... 
Reading symbols from /home/****/programs/any/myprg...done. 
(gdb) list 
1	/* This simple program purpose is to test the debugger */ 
2	#include <stdio.h> 
3	#define MAX 32 
4	int main() 
5	{ 
6	  int num = 0; 
7	  int i, ch; 
8	  char name[MAX]; 
9	 
10	  printf("%s", "Enter String here: "); 
(gdb)  
11	  for(i = 0;(ch = getchar()) != '\n' && i < 32;++i) 
12	      name[i] = ch; 
13	  name[i] = '\0'; 
14	 
15	  printf("%s", "Enter number: "); 
16	  scanf("%d", &num); 
17	 
18	  printf("%s%s\n", "Your name is ", name); 
19	  printf("%s%d\n", "Your inputed number is ", num); 
20	 
(gdb)  
21	 return 0; 
22	} 
(gdb) break 10 
Breakpoint 1 at 0x80484c1: file myprg.c, line 10. 
(gdb) step 
The program is not being run. 
(gdb) run 
Starting program: /home/***/programs/any/myprg  

Breakpoint 1, main () at myprg.c:10 
10	  printf("%s", "Enter String here: "); 
(gdb) step 
__printf (format=0x8048650 "%s") at printf.c:29 
29	**printf.c: No such file or directory.** 
	in printf.c 
(gdb) q 
A debugging session is active. 

	Inferior 1 [process 2128] will be killed. 

Quit anyway? (y or n) y 
*****@*****:~/programs/any$

```

Need your guidance, 

Thank you

---

### Post by karlson on 2011-09-30
> **bedroomCod3r said:**
> Hi,

I'm having a problem regarding gdb. The gdb keeps on displaying no such file or directory every time I use step command in printf();. This surprise me because I don't have this problem on my previous installation (lucid).  I don't know whats going on. 

Below is the log of the session.

******@g****:~/programs/any$ gdb ./myprg

 GNU gdb (GDB) 7.1-ubuntu

 Copyright (C) 2010 Free Software Foundation, Inc.

 License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>

 This is free software: you are free to change and redistribute it.

 There is NO WARRANTY, to the extent permitted by law.  Type "show copying" and "show warranty" for details.

 This GDB was configured as "i486-linux-gnu". 
For bug reporting instructions, please see: 
<http://www.gnu.org/software/gdb/bugs/>... 
Reading symbols from /home/carl/programs/any/myprg...done. 
(gdb) list 
1	/* This simple program purpose is to test the debugger */ 
2	#include <stdio.h> 
3	#define MAX 32 
4	int main() 
5	{ 
6	  int num = 0; 
7	  int i, ch; 
8	  char name[MAX]; 
9	 
10	  printf("%s", "Enter String here: "); 
(gdb)  
11	  for(i = 0;(ch = getchar()) != '\n' && i < 32;++i) 
12	      name[i] = ch; 
13	  name[i] = '\0'; 
14	 
15	  printf("%s", "Enter number: "); 
16	  scanf("%d", &num); 
17	 
18	  printf("%s%s\n", "Your name is ", name); 
19	  printf("%s%d\n", "Your inputed number is ", num); 
20	 
(gdb)  
21	 return 0; 
22	} 
(gdb) break 10 
Breakpoint 1 at 0x80484c1: file myprg.c, line 10. 
(gdb) run 
Starting program: /home/****/programs/any/myprg  

Breakpoint 1, main () at myprg.c:10 
10	  printf("%s", "Enter String here: "); 
(gdb) step 
__printf (format=0x8048650 "%s") at printf.c:29 
29	**printf.c: No such file or directory.** 
	in printf.c 
(gdb) q 
A debugging session is active. 

	Inferior 1 [process 1948] will be killed.  
Quit anyway? (y or n) y 
***@****:~/programs/any$


 
Tried some simple troubleshooting by adding -d flag but no luck 



****@*****:~/programs/any$ gdb -d /usr/include/ ./myprg 
GNU gdb (GDB) 7.1-ubuntu 
Copyright (C) 2010 Free Software Foundation, Inc. 
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html> 
This is free software: you are free to change and redistribute it. 
There is NO WARRANTY, to the extent permitted by law.  Type "show copying" 
and "show warranty" for details. 
This GDB was configured as "i486-linux-gnu". 
For bug reporting instructions, please see: 
<http://www.gnu.org/software/gdb/bugs/>... 
Reading symbols from /home/****/programs/any/myprg...done. 
(gdb) list 
1	/* This simple program purpose is to test the debugger */ 
2	#include <stdio.h> 
3	#define MAX 32 
4	int main() 
5	{ 
6	  int num = 0; 
7	  int i, ch; 
8	  char name[MAX]; 
9	 
10	  printf("%s", "Enter String here: "); 
(gdb)  
11	  for(i = 0;(ch = getchar()) != '\n' && i < 32;++i) 
12	      name[i] = ch; 
13	  name[i] = '\0'; 
14	 
15	  printf("%s", "Enter number: "); 
16	  scanf("%d", &num); 
17	 
18	  printf("%s%s\n", "Your name is ", name); 
19	  printf("%s%d\n", "Your inputed number is ", num); 
20	 
(gdb)  
21	 return 0; 
22	} 
(gdb) break 10 
Breakpoint 1 at 0x80484c1: file myprg.c, line 10. 
(gdb) step 
The program is not being run. 
(gdb) run 
Starting program: /home/***/programs/any/myprg  

Breakpoint 1, main () at myprg.c:10 
10	  printf("%s", "Enter String here: "); 
(gdb) step 
__printf (format=0x8048650 "%s") at printf.c:29 
29	**printf.c: No such file or directory.** 
	in printf.c 
(gdb) q 
A debugging session is active. 

	Inferior 1 [process 2128] will be killed. 

Quit anyway? (y or n) y 
*****@*****:~/programs/any$


Need your guidance, 

Thank you

First off when you post code use code tags.

2.  Do you have debug versions of glibc and source of glibc installed so that gdb can actually go through the source.  
3.  Why do you want to step through printf?
4.  Why do printf("%s", <string>)?  While there is nothing wrong with that statement I don't see any reason not to do printf("<string>");

---

### Post by bedroomCod3r on 2011-10-01
> **karlson said:**
> First off when you post code use code tags.

2.  Do you have debug versions of glibc and source of glibc installed so that gdb can actually go through the source.  
3.  Why do you want to step through printf?
4.  Why do printf("%s", <string>)?  While there is nothing wrong with that statement I don't see any reason not to do printf("<string>");

First off when you post code use code tags.
Whoops My mistake...

 2.  Do you have debug versions of glibc and source of glibc installed so that gdb can actually go through the source.

   I'll Check that.. I'm using an offline linux. 

 3. Why do you want to step through printf?
      You mean I'll use a next command instead of step?

4.  Why do printf("%s", <string>)?  While there is nothing wrong  with that statement I    don't see any reason not to do  printf("<string>");
 
    I agree, there's nothing wrong with printf("<string>");. I was using a book by Ira Pohl ABC. A lot of examples are also in printf("%s", <string>); format. I get used of using printf("%s", <string>); format. In any case Im going to try your suggestion. 

Thank You for replying

---

### Post by karlson on 2011-10-01
> **bedroomCod3r said:**
> 
      You mean I'll use a next command instead of step?

Right.

---

### Post by Arndt on 2011-10-01
> **karlson said:**
> Right.

'step' used to do the right thing, though.

---

### Post by karlson on 2011-10-01
> **Arndt said:**
> 'step' used to do the right thing, though.

If the debug version and the source code are installed I am sure it will.  I just don't see a reason to do this unless you are actually trying to debug the printf function.

---

### Post by Arndt on 2011-10-02
> **karlson said:**
> If the debug version and the source code are installed I am sure it will.  I just don't see a reason to do this unless you are actually trying to debug the printf function.

What is felt to be the right thing can depend on what you're used to, but letting 'step' go into libc code when you don't have the source code to libc is not useful.

---

### Post by bedroomCod3r on 2011-10-04
Thank you Karlson for pointing it out. I tried using the next command and the errors are gone except for the last part.
```


****@****:~/programs/any$ gdb ./prg2

GNU gdb (GDB) 7.1-ubuntu 
Copyright (C) 2010 Free Software Foundation, Inc. 
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html> 
This is free software: you are free to change and redistribute it. 
There is NO WARRANTY, to the extent permitted by law.  Type "show copying" 
and "show warranty" for details. 
This GDB was configured as "i486-linux-gnu". 
For bug reporting instructions, please see: 
<http://www.gnu.org/software/gdb/bugs/>... 
Reading symbols from /home/carl/programs/any/prg2...done. 
(gdb) list 
1    /* This simple program purpose is to test the debugger */ 
2    #include <stdio.h> 
3    #define MAX 32 
4    int main() 
5    { 
6      int num = 0; 
7      int i, ch; 
8      char name[MAX]; 
9     
10      printf("Enter String here: "); 
(gdb)  
11      for(i = 0;(ch = getchar()) != '\n' && i < 32;++i) 
12          name[i] = ch; 
13      name[i] = '\0'; 
14     
15      printf("Enter number: "); 
16      scanf("%d", &num); 
17     
18      printf("Your name is %s\n", name); 
19      printf("Your inputed number is %d\n", num); 
20     
(gdb)  
21     return 0; 
22    } 
(gdb) break 11 
Breakpoint 1 at 0x80484ce: file myprg2.c, line 11. 
(gdb) run 
Starting program: /home/carl/programs/any/prg2  

Breakpoint 1, main () at myprg2.c:11 
11      for(i = 0;(ch = getchar()) != '\n' && i < 32;++i) 
(gdb) next 
Enter String here: two 
12          name[i] = ch; 
(gdb)  
11      for(i = 0;(ch = getchar()) != '\n' && i < 32;++i) 
(gdb)  
12          name[i] = ch; 
(gdb)  
11      for(i = 0;(ch = getchar()) != '\n' && i < 32;++i) 
(gdb)  
12          name[i] = ch; 
(gdb)  
11      for(i = 0;(ch = getchar()) != '\n' && i < 32;++i) 
(gdb)  
13      name[i] = '\0'; 
(gdb)  
15      printf("Enter number: "); 
(gdb)  
16      scanf("%d", &num); 
(gdb)  
Enter number: 2222 
18      printf("Your name is %s\n", name); 
(gdb)  
Your name is two 
19      printf("Your inputed number is %d\n", num); 
(gdb)  
Your inputed number is 2222 
21     return 0; 
(gdb)  
22    } 
(gdb)  
_[B]_libc_start_main (main=0x80484a4 <main>, argc=1, ubp_av=0xbffff4e4, init=0x8048580 <__libc_csu_init>, fini=0x8048570 <__libc_csu_fini>,  
    rtld_fini=0x11e030 <_dl_fini>, stack_end=0xbffff4dc) at libc-start.c:258 
258    libc-start.c: No such file or directory. 
    in libc-start.c[/B] 
(gdb)  

Program exited normally. 
(gdb) q 
****@*****:~/programs/any$  

```So to remove the last error installing libc would do the job right?

---

### Post by karlson on 2011-10-04
> **bedroomCod3r said:**
> Thank you Karlson for pointing it out. I tried using the next command and the errors are gone except for the last part.
```


(gdb)  
_[B]_libc_start_main (main=0x80484a4 <main>, argc=1, ubp_av=0xbffff4e4, init=0x8048580 <__libc_csu_init>, fini=0x8048570 <__libc_csu_fini>,  
    rtld_fini=0x11e030 <_dl_fini>, stack_end=0xbffff4dc) at libc-start.c:258 
258    libc-start.c: No such file or directory. 
    in libc-start.c[/B] 
(gdb)  

Program exited normally. 
(gdb) q 
****@*****:~/programs/any$  

```So to remove the last error installing libc would do the job right?

I would suggest running continue at the return statement.  What you see is not really an error for me.

---

