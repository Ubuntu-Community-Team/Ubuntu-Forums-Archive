---
title: "C Programming and libraries"
date: 2007-04-29
forum: Programming Talk
---

### Post by Zacharias on 2007-04-29
hi guys

i am trying to code in c, but i have a small problem about libraries such conio.h windows.h etc. 

when i write Sleep(1000) it doesnt work.

the question is how can i add more libraries and where can i find. 

i am using 7.04

---

### Post by moma on 2007-04-29
Show your code.
Create [COLOR="Red"]a small example[/COLOR] of your code and paste it here.

---

### Post by Zacharias on 2007-04-29
```


#include<stdio .h>
#include<stdlib .h>
#include<time .h>
#include<conio .h>
int main() {
int x,y,newgame=1;   
     while(newgame==1) {
             srand(time(NULL));
             x=1+rand()%100;
             system("cls");
             printf("Bir sayi giriniz\n");
             scanf("%d",&y);
             while(x!=y) {
                        if(y<x ) {
                                printf("Dusuk\n");
                                printf("Yeniden Deneyin\n");
                                scanf("%d",&y); }
                        if(y>x) {
                                printf("Yuksek\n");
                                printf("Yeniden Deneyin\n");
                                scanf("%d",&y);
                                  }
                             }
                        if(x==y)
                               printf("Tebrikler!!!\n");
                               printf("1 yeni oyun, 0 cikis\n");
                               scanf("%d",&newgame);
                               }
getche();
return 0;
}



```

here conio.h etc is not working thats why i couldnt compile the codes. however ion windows and in devc++ it is working

---

### Post by moma on 2007-04-29
```
#include<stdio.h>
#include<stdlib.h>
#include<time.h>
/*  #include<conio .h>   */ 

conio.h is DOS spesific. Unix/Linux does not have it.

             srand(time(NULL));
             x=1+rand()%100;

             /* system("cls");  */
cls is a DOS command, however you can try 
            system("clear");
 
           /* getche();   */
getche is also DOS spesific.  But you can almost do the same with getchar(). You must press [Return] key to continue.  See the note_1 below.
          getchar();
```
-------------------------------------------------------------

This is how to compile your code.
Simple way:
$  gcc  program.c -o program

Run it
$ ./program 
--------------------------

More elaborated (also correct and complex ) way:
[COLOR="RoyalBlue"]Compile first[/COLOR]
$ gcc -c program.c   
# it creates object file program.o.

Then [COLOR="RoyalBlue"]link[/COLOR] it (you do not need any external link libraries in this case )
$ gcc program.o -o program
# It takes object file and links it with runtime system. The result is the "program" executable.

Run it
$ ./program
----------------------------------------

Note_1: "ncurses" is the library that allows you to create DOS alike GUI programs in Unix/Linux. It has also a proper getch() function. 
Study: [http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/](http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/)   

See also:
[http://users.actcom.co.il/%7Echoo/lupg/tutorials/index.html](http://users.actcom.co.il/%7Echoo/lupg/tutorials/index.html)   (especially chapter 1.1 and 1.3 )
+
[http://www2.its.strath.ac.uk/courses/c/](http://www2.its.strath.ac.uk/courses/c/)
Note: Both guides uses cc as the compiler command. You can replace it with gcc.
-----------------------------------------

BTW: [This is how to....]("http://ubuntuforums.org/showthread.php?p=1962696#post1962696") install Code::Blocks IDE on Ubuntu 6.x / 7.x

---

