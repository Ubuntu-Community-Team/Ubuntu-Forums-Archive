---
title: "[newbie][c]how can i create a program that reads text"
date: 2008-08-23
forum: Programming Talk
---

### Post by cmay on 2008-08-23
hi.
i wonder if its possible to write a program that reads text from the terminal using espeak or some ting like that.
i have written a small program sometime ago that prints one line at a time to the terminal whit that in in mind as a prototype.
also just for the sake of doing something.
its for my own personal use.
i dont see that good anymore so sometimes 
it would be helpful to have something like that.
i have not been able to figure out if e-speak already can do that and if so then i really dont need such program for anything other than practice.

which of course is also a good thing:)
 
here is the program so far.

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
char *progname;
int main(int argc,char **argv){
    char c;
    FILE *fp;
    if(argc != 2){
    printf("%s usage:[argc 1] [file]\n[argc 1]options [--help]\n",progname);
    exit(1);
    }

   if(strcmp(argv[1],"--help")==0){
   printf("usage : print text file one line at the time whit slight delay\n");
   printf("AUTHOR:cmay 2008\nlicense: GPL\n");
   exit(0);
   }
      if((fp=fopen(argv[1],"r"))!= NULL){
   	  while((c=getc(fp))!=EOF){
           if(c=='\n'){
           	system("sleep 1");
		    }
   	  printf("%c",c);
      }
   	  fclose(fp);
   	 }
     else {printf("c:> bad command or filename\n");
        system("sleep 1 && clear");
        printf("sorry %s dumb joke\n",getenv("USERNAME")); 
     }
     
   exit(0);
}
```

---

### Post by dribeas on 2008-08-23
> **cmay said:**
> i have not been able to figure out if e-speak already can do that and if so then i really dont need such program for anything other than practice.

I believe espeak can do it. You can use --stdin as an option and that will read the text from stdin:

```
$ echo "Hi, how are you doing?" | espeak --stdin
```

Or you can provide a file with -f:

```
$ espeak -f text_to_read.txt
```

If you wanted to manually feed text to espeak one line at a time then, instead of writing to the terminal and waiting for a fixed 1 second period, I would construct a string with the line preceded by 'espeak ' and then use system with that command. This will guarantee that the whole line is read before trying to read the next one.

   David

---

### Post by cmay on 2008-08-23
thanks.
i have the idea of just creating a sort of file to read selector so
whit this information as you posted i can try it out.
i have just not find out what e-speak can or cant since i get periods where i cant see and then when i can see i forget about these things.:oops:
i will try to play a little around whit this  see if i can get something useful out of it.other than that its also a good practice. thanks a lot:)

---

