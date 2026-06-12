---
title: "fprintf(stdin,&quot;hello, standard input&quot;,21) ??"
date: 2008-10-01
forum: Programming Talk
---

### Post by kcode on 2008-10-01
fprintf prints out data to a stream (FILE *)
if i make stream stdout, data will be displayed to standard output. while playing with this function, when i made stream stdin is standard input (which is keyboard (always??)), i was expecting some error, but actually nothing happened.
So what happened??
(pardon me considering my noviceness, if you find it foolish)

thanks

---

### Post by slavik on 2008-10-01
I'd suggest reading the C standard, it is most likely that the result of such an operation is undefined (or up to the individual implementations).

---

### Post by Tony Flury on 2008-10-01
also stdin is not always the keyboard - depending on how someone uses an application, stdin might be a file (if they use < - redirection - for instance) or the output of another program (if they use | - pipe ).

Similarly stdout is mot always the screen - it can be another file - or could be piped to be the stdin of another program.

however - if you don't do anything special when you run your program - just run it on its own with no redirections or pipes, and the program itself does not do anything special with stdin and stdout, then they are often keyboard and screen.

---

### Post by kcode on 2008-10-01
> **Tony Flury said:**
> also stdin is not always the keyboard - depending on how someone uses an application, stdin might be a file (if they use < - redirection - for instance) or the output of another program (if they use | - pipe ).

Similarly stdout is mot always the screen - it can be another file - or could be piped to be the stdin of another program.

however - if you don't do anything special when you run your program - just run it on its own with no redirections or pipes, and the program itself does not do anything special with stdin and stdout, then they are often keyboard and screen.

thanks
After reading this,i searched for implementation of redirection.
We can redirect standard streams using freopen().
here is the implementation:

first treating a file as stdout ->

```

#include <stdio.h>

int main()
{
        freopen("outfile","w",stdout);
        printf("1");
      
        return 0;

}
```

cat outfile
1

similarly for stdin->

```

#include <stdio.h>

int main()
{
        int input;
        freopen("outfile","r",stdin);

        scanf("%d",&input);

        printf("%d is read from file which is acting as stdin");

        return 0;
}
```
output ->
1 is read from file which is acting as stdin

regarding the fprintf() thing, no success.

---

