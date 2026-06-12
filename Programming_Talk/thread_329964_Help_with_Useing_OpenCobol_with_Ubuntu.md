---
title: "Help with Useing OpenCobol with Ubuntu"
date: 2007-01-02
forum: Programming Talk
---

### Post by paxmanchris on 2007-01-02
i have been going crazy trying to get OpenCobol to work with ubuntu.
i have check an [old thread]("http://www.ubuntuforums.org/showthread.php?t=115617&highlight=opencobol") for this, but it did not offer any help that i can use.

i got to the point of getting cobc to on my computer useing:
sudo apt-get install open-cobol

i made a test.cob file with the contents of:
```

	IDENTIFICATION DIVISION.
		PROGRAM-ID. hello.
		PROCEDURE DIVISION.
		DISPLAY "Hello World!".
		STOP RUN.

```

then i ran this command:
~$ cobc test.cob

it is able to genrate the c code, BUT it is unable to compile the c code into a binary.
the following is the genrated c code:

--hello.c--
```

/* Generated from test.cob by cobc 0.32 */

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <math.h>
#include <libcob.h>

#include "hello.h"

static int hello_ (int);

int
hello ()
{
  return hello_ (0);
}

static int
hello_ (int entry)
{
  static int initialized = 0;
  static cob_module module = { NULL, NULL, 0, '.', '$', ',', 0, 1, 1};


  cob_field f[4];


  /* perform frame stack */
  int frame_index;
  struct frame { int perform_through; void *return_address; } frame_stack[254];

  /* Start of function code */

  cob_module_enter (&module);

  if ( __builtin_expect(!initialized, 0) )
    {
      (*(int *) (b_2)) = 0;
      (*(int *) (b_3)) = 0;
      cob_move (&cob_zero, (f[1] = (cob_field) {4, b_4, &a_7}, &f[1]));

      initialized = 1;
    }

  /* initialize frame stack */
  frame_index = -1;
  frame_stack[0].perform_through = -1;

  /* initialize number of call params */
  (*(int *) (b_3))   = cob_call_params;

  goto l_6;

  /* PROCEDURE DIVISION */

  /* hello: */
  l_6:;
  /* test.cob:4: DISPLAY */
  {
    cob_display (&c_9);
    cob_newline ();
  }
  /* test.cob:5: STOP */
  {
    cob_stop_run ((*(int *) (b_2)));
  }

  cob_module_leave (&module);
  return (*(int *) (b_2));

  /* error handlers */

  /* standard_error_handler: */
  l_1:;
  switch (cob_error_file->last_open_mode)
    {
    default:
      if ( !cob_error_file->flag_has_status ) {
          cob_default_error_handle ();
          exit(1);
      }
      break;
    }
  if (frame_stack[frame_index].perform_through == 1)
    goto *frame_stack[frame_index].return_address;
  fprintf(stderr, "Codegen error\n");
  exit(1);

}


```

and the header
--hello.h--
```

static unsigned char b_2[4]	__attribute__ ((__aligned__(8)));  /* RETURN-CODE */
static unsigned char b_3[4]	__attribute__ ((__aligned__(8)));  /* NUMBER-OF-CALL-PARAMETERS */
static unsigned char b_4[4]	__attribute__ ((__aligned__(8)));  /* TALLY */
static cob_field_attr a_8	= {33, 0, 0, 0, 0};
static cob_field_attr a_7	= {17, 9, 0, 0, 0};
static cob_field c_9	= {12, "Hello World!", &a_8};


```


and finally the errors:
```

/tmp/cobRWiPIF.c:3:19: error: stdio.h: No such file or directory
/tmp/cobRWiPIF.c:4:20: error: stdlib.h: No such file or directory
/tmp/cobRWiPIF.c:5:20: error: string.h: No such file or directory
/tmp/cobRWiPIF.c:6:18: error: math.h: No such file or directory
In file included from /usr/include/libcob.h:23,
                 from /tmp/cobRWiPIF.c:7:
/usr/include/libcob/byteswap.h:28:23: error: sys/types.h: No such file or directory
In file included from /usr/include/libcob/call.h:23,
                 from /usr/include/libcob.h:24,
                 from /tmp/cobRWiPIF.c:7:
/usr/include/libcob/common.h:88: error: expected specifier-qualifier-list before ‘size_t’
In file included from /usr/include/libcob.h:26,
                 from /tmp/cobRWiPIF.c:7:
/usr/include/libcob/fileio.h:127: error: expected specifier-qualifier-list before ‘size_t’
In file included from /tmp/cobRWiPIF.c:9:
/tmp/cobRWiPIF.c.h:6: warning: excess elements in struct initializer
/tmp/cobRWiPIF.c.h:6: warning: (near initialization for ‘c_9’)
/tmp/cobRWiPIF.c.h:6: warning: excess elements in struct initializer
/tmp/cobRWiPIF.c.h:6: warning: (near initialization for ‘c_9’)
/tmp/cobRWiPIF.c.h:6: warning: excess elements in struct initializer
/tmp/cobRWiPIF.c.h:6: warning: (near initialization for ‘c_9’)
/tmp/cobRWiPIF.c: In function ‘hello_’:
/tmp/cobRWiPIF.c:32: error: ‘NULL’ undeclared (first use in this function)
/tmp/cobRWiPIF.c:32: error: (Each undeclared identifier is reported only once
/tmp/cobRWiPIF.c:32: error: for each function it appears in.)
/tmp/cobRWiPIF.c:52: warning: excess elements in struct initializer
/tmp/cobRWiPIF.c:52: warning: (near initialization for ‘(anonymous)’)
/tmp/cobRWiPIF.c:52: warning: excess elements in struct initializer
/tmp/cobRWiPIF.c:52: warning: (near initialization for ‘(anonymous)’)
/tmp/cobRWiPIF.c:52: warning: excess elements in struct initializer
/tmp/cobRWiPIF.c:52: warning: (near initialization for ‘(anonymous)’)
/tmp/cobRWiPIF.c:84: error: ‘cob_file’ has no member named ‘last_open_mode’
/tmp/cobRWiPIF.c:87: error: ‘cob_file’ has no member named ‘flag_has_status’
/tmp/cobRWiPIF.c:89: warning: incompatible implicit declaration of built-in function ‘exit’
/tmp/cobRWiPIF.c:95: warning: incompatible implicit declaration of built-in function ‘fprintf’
/tmp/cobRWiPIF.c:95: error: ‘stderr’ undeclared (first use in this function)
/tmp/cobRWiPIF.c:96: warning: incompatible implicit declaration of built-in function ‘exit’

```

i really hope that someone can help me here. i need this for one my classes and i DONT want to use window. 

oh.. if you know of a GOOD cobol complier for window (one which is free). let me know.

---

### Post by pmasiar on 2007-01-02
I never used COBOL in my life and hope I never will have to.. :-)  You are gaining some extremely rare skills here -- but I am not jealous :twisted: 

From error messages you posted my guess will be something got wrong during installation. Did you installed open-cobol via apt/synaptic? Did you set up all environment variables as documented in install guide?

---

### Post by paxmanchris on 2007-01-02
yes, i know what your saying pmasiar. i hate the fact that i got to learn it (very much the same way one would hate to learn latin).. 
but it is part of my degree. i must take it.

> Did you installed open-cobol via apt/synaptic?
 Did you set up all environment variables as documented in install guide?
yes i did install via apt/synaptic.
no i didnt set up any envorment variable.. i will give that a try after this post.

i did a:
sudo apt-get install build-essentials 
and got rid of mostly all the errors, but it still does not compile
the error is:
```
/usr/bin/ld: cannot find -ldb
collect2: ld returned 1 exit status

```


i will google the error part and try the enviroment variable part(the one on the OpenCobol web site.. right??) to see if i can get 
it working. in the mean time, if anyone has the answer to my problem feel free to post.

---

### Post by Mithrilhall on 2007-01-02
I'll install this later tonight if I get the chance.

I also had to take Cobol & Advanced Cobol..and the funny thing is I actually liked it.... ](*,)  I don't know why.

---

### Post by paxmanchris on 2007-01-07
i still would like to know if there is an answer to my problems.


dont we all.

---

### Post by Grey on 2007-01-07
Interesting.  I never knew that COBOL translated to C code.  That could very well explain why I couldn't get COBOL working on my laptop when I had to take that god-forsaken class.  (I was a linux newbie at the time.  I ended up just doing the work in the University's Sun labs.)

But it seems to me that you are missing a development library.  

```

/usr/bin/ld: cannot find -ldb
collect2: ld returned 1 exit status

```

I actually have to do my development in Windows these days, so I can't check.  But it seems to me that you might need one of the [libdb*-dev packages](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libdb&searchon=names&subword=1&version=edgy&release=all).

---

### Post by penguin007 on 2007-01-07
I also got the same errors using openCOBOL.

If you only need it for a course, I suggest tiny COBOL:

[http://tiny-cobol.sourceforge.net/index.php](http://tiny-cobol.sourceforge.net/index.php)

Works fine.

(Disclaimer: I used to be a COBOL programmer:D , and I teach COBOL and Python at collage. COBOL is cool once you understand what it's used for.)

---

### Post by pmasiar on 2007-01-08
> **penguin007 said:**
> I teach COBOL and Python at college

Interesting place are you in: teaching COBOL, so obsolete for way too long, and Python, just coming in age language. No Java, no C++? :twisted:   If you are so open-minded, you might be interested in [http://en.wikipedia.org/wiki/Game_maker](http://en.wikipedia.org/wiki/Game_maker) - great way for learn programming by creating games.

---

### Post by paxmanchris on 2007-01-08
> **Grey said:**
> [libdb*-dev packages](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libdb&searchon=names&subword=1&version=edgy&release=all).

this work thank you very much...


still wont know for sure if it will work with everything, but for now
it will do.

so, here is how to get open cobol to work:
sudo apt-get install build-essentials
sudo apt-get install open-cobol
sudo apt-get install libdb4.4-dev libncurses5-dev libncursesw5-dev

---

### Post by paxmanchris on 2007-01-09
i put this up on ubuntu guide
[go here]("http://ubuntuguide.org/index.php?title=Ubuntu:Edgy/AddOnApplications&diff=10371&oldid=10370#How_to_install_OpenCobol")

if the how to works for anyone who reads it, you can reply here and let me know:D

---

### Post by penguin007 on 2007-01-10
paxmanchris: OK, all my dirty linen: bash, PHP, Basic (about 5 flavours), C... even some assembler :-)  Thanks for the link.

I rechecked my Ubuntu box this morning, and traced the openCOBOL problem yep, it MUST have libdb4.4-dev - uses the Berkeley DB engine to  do SORT. And no, tinyCOBOL won't run (works fine on my SuSE box, though. And no, no longer have the SuSE box:-)

I think libdb*dev should be put into the dependencies of openCOBOL.

---

### Post by penguin007 on 2007-01-10
Hi paxmanchris: your example in the Guide is slightly off-centre. ALL the lines must start in column 8, including the first line. Strictly speaking, lines 4 and 5 should start in column 12, but that's enough for today's lesson :-)

---

### Post by paxmanchris on 2007-01-11
yikes.. COBOL is crazy. 
well im not going to touch the guide anymore, ill let someone else fix it. thats the beauty of the wiki.

i wonder if i should send a email in the way of official ubuntu people.. to see if i can actuley get them to make the libdb stuff to be depdents of openCOBOL

it would be so cool if they do

---

### Post by penguin007 on 2007-01-20
Yes, I think it would be a Good Idea (TM) to send the maintainers an email.

---

### Post by Lary Grant on 2007-10-24
Hi... I know it is over a year later but I noticed this thread in a search,

I just starting playing around with opencobol... trying to get it to run a program I wrote on a mainframe.

One thing to note is that you must use the -x option to get cobc to generate a standalone executable.  Otherwise it just generates a .so file.

I think the idea behind that default is that if you are porting COBOL to Linux you are more likely wanting to call it from a program with a nice UI than to run it standalone.  However, that default is certainly frustrating to people trying to run a simple test program!

A few problems I ran into...

When I downloaded the test data file from the mainframe, newlines got added to the records.  Opencobol considers those newlines to be part of the record, so I needed to change my FD to be 1 position longer.  Until I did that, the reading was hapenning from the wrong place.

Also, the GOBACK statement does not seem to work the same as on the mainframe.  Opencobol was ignoring it, causing very weird behavior, since instead of exiting the program, control "fell through" to the next statement.

But after all that, it was quite impressive that my Cobol program ran correctly on my Ubuntu machine.

---

### Post by slavik on 2007-10-24
> **pmasiar said:**
> Interesting place are you in: teaching COBOL, so obsolete for way too long, and Python, just coming in age language. No Java, no C++? :twisted:   If you are so open-minded, you might be interested in [http://en.wikipedia.org/wiki/Game_maker](http://en.wikipedia.org/wiki/Game_maker) - great way for learn programming by creating games.
If you want readable self-documented code, you code in COBOL, not Python ;)

There is a reason why Grace Murray Hopper came up with the idea of COBOL, the programmers were lazy when documenting their code. Maybe we should force Microsoft to code in COBOL? ;) I keed!

---

### Post by pmasiar on 2007-10-24
> **slavik said:**
> If you want readable self-documented code, you code in COBOL, not Python ;)

... and if you want non-readable (write-only) code which even author cannot understand after 6 months, by any mean, Perl is the best fit. :-)

---

