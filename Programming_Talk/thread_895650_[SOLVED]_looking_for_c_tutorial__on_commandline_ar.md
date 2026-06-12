---
title: "[SOLVED] looking for c tutorial  on commandline arguments."
date: 2008-08-20
forum: Programming Talk
---

### Post by cmay on 2008-08-20
hi
i have read and solved all prblems in this book
[http://nyttf.dk/?pagetype=book&vareid=57122709](http://nyttf.dk/?pagetype=book&vareid=57122709)
i wanna learn c so that i can understand better 
books like kernighans the unix programming enviroment
and i have some books of my own on unix that i would 
benefit from learning c to understand.

however this book i have followed does not teach anything
about commandline parameters at all.
i found the tutorial 
[http://www.lysator.liu.se/c/bwk-tutor.html](http://www.lysator.liu.se/c/bwk-tutor.html)
to try and make up for this.
here is the example from this tutorial.

   ```
main(argc, argv)
          int argc;
          char **argv; {
               ...
               aflag = bflag = cflag  = 0;
               if( argc > 1 && argv[1][0] == '-' ) {
                       for( i=1; (c=argv[1][i]) != '\0'; i++ )
                               if( c=='a' )
                                       aflag++;
                               else if( c=='b' )
                                       bflag++;
                               else if( c=='c' )
                                       cflag++;
                               else
                                       printf("%c?\n", c);
                       --argc;
                       ++argv;
               }
```

can anyone help me find something that can teach me this 
better since i do not understand this yet.

any help greatly apriciated.
thank for your time.

---

### Post by LaRoza on 2008-08-20
```

#include <stdio.h>
int main(int argc, char ** argv)
{
    int i;
    for (i = 0; i < argc; i++)
    {
        puts(argv[i]);
    }
    return 0;
}

```

argc is the argument count, argv is the argument vector (list of arguments, indexed like an array. Can also be defined as "char * argv[]))

---

### Post by generalguy on 2008-08-20
Basically argc holds the number of arguments given. This includes the program name so invoking:

```
myprog 1 2 3
```

on the command line would have an argc of 4. argv holds the actual arguments as strings, so it would contain:
```

{"myprog","1","2","3"}

```

---

### Post by cmay on 2008-08-20
thanks.
i have found out that much by now that i can write a simple program that takes a single argument . but what i want is for it to take more than one.
i had a break for 3 weeks since i was sick so coming back to my studies i wanted to rewrite a practice program. the wc program from kerninghans c programming language . a book that i have to read on the library.
this example below is how much i already know so far.

```
#include <stdio.h>
#include <stdlib.h>
char *progname;
void do_stuff();
void do_more_stuff_here();
int main(int argc, char** argv){
    /* declare stuff here*/
    progname=argv[0];   
    int i;

    /* Start at i = 1 to skip the command name. */

    for (i = 1; i < argc; i++){

	/* Check for a switch (leading "-"). */

	if (argv[i][0] == '-'){

	/* Use the next character to decide what to do. */
        switch (argv[i][1]){
        --argc;
        ++argv;
		case 'a':
		do_stuff();
		puts("the a flag");
		break;
		case 'b':
		do_stuff();
		puts("the b flag");
		break;
		case 'c':
		do_stuff();
		puts("the c flag");
		break;
		case 'd':
		do_more_stuff_here();
		puts("the d flag");		
		break;
        default:
        printf("%s invalid input or missing parameters \n",progname);
        exit(1);
        break;      
	        }	
    	  }    
        }
        printf("usage: does stuff %d\n",argc);
return 0;

}
void do_stuff(){
	printf(" do some stuff here 1 ");
	getchar();
}
void do_more_stuff_here(){
	puts("hello world again");
	getchar();
}
```

---

### Post by LaRoza on 2008-08-20
Your C code is really ancient. Try using modern standard C, which is what most people use. At least C89

---

### Post by dwhitney67 on 2008-08-20
> **cmay said:**
> hi
i have read and solved all prblems in this book
[http://nyttf.dk/?pagetype=book&vareid=57122709](http://nyttf.dk/?pagetype=book&vareid=57122709)
i wanna learn c so that i can understand better 
books like kernighans the unix programming enviroment
and i have some books of my own on unix that i would 
benefit from learning c to understand.

however this book i have followed does not teach anything
about commandline parameters at all.
i found the tutorial 
[http://www.lysator.liu.se/c/bwk-tutor.html](http://www.lysator.liu.se/c/bwk-tutor.html)
to try and make up for this.
here is the example from this tutorial.

   [PHP]main(argc, argv)
          int argc;
          char **argv; {
               ...
               aflag = bflag = cflag  = 0;
               if( argc > 1 && argv[1][0] == '-' ) {
                       for( i=1; (c=argv[1][i]) != '\0'; i++ )
                               if( c=='a' )
                                       aflag++;
                               else if( c=='b' )
                                       bflag++;
                               else if( c=='c' )
                                       cflag++;
                               else
                                       printf("%c?\n", c);
                       --argc;
                       ++argv;
               }[/PHP]

can anyone help me find something that can teach me this 
better since i do not understand this yet.

any help greatly apriciated.
thank for your time.
If you are developing for Unix/Linux only, then I would recommend using getopt().

From the example you provided above, essentially the loop is examining each argv value, if any, and not including the very first one which is the program name.

If the first character of one of the argv strings is a '-', then the next character from the argv string is obtained.  Desirable values for these characters are 'a', 'b', and 'c'; anything else will be reported as a warning using the printf().

So for example, if you compile the program above, and run such as:
```
$ gcc option.c -o option
$ option -a -b -n
```
The output should look like following because the 'n' option is not recognized by the program:
```
n?
```
Any command line arguments that are not preceded with a '-' are ignored by your program; they shouldn't be because these too can be deemed to be errors.

On occasion it is necessary to supply data with a command-line option.  For instance:
```
my_server -p 9000
```
This application expects to receive a '-p' as an option to specify a port number, which is 9000.  Thus the application needs to parse the command-line argv[1] string for a '-', then a 'p', and then use argv[2] to get the port number.  If the argv[2] is not a numeric value (or if it is missing), then an error should be reported.

In conclusion, the best way to learn how to process command-line args is to write code that you can practice with.

P.S.
Throw away those C books you are referencing; they are teaching you antiquated C programming structure.

The modern way to declare a function, whether it be main() or something else is to follow this convention:
[PHP]<return type> functionName( <param1 type><param1>, <param2 type><param2>, ..., <paramN type><paramN> )
{
  ...
}[/PHP]

---

### Post by cmay on 2008-08-20
> your C code is really ancient. Try using modern standard C, which is what most people use. At least C89 
yes but the books i have that i am trying to understand uses this old code.
i have as example read the unix programming enviroment by kernighan.
that code in that book is even older than this. it still uses void main()
i have not found any up to date tutorials on the internet so far.
i would be happy to learn the new c99 standard but i have not come across book nor free tutorial on that yet.

---

### Post by cmay on 2008-08-20
> P.S.
Throw away those C books you are referencing; they are teaching you antiquated C programming structure.

i will as soon as i have a understanding of the books i have picked up on unix. i also read as much i can about c as i can on the internet.

and thanks for the reply this looks like something 
i can use to spend some time on .

thanks.

---

### Post by dwhitney67 on 2008-08-20
cmay

This might be a better C tutorial to reference/bookmark:
[http://www.cprogramming.com/tutorial.html#ctutorial](http://www.cprogramming.com/tutorial.html#ctutorial)

---

### Post by mike_g on 2008-08-20
Once you have the basics done I'd recommend learning to use getopt_long. It handles linux commnd line options for you, and saves quite a bit of work. You can find exmaples by tying:
```
man getopt
```

---

### Post by cmay on 2008-08-20
> 
Once you have the basics done I'd recommend learning to use getopt_long. It handles linux commnd line options for you, and saves quite a bit of work. :

thanks. the above is just a template i had created 3 weeks ago when i had a break. i want to start learning again where i left of. i am very happy for the help i recieve.
thanks

---

### Post by cmay on 2008-08-20
thanks all of the ones giving input to me.
i posted these links i have been using so far.
just in case some one could find one of them useful
still some of them are are bit old. 
i how ever found the ones about pointers ted jensens in particular
very useful.

generel c tutorials           

[http://www.physics.drexel.edu/students/courses/Comp_Phys/General/C_basics/](http://www.physics.drexel.edu/students/courses/Comp_Phys/General/C_basics/)
[http://www.cs.cf.ac.uk/Dave/C/node4.html](http://www.cs.cf.ac.uk/Dave/C/node4.html)
[http://www.cprogramming.com/tutorial.html#ctutorial](http://www.cprogramming.com/tutorial.html#ctutorial)
[http://www.lysator.liu.se/c/bwk-tutor.html](http://www.lysator.liu.se/c/bwk-tutor.html)
[http://www.nongnu.org/c-prog-book/online/index.html](http://www.nongnu.org/c-prog-book/online/index.html)
[http://www.le.ac.uk/cc/tutorials/c/](http://www.le.ac.uk/cc/tutorials/c/)
[http://users.actcom.co.il/~choo/lupg/tutorials/](http://users.actcom.co.il/~choo/lupg/tutorials/)
[http://www.kegel.com/academy/tutorials.html](http://www.kegel.com/academy/tutorials.html)

in danish
[http://our-site.dk/service/kurser/C/C.php](http://our-site.dk/service/kurser/C/C.php)

pointers
[http://pw2.netcom.com/~tjensen/ptr/pointers.htm](http://pw2.netcom.com/~tjensen/ptr/pointers.htm)
[http://www.cplusplus.com/doc/tutorial/pointers.html](http://www.cplusplus.com/doc/tutorial/pointers.html)
[http://boredzo.org/pointers/](http://boredzo.org/pointers/)

manpages / make
[http://linux.die.net/man/](http://linux.die.net/man/)
[http://www.gnu.org/software/make/manual/make.html](http://www.gnu.org/software/make/manual/make.html)
[http://www-user.tu-chemnitz.de/~anhe/DOCU/C/C/master_index](http://www-user.tu-chemnitz.de/~anhe/DOCU/C/C/master_index).
[http://hsrl.rutgers.edu/ug/make_help.html](http://hsrl.rutgers.edu/ug/make_help.html)

---

### Post by happysmileman on 2008-08-20
If you're sitll wondering why your code above it wrong, I think it's because you included: "--argc;" and "++argv" in it, I'm not sure why you did that.

```
int main(int argc, char** argv){
    /* declare stuff here*/
    progname=argv[0];   
    int i;

    /* Start at i = 1 to skip the command name. */

    for (i = 1; i < argc; i++){

	/* Check for a switch (leading "-"). */

	if (argv[i][0] == '-'){

	/* Use the next character to decide what to do. */
        switch (argv[i][1]){
        _--argc;_
        _++argv;_
		case 'a':
		do_stuff();
		puts("the a flag");
		break;
		case 'b':
		do_stuff();
		puts("the b flag");
		break;
		case 'c':
		do_stuff();
		puts("the c flag");
		break;
		case 'd':
		do_more_stuff_here();
		puts("the d flag");		
		break;
        default:
        printf("%s invalid input or missing parameters \n",progname);
        exit(1);
        break;      
	        }	
    	  }    
        }
        printf("usage: does stuff %d\n",argc);
return 0;
}

```

Underlined them there, those are unecessary and will cause the program to skip over many arguments given

---

### Post by cmay on 2008-08-20
> f you're sitll wondering why your code above it wrong, I think it's because you included: "--argc;" and "++argv" in it, I'm not sure why you did that.
thanks
 its just a template i have from tutorial where that was supposed to have a simple calculations of how many dollars tax outputted in different ways to terminal so what i did was remove this and then just use it as template.
it did not compile from the tutorial in the first place.

i posted some links which some of them is good othes not so up to date i hope maybe some one could use them. i think i found some thing on getopt in the gnu tutorial. i will dig into this tonight.
i printed the whole thing and sort it as i read it.

---

### Post by cmay on 2008-08-20
update.
[http://www.nongnu.org/c-prog-book/online/x941.html](http://www.nongnu.org/c-prog-book/online/x941.html)
this was why i ask for some tutorials as it happens too many times
 when i read online tutorials.
 i assume that this is the way i should do if i want to parse command-line arguments.
 however i only programmed a month in c
so i do not quit understand this yet.
i cant find any tutorial on it.

```
#include <stdlib.h>
#include <argp.h>

const char *argp_program_version = "simple_argp 0.1";
const char *argp_program_bug_address =
           "<some_email_address@you_care_about.com>";

static char doc[] =
"short program to show the use of argp\nThis program does little";

static char args_doc[] = "ARG1 ARG2";

/* initialise an argp_option struct with the options we except */
static struct argp_option options[] =
{
  {"verbose", 'v', 0,      0, "Produce verbose output" },
  {"output",  'o', "FILE", 0, "Output to FILE" },
  { 0 }
};

/* Used by `main' to communicate with `parse_opt'. */
struct arguments
{
  char *args[2];                /* ARG1 & ARG2 */
  int silent, verbose;
  char *output_file;
};

/* Parse a single option. */
static error_t
parse_opt (int key, char *arg, struct argp_state *state)
{
  /* Get the INPUT argument from `argp_parse', which we
     know is a pointer to our arguments structure. */
  struct arguments *arguments = state->input;

  switch (key)
    {
    case 'q': case 's':
      arguments->silent = 1;
      break;
    case 'v':
      arguments->verbose = 1;
      break;
    case 'o':
      arguments->output_file = arg;
      break;

    case ARGP_KEY_ARG:
      if (state->arg_num >= 2)
        /* Too many arguments. */
        argp_usage (state);

      arguments->args[state->arg_num] = arg;

      break;

    case ARGP_KEY_END:
      if (state->arg_num < 2)
        /* Not enough arguments. */
        argp_usage (state);
      break;

    default:
      return ARGP_ERR_UNKNOWN;
    }
  return 0;
}

/* Our argp parser. */
static struct argp argp = { options, parse_opt, args_doc, doc };

int main (int argc, char **argv)
{
  struct arguments arguments;

  /* Default values. */
  arguments.silent = 0;
  arguments.verbose = 0;
  arguments.output_file = "-";

  /* Parse our arguments; every option seen by `parse_opt' will
     be reflected in `arguments'. */
  argp_parse (&argp, argc, argv, 0, 0, &arguments);

  printf ("ARG1 = %s\nARG2 = %s\nOUTPUT_FILE = %s\n"
          "VERBOSE = %s\nSILENT = %s\n",
          arguments.args[0], arguments.args[1],
          arguments.output_file,
          arguments.verbose ? "yes" : "no",
          arguments.silent ? "yes" : "no");

  exit (0);
}
    
```
any specific tutorials on this will be higly apriciated.
my sources are too old or too uninformative for a beginner anyway:)

thanks for the time.

---

### Post by dwhitney67 on 2008-08-20
cmay -
Here's an example using getopt().  Note that getopt() is not available under Windoze.

[PHP]#include <unistd.h>
#include <stdlib.h>
#include <string.h>
#include <stdio.h>


void printUsage( const char *progName )
{
  printf( "Usage:  %s [-p port] [-h hostname] [-v]\n"
          "where -p is used to specify the port number,\n"
          "      -h is used to specify the hostname of the server,\n"
          "      -v is used for verbose debug output.\n\n",
          progName );
}

void parseOptions( int argc, char **argv, int *port, char **host, int *verbose )
{
  int          c;
  extern char *optarg;

  // Parse command line arguments (note the ':' after each possible arg character
  // denotes that an additional argument is expected.) 
  //
  while ((c = getopt(argc, argv, "p:h:v")) != EOF)
  {
    switch (c)
    {
      case 'p':    // port number
          *port = atoi(optarg);
          break;

      case 'h':    // host name
          if (*host != 0)
            free(*host);

          *host = malloc( strlen(optarg)+1 );
          strncpy( *host, optarg, strlen(optarg) );
          break;

      case 'v':    // vebose debug output
          *verbose = 1;
          break;

      default:
          printUsage( argv[0] );
          exit(1);
    }
  }
}


int main( int argc, char **argv )
{
  int port = 9000;
  char *host = malloc( 10 );
  strncpy( host, "localhost", 10 );
  int verbose = 0;

  parseOptions( argc, argv, &port, &host, &verbose );

  printf( "Port    = %d\n", port );
  printf( "Host    = %s\n", host );
  printf( "Verbose = %s\n", (verbose ? "true" : "false") );

  free( host );

  return 0;
}[/PHP]

---

### Post by cmay on 2008-08-20
> cmay -
Here's an example using getopt(). Note that getopt() is not available under Windoze
thanks thanks thanks.
that i can see pretty clear how works as opposed to many of the
examples i seen in tutorials that dont explain or dont work.
i am reading the book by andrew s tanenbaum about minix3 and some other books i have about unix (old but still usable) 
and i have to learn c to fully understand what the books are trying to communicate.

thanks for the help.
that means a lot to me.

---

