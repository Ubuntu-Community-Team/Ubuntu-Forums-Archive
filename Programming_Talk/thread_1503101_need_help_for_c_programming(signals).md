---
title: "need help for c programming(signals)"
date: 2010-06-06
forum: Programming Talk
---

### Post by amite on 2010-06-06
**c programmming help.....**             
                                                                > 
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <signal.h>

main()
{
             if(fork()==0) //IF CHILD
            {
                     char ch;
            while(1)
                    {
                 ch=rand();
                              printf("%c ",ch);
                      }
        }
          else   //PARENT PROCESS
          {
                    if(getchar()==27)
                               signal(SIGINT,SIG_DFL);
          }
}
I am learning c programming.My requirement is after executing this program terminal give random char to stdout and when i press esc then it stop.So i start a child to give output random characters and parent process wait for esc character.after pressing esc parent send kill -9 signal to terminate it self and so child also terminated.

Before using SIGKILL i tried SIGCHLD to terminate child and after that parent terminate normally.but both doesn't working,after executing the process i have to use ctrl+c to stop the process.

**I want to just know why is it not working,where  is wrong in my approach?**
if any one have also other approach to solve the sameproblem please suggest me....

Thanks..:smile:

---

### Post by rnerwein on 2010-06-06
hi 
first start with the logic of spawn a process and signals.
just a little explanation:
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <signal.h>

main()
{
pid_t i_child;

    switch(i_child = fork())  {
        case 0: /* i'am the child */
            fprintf(stderr,"hey father you have to pay\n");
            exit(0); /* don't forget the exit or child and father run
                        the same procedure later */
            break; /* only for the compiler --> never reached */

        case -1:  /* something wrong - e.g. no space, to many processes ?*/
            exit(1);
            break;

        default: /* hey i'am father */
            fprintf(stderr,"let's have a party !!!!!\n");
            break;
    }
exit(0);
}

---

### Post by amite on 2010-06-06
I don't understand what do u want to clarify.........i think u r just giving me another way of implementing fork() process....but my concern : why when input esc parent doesn't execute signal() while they should run parallel.(I think here i m smthng wrong but i don't know what happens exactly after fork())
> 
case 0: /* i'am the child */
            fprintf(stderr,"hey father you have to pay\n");
            exit(0); /* don't forget the exit or child and father run
                        the same procedure later */


here in my program child is executing an infinite loop,so how will it come out of infinite loop?

---

### Post by gmargo on 2010-06-06
Read The Fine Man pages!  Your "signal(2)" call does nothing - it sets the signal handler to the default, where it already is.  If you want to kill the child, you must use the kill(2) system call.

System call **signal(2)** is used to designate a signal handler.

System call **kill(2)** is used to send a signal to yourself or to another process.

---

### Post by MadCow108 on 2010-06-06
you can't just print and expect the output to go into stdin of another process (fork spawns a new process).

you will have to use some kind of interprocedual communication like pipes, messages queues, sockets, shared memory etc...
here's an overview:
[http://beej.us/guide/bgipc/output/html/multipage/index.html](http://beej.us/guide/bgipc/output/html/multipage/index.html)

---

### Post by gmargo on 2010-06-06
Here is a small revision of your code, that might help make things clearer.

```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <signal.h>

char * me = "Parent";

void sigkill(int signum)
{
    printf("=== %s EXIT SIGNAL %d ===\n", me, signum);
    exit(0);
}

main()
{
    int pid = fork();
    signal(SIGINT, sigkill);
    signal(SIGQUIT, sigkill);
    signal(SIGTERM, sigkill);
    if(pid == 0) //IF CHILD
    {  
        int ch;
        me = "Child";
        while(1)
        {  
            ch = (rand() % 26) + 'A';   // limit range to ascii A-Z
            printf("%c",ch);
            fflush(stdout); // flush output buffer
            sleep(2);   // don't overwhelm
            if (1 == getppid())
            {  
                printf("=== CHILD EXIT SINCE PARENT DIED ===\n");
                exit(0);
            }
        }
        printf("==CHILD EXIT NORMAL==\n");
    }
    else //PARENT PROCESS
    {  
        int ch;
        if((ch = getchar())==27)
            kill(pid, SIGINT);
        printf("==PARENT EXIT NORMAL (ch=%d)==\n", ch);
    }
    return(0);
}

```

---

### Post by dwhitney67 on 2010-06-06
gmargo, a few things about the app you posted:

1.  The main() function should be declared to return an int

2.  Because getchar() is a blocking function, it will not return back any data until the user presses the "return" key.  Thus even with the pressing of the "Esc" key, the program will not terminate until the "return" key is pressed.  The stdin stream can be setup to be non-blocking, thus mitigating the need to wait for the newline.

3.  The random generator has not been seeded; prior to the first usage of rand(), srand() must be called preferably with a large number.  The current time in seconds since the Linux epoch is a typical choice for this number.

For number 2 above, the stdin can be setup to be non-blocking using the following:
```

#include <termios.h>
#include <unistd.h>
#include <string.h>

// For yesOrNo, 1 is to enable non-blocking, 0 to disable (ie blocking).
int enableNonBlocking(int yesOrNo, int fileno)
{
   static struct termios old;

   if (yesOrNo)
   {
      struct termios tmp;

      if (tcgetattr(fileno, &old))
      {
         return -1;
      }

      memcpy(&tmp, &old, sizeof(old));

      tmp.c_lflag &= ~ICANON & ~ECHO;

      if (tcsetattr(fileno, TCSANOW, (const struct termios*) &tmp))
      {
         return -1;
      }
  }
  else
  {
     tcsetattr(fileno, TCSANOW, (const struct termios*) &old);
  }

  return 0;
}

```
In the main() function, it would be called in the parent process.
```

int main(void)
{
   ...

   if (pid == 0)
   {
      /* child */
      srand(time(0));

      ...
   }
   else
   {
      /* parent */
      enableNonBlocking(1, STDIN_FILENO);

      int ch;
      do
      {
        if((ch = getchar())==27)
            kill(pid, SIGINT);
      } while (ch != 27);

      enableNonBlocking(0, STDIN_FILENO);
   }

   ...
}

```

---

### Post by amite on 2010-06-06
Thank  all of u.....

Now I need some suggestion.I want to make my contribution to open sources and make my on system(modifications).But I can't find proper guidance ,so if u guys can suggest me what to read then it would be great for me.
I read The c Programming language(Danies Ritchie),I am reading Operating system(A.Tanenbaum) and learning shell scripting(Wiley Linux command line and shell scripting).But find some c prog. concepts which i didn't find in ritchie's book and such other things which i don't know where can i find.
whatever term come across me i google up and learn but it's not very fruitful unless i get some initial direction.So please suggest me where should i start?
what should a linux system admin. (not for enterprises) must know or say to maintain my system properly what are the topics which i must learn....

It may seems weird but whatever i learned,i learned here.........i haven't attend any classes at all for these .

---

