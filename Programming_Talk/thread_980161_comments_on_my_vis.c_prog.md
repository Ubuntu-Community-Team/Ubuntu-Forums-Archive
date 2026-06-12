---
title: "comments on my vis.c prog"
date: 2008-11-12
forum: Programming Talk
---

### Post by cmay on 2008-11-12
i wrote this taken in part from  the book the unix programming environment. the original does not look like this but the vis function is almost exactly the same. what do you think. more important how can i improve it. i am newbie so please be honest.
 thanks for taking you time to read this.
[php]
#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>
#include <string.h>

char author[]="cmay <no@mail.com>";
float version= 0.1;
char *progname;

int Vis(FILE *in);
int print_usage();
int print_version();

int main(int argc, char** argv)
{
    extern char *progname;
           progname=argv[0];
           int i;
           
    FILE *my_file =fopen(argv[2],"r");

        if(argc == 1)
          {
              print_usage();
              return 1;
          }
           if (argv[i][0] == '-')
          {

           switch (argv[i][1])
          {                       
            case 's':
            argv++;
            argc--;
              if(my_file == NULL)
            {
              fprintf(stderr,"%s error opening %s\n",progname,argv[i]);
            }else{
                i++;
            Vis(my_file);
             fclose(my_file);
             return 0;
            }
            break;
            case 'h':
            print_usage();
            break;
            case 'v':
            print_version();
            break;
            default:
            fprintf(stderr,"unknown argument\n");            
            fprintf(stderr,"%s usage: Vis [file]\n",progname);
            return 1;
          }
      }
             
       
    return 0;
}
/***********************************************************************/

int Vis(FILE *in)
{
    int c;
    
    while((c=getc(in))!= EOF)
    {
         if((isascii(c) && isprint(c)) || c == '\n'||c=='\t'||c== ' ')
         {
              putchar(c);
             
          }else{
           
           printf("\\%o30",c);
        
        }
    }
return 0;
}

/**********************************************/ 
int print_usage()
{
    fprintf(stdout,"%s:usage [-v][-s][-h][file]\n",progname);
    fprintf(stdout,"license GPL\n");
    return 0;
    
}
/***********************************/
int print_version()
{
    fprintf(stdout,"Progname: %s \n",progname);
    fprintf(stdout,"Author:%s\n",author);
    fprintf(stdout,"Version%1.2f\n",version);
    return 0;
}
/***************end of prog ***********************/
[/php]

---

### Post by stevescripts on 2008-11-12
Things to think about ...

Consider your function declarations and return types ...

Functions that print info to the screen are normally void.

Not that it matters here, get in the habit of *never* using float...

Steve (who seldom does C anymore)

---

### Post by cmay on 2008-11-12
thanks.
can i ask why never use float .
the return functions should be void yet it is put there for the reason that i had some problems when writing it so it got into a never ending loop which i needed a return to getting out of. i should of course change it.

---

### Post by stevescripts on 2008-11-12
At some point, floats will bite you in the backside due to inaccuracy.

Steve
(also, what if you wanted a program version like, say 0.9a ?)

---

### Post by dwhitney67 on 2008-11-12
> **cmay said:**
> i wrote this taken in part from  the book the unix programming environment. the original does not look like this but the vis function is almost exactly the same. what do you think. more important how can i improve it. i am newbie so please be honest.
 thanks for taking you time to read this.
[php]
#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>
#include <string.h>

char author[]="cmay <no@mail.com>";
float version= 0.1;
char *progname;

int Vis(FILE *in);
int print_usage();
int print_version();

int main(int argc, char** argv)
{
    extern char *progname;
           progname=argv[0];
           int i;
           
    FILE *my_file =fopen(argv[2],"r");

        if(argc == 1)
          {
              print_usage();
              return 1;
          }
           if (argv[i][0] == '-')
          {

           switch (argv[i][1])
          {                       
            case 's':
            argv++;
            argc--;
              if(my_file == NULL)
            {
              fprintf(stderr,"%s error opening %s\n",progname,argv[i]);
            }else{
                i++;
            Vis(my_file);
             fclose(my_file);
             return 0;
            }
            break;
            case 'h':
            print_usage();
            break;
            case 'v':
            print_version();
            break;
            default:
            fprintf(stderr,"unknown argument\n");            
            fprintf(stderr,"%s usage: Vis [file]\n",progname);
            return 1;
          }
      }
             
       
    return 0;
}
/***********************************************************************/

int Vis(FILE *in)
{
    int c;
    
    while((c=getc(in))!= EOF)
    {
         if((isascii(c) && isprint(c)) || c == '\n'||c=='\t'||c== ' ')
         {
              putchar(c);
             
          }else{
           
           printf("\\%o30",c);
        
        }
    }
return 0;
}

/**********************************************/ 
int print_usage()
{
    fprintf(stdout,"%s:usage [-v][-s][-h][file]\n",progname);
    fprintf(stdout,"license GPL\n");
    return 0;
    
}
/***********************************/
int print_version()
{
    fprintf(stdout,"Progname: %s \n",progname);
    fprintf(stdout,"Author:%s\n",author);
    fprintf(stdout,"Version%1.2f\n",version);
    return 0;
}
/***************end of prog ***********************/
[/php]

A couple of issues I see:

1.  The variable progname is not really necessary.  You could just pass argv[0] as a function paramater to print_usage() or print_version().

2.  You attempt to open the file (using argv[2]) before you even check if you have sufficient arguments on the command line.

3.  Consider using getopt() if you plan to parse command line options.

4.  Vis() returns a value; it appears that it is not necessary.  Declare the function to return void.

5.  Choose a better indentation style, especially in the switch-block.

---

### Post by cmay on 2008-11-12
> **dwhitney67 said:**
> A couple of issues I see:
thanks.
1.  The variable progname is not really necessary.  You could just pass argv[0] as a function paramater to print_usage() or print_version().

2.  You attempt to open the file (using argv[2]) before you even check if you have sufficient arguments on the command line.

3.  Consider using getopt() if you plan to parse command line options.

4.  Vis() returns a value; it appears that it is not necessary.  Declare the function to return void.
1
i had not been thinking about that up to now. seems like a more compact readable solution. i should maybe get into that habit. i do not know where i seen the other way done before but i have always been thinking it was 'the right'  way to do it. 
2
that explains the problems i had getting the program to work. i just wanted to rewrite the whole program and not copy the program from the book.  
3
i am actually trying right now to write it using getopt() which i will spend my evening doing. thanks for the replies.

one thing is however i am not so sure of is how to make it open more than one file from the arguments given on the commandline. i am still very new to this. 
thanks for the time.

---

### Post by dwhitney67 on 2008-11-12
> **cmay said:**
> 
...
i am actually trying right now to write it using getopt() which i will spend my evening doing.
...

Good for you.  If you have the manpages installed on your system, there is a clear-cut example provided for getopt() at the end of the manpage.

```

man 3 getopt

```

---

### Post by cmay on 2008-11-12
> **dwhitney67 said:**
> Good for you.  If you have the manpages installed on your system, there is a clear-cut example provided for getopt() at the end of the manpage.

```

man 3 getopt

```

i have a template from a example you gave me once. i just never used it to write a program that uses files before. thanks again for posting that one.:)

---

### Post by rbprogrammer on 2008-11-12
Great recommendation dwhitney67 on using the man pages.  But also as a supplement, I always found the GNU's libtool manual particularly useful in instances like this.

You can find getopt in the libtool docs at:
[http://www.gnu.org/software/libtool/manual/libc/Getopt.html](http://www.gnu.org/software/libtool/manual/libc/Getopt.html)

---

### Post by cmay on 2008-11-13
it was geting late at night when i got around to doing it but i got a working version. 
i will take some more time later to write this so it is more nice and handy in the layout.
thanks for your help. 
[php]#include <unistd.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h>
#include <stdio.h>

void Print_Usage( const char *progName )
{
  printf( "Usage:  %s options [-h ] [-v] [file]\n"
          "-h help this help,\n"
          "-v version information.\n\n",
          progName );
}
void  Print_Version()
{
    printf("Author:cmay <no@mail.com>\n"
           "license:GPL\n"
           "version: 0.2a \n");
}
void Vis(FILE *in)
{
    int c;
    
    while((c=getc(in))!= EOF)
    {
         if((isascii(c) && isprint(c)) || c == '\n'||c=='\t'||c== ' ')
         {
              putchar(c);
             
          }else{
           
           printf("\\%o30",c);
        
        }
    }
}
    
void parseOptions( int argc, char **argv, int *vflag, int *hflag)
{
  int          c;
  extern char *optarg;
 
  while ((c = getopt(argc, argv, "hv")) != EOF)
  {
    switch (c)
    {
      case 'v':    
          *vflag=1;
          break;

      case 'h':  
          *hflag=1;       
          break;
     default:
     Print_Usage(argv[0]);
        exit(0);
     }
  }
}


int main( int argc, char **argv )
{
  int vflag=0;
  int hflag=0;
  FILE *fp;
 
  parseOptions( argc, argv, &vflag, &hflag);
    if(hflag == 1)
      {
          Print_Usage(argv[0]);  
          return 0; 
      }
    if(vflag ==1)
      {
          Print_Version();
          return 0;
       }else{
            
             if(argc != 2)
             {
               fprintf(stderr,"invalid option or too many arguments\n");
               return 1;
           }else{
               
            fp=fopen(argv[1],"r");
            
            if(fp == NULL)
            {
                fprintf(stderr,"%s error opening %s:\n",argv[0],argv[1]);
                return 1;
          }else{
          Vis(fp);
           fclose(fp);
         return 0;
         }
       }
     }
    
  return 0;
} [/php]

---

