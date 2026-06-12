---
title: "[SOLVED] &amp;amp;amp;quot; program to imitate&amp;amp;amp;quot; cat command"
date: 2008-03-09
forum: Programming Talk
---

### Post by vikasmk on 2008-03-09
```
#include"stdio.h"
 int main()
{ FILE *fp/*file pointer*/
  char ch;
  
 
  
 fp=fopen(" ","rb");/*SOme how want to get the file name here)*/
  if(fp==NULL)
  printf("cant open or file doesn't exist\n");
  do {
      ch=fgetc(fp);
      printf("%c",ch);     
   } while (ch!=EOF);
  fclose(fp);
  
 return 0;
  
 }
```
  i want the program to read in a filename and display its content just like "cat"
 but ```
fopen(" ","rb");
``` i dont know any way of getting the file name into the fopen function. 
Can anyone suggest something??

---

### Post by Fixman on 2008-03-09
```
#include"stdio.h"
 int main(int argc, char **argv)
{ FILE *fp/*file pointer*/
  char ch;


  if (argc != 2)
  {
    printf ("Usage: %s file\n", argv[0]) ;
    return 1 ;
  }
  
 fp=fopen(argv[1],"r");/*SOme how want to get the file name here)*/
  if(fp==NULL)
  {
     printf("cant open or file doesn't exist\n");
     return 1 ;
   }
  do {
      ch=fgetc(fp);
      printf("%c",ch);     
   } while (ch!=EOF);
  fclose(fp);
  
 return 0;
  
 }
```

If you there put

```
catclone file.txt
```

Prints the contents of file.txt

EDIT: Note that program DOES NOT imitate cat. A "total" cat imitation that I just made is:

```

#include <stdio.h>

int pr (FILE *n)
{
	if (!n) return 0 ;

	char c ;
	while ( (c = fgetc (n)) != EOF) printf ("%c", c) ;
	
	return 1 ;
}

int main(int argc, char **argv)
{
	if (argc == 1)
	{
		pr (stdin) ;
		return 0 ;
	}
	
	int i ;
	for (i = 1 ; i < argc ; i++) if (!pr(fopen(argv[i], "r"))) printf ("cat: %s: No such file or directory\n", argv[i]) ;
	
	return 0 ;
}


```

---

### Post by vikasmk on 2008-03-09
```
vikasmk@vikasmk:~$ gcc catclone.c
catclone.c: In function ‘main’:
catclone.c:4: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘char’
catclone.c:13: error: ‘fp’ undeclared (first use in this function)
catclone.c:13: error: (Each undeclared identifier is reported only once
catclone.c:13: error: for each function it appears in.)
catclone.c:13: warning: passing argument 1 of ‘fopen’ makes pointer from integer without a cast

```

---

### Post by ruy_lopez on 2008-03-09
for piping you can add something like this:

```

if (argc == 1) /* only program name */
       fp = stdin;
else {
/* fopen code */
}

```

Then you can pipe into your program.

Also, you can use fputc(ch, stdout) instead of print.

---

### Post by ruy_lopez on 2008-03-09
> **vikasmk said:**
> ```
vikasmk@vikasmk:~$ gcc catclone.c
catclone.c: In function ‘main’:
catclone.c:4: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘char’
catclone.c:13: error: ‘fp’ undeclared (first use in this function)
catclone.c:13: error: (Each undeclared identifier is reported only once
catclone.c:13: error: for each function it appears in.)
catclone.c:13: warning: passing argument 1 of ‘fopen’ makes pointer from integer without a cast

```

You're missing a ";" after FILE *fp

---

### Post by vikasmk on 2008-03-09
ya missed a ";" :popcorn: 
 thanx

---

### Post by Fixman on 2008-03-09
> **vikasmk said:**
> ya missed a ";" :popcorn: 
 thanx

Yup, I didn't test that code. But I tested the second one, that cleaner and totally clones cat.

---

### Post by mike_g on 2008-03-09
Also, EOF is an integer value.

---

### Post by a9bejo on 2008-03-09
> **vikasmk said:**
> [CODE]
  i want the program to read in a filename and display its content just like "cat"


You could study the [source code for the real cat](http://git.savannah.gnu.org/gitweb/?p=coreutils.git;a=blob;f=src/cat.c;h=d12144590901a54a43dfd1c5d31326046b123f94;hb=HEAD) at gnu.org and see how it is done there.

Writing a simple cat is also a part of the [K&R](http://en.wikipedia.org/wiki/The_C_Programming_Language_(book)) book. Here is the version from the book, written by Brian Kernighan and Dennis Ritchie:

[php]
#include <stdio.h> 
/* cat:  concatenate files, version 2 */ 
main(int argc, char *argv[]) 
{ 
    FILE *fp; 
    void filecopy(FILE *, FILE *); 
    char *prog = argv[0];  /* program name for errors */ 
    if (argc == 1 ) /* no args; copy standard input */ 
        filecopy(stdin, stdout); 
    else 
        while (--argc > 0) 
            if ((fp = fopen(*++argv, "r")) == NULL) { 
                fprintf(stderr, "%s: can't open %s\n", 
                        prog, *argv); 
                exit(1); 
            } else { 
                filecopy(fp, stdout); 
                fclose(fp); 
            } 
    if (ferror(stdout)) { 
        fprintf(stderr, "%s: error writing stdout\n", prog); 
        exit(2); 
    } 
    exit(0); 
}

/* filecopy:  copy file ifp to file ofp */ 
void filecopy(FILE *ifp, FILE *ofp) 
{ 
    int c; 
    while ((c = getc(ifp)) != EOF) 
        putc(c, ofp); 
} 

[/php]

---

### Post by vikasmk on 2008-03-09
what that filecopy function??

---

### Post by ruy_lopez on 2008-03-09
> **a9bejo said:**
> Writing a simple cat is also a part of the [K&R](http://en.wikipedia.org/wiki/The_C_Programming_Language_(book)) book. Here is the version from the book, written by Brian Kernighan and Dennis Ritchie

Here's filecopy():
[php]
/* filecopy: copy file ifp to file ofp */
void filecopy(FILE *ifp, FILE *ofp)
{
	int c;

	while ((c = getc(ifp)) != EOF)
		putc(c, ofp);
}
[/php]

EDIT: Straight from the book.

---

### Post by Fixman on 2008-03-09
> **vikasmk said:**
> what that filecopy function??

I guess its a non-headed function, but filecopy (a, stdout) is equicalent to my pr function.

---

### Post by Jessehk on 2008-03-09
I don't know how helpful this will be, but I wrote a *cat* clone a little while ago. 

If there are no arguments, it will read from stdin. If there *are* file arguments, it will open them one by one. Familiar error messages are provided thanks to **strerror()** when something goes wrong.

I should mention that just like the standard *cat*, it will not quit if a file can't be opened -- it will just print an error and go to the next one.
Also, I've used a glibc function, **getline()** that isn't standard. It should compile on all Linux distributions though. If portability really matters, it shouldn't be too hard to switch to **fgets()**.

```

/*
 * Clone of standard cat utility.
 * By Jessehk
 */
 
#define _GNU_SOURCE

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <errno.h>

#define IN_BUFFSIZE 64u
#define INPUT_ERR -1

void read_error( const char *filename, const char *msg ) {
    fprintf( stderr, "%s: %s\n", filename, msg );
}

void read( FILE *src ) {
    char *line = NULL;
    size_t buffsize = IN_BUFFSIZE;
    
    while ( getline( &line, &buffsize, src ) != INPUT_ERR )
        fputs( line, stdout );
        
    free( line );
}

int main( int argc, char *argv[] ) {
    FILE *src;
    int i;

    if ( argc > 1 ) {
        for ( i = 1; i < argc; i++ ) {
            if ( (src = fopen( argv[i], "r" )) == NULL ) {
                read_error( argv[i], strerror( errno ) );
            } else {
                read( src );
                fclose( src );
            }
        }
    } else
        read( stdin );
        
    return EXIT_SUCCESS;
}

```

---

### Post by a9bejo on 2008-03-09
> **vikasmk said:**
> what that filecopy function??

That code is also in the book.  I added it to my post above.

Edit: Looks like I was a little slow with that answer ;)

---

### Post by ruy_lopez on 2008-03-09
Buffered version of K&R's filecopy:

```

#include <stdio.h>
#include <string.h> 
#include <errno.h>
#include <fcntl.h>
#include <stdlib.h>
#include <unistd.h>

void filecopy(int);

int main(int argc, char *argv[])
{
	int fd;
	
	if (argc == 1)
		filecopy(0);
	else {
                while (--argc > 0)
		        if ((fd = open(*++argv, O_RDONLY, 0)) < 0) {
			        fprintf(stderr, "open error: %s\n", strerror(errno));
			        exit(EXIT_FAILURE);
		        } else {
			        filecopy(fd);
			        close(fd);
		        }
	}

	exit(EXIT_SUCCESS);
}

void filecopy(int fd)
{
	int n;
	char buf[BUFSIZ];

	while ((n = read(fd, buf, BUFSIZ)) > 0)
		write(1, buf, n);
}

```

---

