---
title: "yes program."
date: 2009-06-24
forum: Programming Talk
---

### Post by cmay on 2009-06-24
hi.
i could not sleep last night  so i wrote a small yes program from this describiton [http://linux.about.com/library/cmd/blcmdl1_yes.htm](http://linux.about.com/library/cmd/blcmdl1_yes.htm)
i never used the yes command or have it on my system but i seen the program before from here [http://minnie.tuhs.org/UnixTree/V7/usr/src/cmd/yes.c.html](http://minnie.tuhs.org/UnixTree/V7/usr/src/cmd/yes.c.html)

i would like to know what you think of it.
```

/* 
* usage; a simple yes program that print 'y' to stdout unless string giving as second option
* synopsis
* yes [option] 
* yes [string]
* yes  [default , will print'y' to stdout] 
*
* options 
*            --version
*            --help
*            --license 
* 
*/

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <errno.h>


void help();
void license();
void version();

int main(int argc, char** argv)
{
   
    int i;
    if( argc == 1)
    { 
        for(;;)
           fprintf(stdout,"y\n");
                
                 
    } 
         
         for(i=1;i < argc;i++)
         {
                
                   
                   if(strcmp(argv[i],"--version") == 0)
                   {
                             version(argv[0]);
                   }
                   
                   else if (strcmp(argv[i],"--license") == 0)
                   {
                            license(argv[0]);
                   }
                   
                   else if (strcmp(argv[i],"--help") == 0)
                  {
                             help(argv[0]);
                
                   } else { 
                    
                              for(;;)
                                 fprintf(stdout,"%s\n",argv[i]);
                                  
                         }   
         }
         
         
    return 0;
}


void help(const char *progname)
{
    printf("%s: usage no option [option] [string]                        \n"
           "\t--version                   prints version number to stdout\n"
           "\t--help                                           this help \n"
           "\t--license                          prints license to stdout\n"
           "\tno option prints singel char y to stdout until program killed\n"
           "\t%s [string]  prints string to stdout until program killed\n",progname,progname);
            exit(0);
}

void license(const char *progname)
{
    fprintf(stdout,"%s\tauthor carsten may 2009\n license BSD\n",progname);
     exit(0);
}

void version(const char *progname)
{
    fprintf(stdout,"%s\tversion 0.0.1\n",progname);
      exit(0);
}



```

---

### Post by jinksys on 2009-06-24
Looks good, but what if I want it to repeat the text **--help** repeatedly?

---

### Post by simeon87 on 2009-06-24
What would be a useful purpose of such program?

---

### Post by MadCow108 on 2009-06-24
[http://en.wikipedia.org/wiki/Yes_(Unix)#Uses](http://en.wikipedia.org/wiki/Yes_(Unix)#Uses)

---

### Post by cmay on 2009-06-24
> **jinksys said:**
> Looks good, but what if I want it to repeat the text **--help** repeatedly?

thats a problem i can see that. 
one more thing is that when i woke up i just posted this i did not know what to think of my self. but having played around with i can see that it does not  seem to work. 

the yes program from the unix tree sources does the same ting but i have not been able to verify how that works either. 

i dont use programs that ask me to confirm tings that often i guess. 

it took 15 minuttes to write and i am not sure it is worth making more out of it other than figure out why it does not work.  it should at least work other wise there is no point in doing it.

---

### Post by simeon87 on 2009-06-24
> **jinksys said:**
> Looks good, but what if I want it to repeat the text **--help** repeatedly?

To be fair, the yes program included in Ubuntu also can't repeatedly print --help or --version :)

> **MadCow108 said:**
> [http://en.wikipedia.org/wiki/Yes_(Unix)#Uses](http://en.wikipedia.org/wiki/Yes_(Unix)#Uses)

Thanks, though it also suggests the use of this program may be a bit outdated.

---

### Post by Joeb454 on 2009-06-24
> **simeon87 said:**
> To be fair, the yes program included in Ubuntu also can't repeatedly print --help or --version :)

Actually yes it can ;)

```
yes "--help"
```

Works on my system anyway :p (I should probably point out that right now I'm on an OS X system)

---

### Post by s.fox on 2009-06-24
```
yes --help
```also works for me on my system (fedora 8 based distribution)

-Ash R

---

### Post by cmay on 2009-06-24
thanks 
i put in a -i flag to ignore the --help --version and ---license long options. 
i cant make it useful on my own system anyway. 
```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <errno.h>


void help();
void license();
void version();

int main(int argc, char** argv)
{
   
    int i;
    if( argc == 1)
    { 
        for(;;)
           fprintf(stdout,"y\n");
                
                 
    } 
         if(argv[1][0] == '-' && argv[1][1] == 'i')
         {
               
             for(;;)
                fprintf(stdout,"%s\n",argv[2]);
                                  
         }  
         
         for(i=1;i < argc;i++)
         {
                
                   
                   if(strcmp(argv[i],"--version") == 0)
                   {
                             version(argv[0]);
                   }
                   
                   else if (strcmp(argv[i],"--license") == 0)
                   {
                            license(argv[0]);
                   }
                   
                   else if (strcmp(argv[i],"--help") == 0)
                  {
                             help(argv[0]);
                
                   } else { 
                    
                              for(;;)
                                 fprintf(stdout,"%s\n",argv[i]);
                                  
                         }   
         }
         
         
    return 0;
}


void help(const char *progname)
{
    printf("%s: usage no option [option] [string]                        \n"
           "\t--version                   prints version number to stdout\n"
           "\t--help                                           this help \n"
           "\t--license                          prints license to stdout\n"
           "\tno option prints singel char y to stdout until program killed\n"
           "\t%s [string]  prints string to stdout until program killed\n",progname,progname);
            exit(0);
}

void license(const char *progname)
{
    fprintf(stdout,"%s\tauthor carsten may 2009\n license BSD\n",progname);
     exit(0);
}

void version(const char *progname)
{
    fprintf(stdout,"%s\tversion 0.0.1\n",progname);
      exit(0);
}

```

---

### Post by ibuclaw on 2009-06-24
> **Joeb454 said:**
> Actually yes it can ;)

```
yes "--help"
```

Works on my system anyway :p (I should probably point out that right now I'm on an OS X system)

Wrong :)

```
yes \ --help
```

---

### Post by jinksys on 2009-06-24
> **Joeb454 said:**
> (I should probably point out that right now I'm on an OS X system)

It looks like linux's yes command has two switches, version and help.  BSD's yes command has no switches, so it can print --help.

<--OS 10.5

---

