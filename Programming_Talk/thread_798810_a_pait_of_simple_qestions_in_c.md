---
title: "a pait of simple qestions in c"
date: 2008-05-18
forum: Programming Talk
---

### Post by cmay on 2008-05-18
hi .
i have been learning c from some books i got cheap since they are for educational purpose and outdated a bit. i have followed some tutorials on the net also like c made easy .a pointer tutorial from gamedev.com and the one in the sticky treadh .
 my qestion is now that i am in the chapter where the books give two simple samples for filehandling assuming there will be a teacher in a classroom that can explain this more in depht which i do not have.
i just wanna learn this one language for personal reasons and nothing else so i dont take classes or anything like that. i am not gonna use it for anything other than just understanding my computer a bit better .
 when i try use the funktions atoi and the close <file> i get a warning about the funktion being implicit declared.
 mostly these warnings is from me mispelling the #include <stdio.h> but as i go along whit these books i start to run into samples that do not compile and i know i think that i  spell it right.
is there any special considerations for file handlings in linux envoriment that may have something to do whit this.
i know this must be a newbie qestion and i have also just used 3 weeks on this c programmering. anyway i will be very happy for any help understanding what i do wrong  i have completed the lessons on the danish c programmering tutorials i could find i want to use books in my own language if i can but still if anyone got some links to c programmering tutorials other than the ones i mentioned i will be very happy also.

thanks for reading this.

---

### Post by LaRoza on 2008-05-18
Make sure you have build-essential installed:

```

sudo aptitude install build-essential

```

```

#include <stdio.h>

int main(int argc,char ** argv)
{
    FILE * toopen = fopen("hw","w");
    fputs("Hello world\n",toopen);
    fclose(toopen);
} 

```

Compile and run this, it should create a file named "hw" and print the words "Hello world" to it with no warnings or errors.

---

### Post by cmay on 2008-05-18
hi 
thanks for the reply.
i have installed build-essential and i use geany.
the program samples i compile works mostly fine exept some of the more interesting examples like file handling.
 as the examples from the book mostly  is some like  while((c=getchar())!=EOF) stuff and i have to use the cat command to get the results the books are written  for a specifik educational purpose and use dos type command not unix commands but the author promised that it should be strict ansi c compliant and work on linux unix just as good. 
i know i have some thing missing somewhere since the most samples works good .
 its just that i cant find out whats wrong from two short samples showing how to open a file called test.txt and close a file whit hello in test.txt. 
all the array and struct samples works great however.

thanks you for the answer.

---

### Post by LaRoza on 2008-05-18
> **cmay said:**
> hi 
thanks for the reply.
i have installed build-essential and i use geany.
the program samples i compile works mostly fine exept some of the more interesting examples like file handling.
 as the examples from the book mostly  is some like  while((c=getchar())!=EOF) stuff and i have to use the cat command to get the results the books are written  for a specifik educational purpose and use dos type command not unix commands but the author promised that it should be strict ansi c compliant and work on linux unix just as good. 
i know i have some thing missing somewhere since the most samples works good .
 its just that i cant find out whats wrong from two short samples showing how to open a file called test.txt and close a file whit hello in test.txt. 
all the array and struct samples works great however.

thanks you for the answer.
Could you post the code?

---

### Post by cmay on 2008-05-18
hi 
all i got out this code you posted is that you are way better teacher than the book is :)
 it works fine whit this.
i can post the code from the book if you want but i have to just copy it from my other machine on to a usb stick to get to my computer that is connected to the internet. i use my very old computer to learn programmering on . just in case i do a bad interupt example and blow it up some day. 

can you wait say half hour or so  ?.
by the way laroza i recently tried to get registered whit your programmering
forum and i cant get in whit the passwords and i nerver had any registering comfirm email or anything. its bugging me a bit but i think if you dont want a user on the forum that dont parcipitate  you could simply delete me. i think my email provider has blocked the registration notification. this stuff happens a lot to me sorry being of topic but it just came to mind.

any way thanks a lot

---

### Post by cmay on 2008-05-18
the code exactly as from the book.
 
#include <stdio.h>
int main(char *s[])
{
int i=0;
char fil[]="test.txt";
FILE *fp;
if((fp=fopen(fil,"w"))!=NULL)
{
while(fil[i])
putc(fil[i++],fp);
close(fil);
}
return 0;
}

sample output from compiler log  there are lots of warnings its just this one that is the most frequent one.
test.c:11: advarsel: implicit declaration of function ‘close’

thanks for the help.

---

### Post by dwhitney67 on 2008-05-18
Here's your code, pretty formatted for easier reading.  You should attempt to code in a way that makes it easier for both you and others to read.

Btw, your warning was due to the fact that you were using close().  That is defined in unistd.h.  What it more appropriate to use is fclose() -- essentially the complement function of fopen().

[PHP]#include <stdio.h>     // for fopen(), fclose()

int main( int argc, char **argv )
{
  int   i   = 0;
  char *fil = "test.txt";
  FILE *fp  = fopen( fil, "w" );

  if ( fp != NULL )
  {
    while ( fil[i] )
    {
      putc( fil[i++], fp );
    }

    fclose( fp );
  }

  return 0;
}[/PHP]

---

### Post by cmay on 2008-05-18
sorry,thanks

---

