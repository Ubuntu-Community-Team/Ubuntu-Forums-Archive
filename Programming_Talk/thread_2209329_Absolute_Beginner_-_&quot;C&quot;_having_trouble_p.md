---
title: "Absolute Beginner - &quot;C&quot; having trouble parsing a string"
date: 2014-03-05
forum: Programming Talk
---

### Post by squakie on 2014-03-05
OK, I've read what I could on the net.  I've read what I could on this in Sam's "Teach Yourself C in One Hour a Day".  So I'm obviously either not understanding what is in those references, or I'm not thinking through the implementation of them in a correct fashion.

My program reads a file via fgets and starts processing it via:```
/************************************************/
/*  Process Juno input type                    **/
/************************************************/        

void input_is_juno()
{

  char my_input_string[my_size];
  char * my_token1;
  char * my_token2;

  my_token1 = malloc(my_size);
  my_token2 = malloc(my_size);

  my_input_string[0] = '\0';
  memset(my_token1, '\0', my_size);
  memset(my_token2, '\0', my_size); 

  while( fgets (my_input_string, my_size - 1, infile) != NULL)
     {

       if (strlen(my_input_string) > 0)
          {

printf("\n\nread: %s\n", my_input_string);
fflush(stdout);
       
            juno_type_parse( my_input_string, my_token1,my_token2); 
printf("\n\nextracted token: %s, with value: %s\n\n", my_token1, my_token2);
fflush(stdout);
          }
       else
          {
             my_token1[0] = '\0';
             my_token2[0] = '\0';
             return;
          }
       if ( 0 == strcmp(my_token1, "Email") )
          {
             strcpy(csv_email, my_token2); 
          }
     }
             
 
}

```


The function " juno_type_parse( my_input_string, my_token1,my_token2); " is intended to:
[LIST]
[*]remove line terminators from the end of my_input_string.  These can include CR and LF since the file can come from Windows. 
[*]find the first ":" in my_input_string 
[*]copy everything from the start of the string up to but not including the ":" to out_token1 
[*]copy everything after the ":" to out_token2 
[/LIST]

The problem is that I can printf the input string and it's length before I try to truncate, but I get the segmention fault before I get to the printf that let's me know it has removed the trailing newline character(s)  So, I suspect some in the truncation is being referenced or counted incorrectly. 

Here's the parsing code:```
/****************************************************
*     Juno - Parse out beginning of line     
*     amd return the token and the resulting data
*     to the end of the line         
****************************************************/


void juno_type_parse(char *in_str, char *out_token1, char *out_token2)
{

    size_t t;
    char x;
    int i;


    /* remove the null terminator */
    t = strlen(in_str);
    i = (int)t;
printf("\n\nstring: %s, length: %d\n\n", in_str, i);
fflush(stdout);

    while (i > -1)
      {
        if ( (in_str[i] == '\n') || (in_str[i] == 0x6D) || (in_str[i] == 0x0A) )
/* change end of line characters to nulls   */
          { 

printf("\n\ntruncating %x\n", in_str[t]);
fflush(stdout);
             in_str[i] = '\0';
          }
        --i;
      }
printf("\n\nstripped string: %s, lenght: %d\n\n", in_str, (int)strlen(in_str));
fflush(stdout);
.
.
.
.
```


Using this file as input:```
dave@davePC:~/juno-address-book$ hexdump -C junk.nv
00000000  54 79 70 65 3a 56 65 72  73 69 6f 6e 0d 0a 56 65  |Type:Version..Ve|
00000010  72 73 69 6f 6e 3a 41 42  20 30 2e 33 2e 30 0d 0a  |rsion:AB 0.3.0..|
00000020  0d 0a 54 79 70 65 3a 45  6e 74 72 79 0d 0a 45 6d  |..Type:Entry..Em|
00000030  61 69 6c 3a 78 78 78 78  40 63 6f 6d 63 61 73 74  |ail:xxxx@comcast|
00000040  2e 6e 65 74 0d 0a 41 6c  69 61 73 3a 0d 0a 4e 61  |.net..Alias:..Na|
00000050  6d 65 3a 66 69 72 73 74  2c 20 6c 61 73 74 0d 0a  |me:first, last..|
00000060  50 72 69 6d 61 72 79 20  50 68 6f 6e 65 3a 0d 0a  |Primary Phone:..|
00000070  42 69 72 74 68 3a 0d 0a  41 64 64 72 65 73 73 3a  |Birth:..Address:|
00000080  0d 0a 44 65 6c 65 74 65  64 3a 30 0d 0a 54 69 6d  |..Deleted:0..Tim|
00000090  65 3a 31 33 30 30 34 34  36 30 35 39 0d 0a 0d 0a  |e:1300446059....|
000000a0  54 79 70 65 3a 45 6e 74  72 79 0d 0a 0d 0a        |Type:Entry....|
000000ae
dave@davePC:~/juno-address-book$ 


```

I get the following on my screen:```
dave@davePC:~/juno-address-book$ ./test junk.nv juno testout gmail-csv


read: Type:Version



string: Type:Version
, length: 14
Segmentation fault (core dumped)
```

Given the printf's I have in the code for trying isolate the problem,  and the resulting output, it must be failing in this:```
    while (i > -1)
      {
        if ( (in_str[i] == '\n') || (in_str[i] == 0x6D) || (in_str[i] == 0x0A) )
/* change end of line characters to nulls   */
          { 

printf("\n\ntruncating %x\n", in_str[i]);
fflush(stdout);
             in_str[i] = '\0';
          }
        --i;
      }
printf("\n\nstripped string: %s, lenght: %d\n\n", in_str, (int)strlen(in_str));
fflush(stdout);
```
Since I never get a "truncating <some hex character>" message.

PLEASE - I need some help on this, not being told to "learn C" or rtfm.  I am doing the absolute best I can do at this time.  If I have some fundamental things wrong, please explain those to me.  I am an ABSOLUTE BEGINNER at this now.

---

### Post by s.fox on 2014-03-05
Removed all caps from thread title :)

---

### Post by squakie on 2014-03-05
BTW - these warnings show up in the compilation - I don't understand what they are saying and why```
dave@davePC:~/juno-address-book$ gcc save-nvconvert.c -o tes
save-nvconvert.c: In function &#8216;juno_type_parse&#8217;:
save-nvconvert.c:375:5: warning: passing argument 2 of &#8216;strchr&#8217; makes integer from pointer without a cast [enabled by default]
     x = strchr(in_str, ":");
     ^
In file included from save-nvconvert.c:63:0:
/usr/include/string.h:232:14: note: expected &#8216;int&#8217; but argument is of type &#8216;char *&#8217;
 extern char *strchr (const char *__s, int __c)
              ^
save-nvconvert.c:375:7: warning: assignment makes integer from pointer without a cast [enabled by default]
     x = strchr(in_str, ":");
       ^
save-nvconvert.c:376:13: warning: comparison between pointer and integer [enabled by default]
     if ( (x != NULL) && (x > 0) )
             ^
dave@davePC:~/juno-address-book$ 
```

---

### Post by trent.josephsen on 2014-03-05
strchr takes an int (as a proxy for a char), but you're passing it a string, which decays to a pointer-to-char.
```
strchr(in_str, ':')
```

---

### Post by steeldriver on 2014-03-05
Instead of reinventing the wheel, how about using the standard strtok function?

If you're just trying to tokenize key:value pairs and spit them back out with comma separators, then there's even no need to strcpy - you can just use strtok to return successive pointers to the (null-delimited) tokens in the input string. I'm rusty on all this so no doubt trent et al will be along to correct any obvious howlers:

```

#include <stdio.h>
#include <string.h>

#define BUFFSZ 128

int main(int argc, char *argv[])
{
  FILE * fp;
  char buf[BUFFSZ];
  char * pChar;

  if ( (fp = fopen(argv[1], "r")) == NULL ) {
    fprintf(stderr, "ERROR: could not open file '%s' for reading\n", argv[1]);
    return 1;
  }
 
  while ( fgets(buf, BUFFSZ, fp) != NULL ) {
    if ( (pChar = strtok(buf, ":\r\n")) != NULL) {
      printf("%s,", pChar);
      if ( (pChar = strtok(NULL, ":\r\n")) != NULL)
        printf("%s\n", pChar);
    }
  }

  return 0;
}

```

```

$ cat myfile
key1:value1
key2:value2
keys can have spaces:so can values
lastkey:lastval

```

```

$ gcc -Wall -o tokenize tokenize.c 
$  
$ ./tokenize myfile
key1,value1
key2,value2
keys can have spaces,so can values
lastkey,lastval

```

---

### Post by squakie on 2014-03-05
Well, since I'm back to being an absolute beginner, I have to tell you I actually didn't know about strtok ;)  That will make life much easier.   I'll give both of these things a try a little later tonight.

Thank you very much!!!!!

---

### Post by squakie on 2014-03-05
Okay, I tried the code.  No warnings in the compilation (yea!).  Here's my function now (I did cut and paste and just substituted my existing field names).  I had to add the initialization of the 2 token2 to '\0' or else the 2nd token was carrying forward garbage.  I added printf's to help me trace if there was a problem:```
void input_is_juno()
{

  char my_input_string[my_size];
  char * my_token1;
  char * my_token2;

  my_token1 = malloc(my_size);
  my_token2 = malloc(my_size);

  my_input_string[0] = '\0';
  memset(my_token1, '\0', my_size);
  memset(my_token2, '\0', my_size); 

 
   while ( fgets(my_input_string, my_size, infile) != NULL )
   {
        my_token1[0] = '\0';
        my_token2[0] = '\0';

        if ( (my_token1 = strtok(my_input_string, ":\r\n")) != NULL)
        {
printf("\ntoken1: %s", my_token1);
            if ( (my_token2 = strtok(NULL, ":\r\n")) != NULL)
            {
printf("\nmy_token2: %s\n", my_token2);
            }
        }
printf("\nresulting outputs: %s, %s\n\n", my_token1, my_token2); 
fflush(stdout);            
   }

   if ( 0 == strcmp(my_token1, "Email") )
   {
      strcpy(csv_email, my_token2); 
   }
 
}
```

Unfortunately, I'm still getting a segmentation fault:[code]resulting outputs: (null), 

Segmentation fault (core dumped)
dave@davePC:~/juno-address-book$ [code]

This is happening on the "blank" lines of the input - in this case the only input read by fgets was CR followed by a LF.

[COLOR=#ff0000][B]EDIT:  I removed a bunch of stuff I originally posted here because it just didn't make sense.  Therefore, I'm leaving out what mind is thinking is happening - which is probably wrong, and waiting on other input. ;)
[/B][/COLOR]
Thanks again!  And if I'm thinking too much, just plain wrong in my thinking, etc., etc., etc., please say so and explain so I have a better understanding.

Thanks!

---

### Post by dwhitney67 on 2014-03-05
strtok() returns a pointer to a location within the string being tokenized, or a pointer to NULL.  When a token is found (in your case, either a colon, a newline or a carriage return), the token is replaced with a NULL character.

Anyhow, in your program you allocated space for the "my_token" variables, and then you turn around and reassign the variables to point elsewhere when the strtok() is performed.  Without a doubt, this is not what you intended.  I recommend that you strtok() the input string and then allocate space for your buffers based on the length of the string returned by strtok().  For example:
```

  char my_input_string[my_size];
  char * my_token1 = NULL;
  char * my_token2 = NULL;

   while ( fgets(my_input_string, my_size, infile) != NULL )
   {
      char * tmp = NULL;

      if ( (tmp = strtok(my_input_string, ":\r\n")) != NULL)
      {
         my_token1 = malloc(strlen(tmp) + 1);
         strcpy(my_token1, tmp);

         if ( (tmp = strtok(NULL, ":\r\n")) != NULL)
         {
            my_token2 = malloc(strlen(tmp) + 1);
            strcpy(my_token2, tmp);
         }
      }

      if (my_token1 != NULL && my_token2 != NULL)
      {
          /* safe to reference these variables for printing or whatever */
      }

      free(my_token1);
      free(my_token2);
   }

```

EDIT:

If you have no plans to use the "my_token" variables outside of the while-loop, then the malloc()/strcpy() steps are moot.  So is the need for the 'tmp' variable.  Just assign the result of the strtok() call directly to the "my_token" variables.  Something like:
```

   while ( fgets(my_input_string, my_size, infile) != NULL )
   {
      my_token1 = strtok(my_input_string, ":\r\n");
      my_token2 = strtok(NULL, ":\r\n");

      if (my_token1 != NULL && my_token2 != NULL)
      {
          /* safe to reference these variables for printing or whatever */
      }
   }

```

P.S.  In lieu of the malloc() and strcpy() combo, you can opt to use strdup().

---

### Post by squakie on 2014-03-05
still no go.  i changed the code i *thought* to be the same but still getting the segmentation fault.  It still has to be where the input string is only CRLF.  Something is either walking off the end of tha stribg via the "If"s, or else I don't know what.```
 
   while ( fgets(my_input_string, my_size, infile) != NULL )
   {
        my_token1[0] = '\0';
        my_token2[0] = '\0';

        if ( (my_token1 = strtok(my_input_string, ":\r\n\x0D")) != NULL)
        {
printf("\ntoken1: %s", my_token1);
fflush(stdout);
            if ( (my_token2 = strtok(NULL, ":\r\n\x0D")) != NULL)
            {
printf("\nmy_token2: %s\n", my_token2);
fflush(stdout);
            }
            else
            {
               my_token2[0] = '\0';
            }
        }
        else
        {
           my_token1[0] = '\0';
           my_token2[0] = '\0';
        }
printf("\nresulting outputs: %s, %s\n\n", my_token1, my_token2); 
fflush(stdout);            
   }
```

yeilds:```
dave@davePC:~/juno-address-book$ ./test junk.nv juno testout gmail-csv

token1: Type
my_token2: Version

resulting outputs: Type, Version

Segmentation fault (core dumped)
dave@davePC:~/juno-address-book$ 
```
where the "record" following one that generated the resulting outputs: Type, Version
 only contains CRLF - no ":" or anything else.  So the first if: ```
        if ( (my_token1 = strtok(my_input_string, ":\r\n\x0D")) != NULL)
```
is failing - I assume because the is nothing before any of the terminators so setting my_token1 to the output of strtok I believe is where it is failing, because there is nothing - no string - coming back from the strtok.  Does that make sense, if so, how to fix it?  I'm in a little over my head here right now.

Thanks!

EDIT:  This is also why I was trying the old loops I had before - I was trying to change those characters to '\0' so I would still have a string - albeit an empty string - coming back, at least that was my intention ;) 

EDIT-EDIT:  since the internal "pointer" in strtok when  goes beyond the end of the input (e.g, it skips ":", CR, Newline (and in my case a probably redundant \x0D [LF]) isn't that internal pointer going beyond the string - we removed everything if the string is only CRLF - there's nothing after that because it's a "DOS" type delimited file.  It would seem to me, but hey I'm asking because I don't have a clue, that it's walking off the end of the input string.

---

### Post by steeldriver on 2014-03-05
You need to get rid of all the **my_token1[0] = '\0'** stuff - in particular, when strtok has exhausted all the tokens in my_input_string, it returns a **pointer to NULL** - and you are then trying to **assign a value to it**

---

### Post by trent.josephsen on 2014-03-05
> **dwhitney67 said:**
> strtok() returns a pointer to **a location within the string being tokenized**, or a pointer to NULL.  When a token is found (in your case, either a colon, a newline or a carriage return), the token is replaced with a NULL character.

(emphasis mine)

Here's a sample program to demonstrate. See if you can predict what it will print before you run it.
```
#include <stdio.h>
#include <string.h>

int main(void)
{
	char buf[] = "email:foo@bar.org";
	char *tok = NULL;

	printf("buffer: <%s>\n", buf);

	if ((tok = strtok(buf, ":\r\n")) != NULL) {
		puts("----------------------------------------");
		printf("token:  <%s>\n", tok);
		printf("buffer: <%s>\n", buf);
	}
	tok[0] = '\0';
	puts("----------------------------------------");
	printf("token:  <%s>\n", tok);
	printf("buffer: <%s>\n", buf);
        return 0;
}
```

---

### Post by squakie on 2014-03-05
> **steeldriver said:**
> You need to get rid of all the **my_token1[0] = '\0'** stuff - in particular, when strtok has exhausted all the tokens in my_input_string, it returns a **pointer to NULL** - and you are then trying to **assign a value to it**

Okay, it looks like this now:```
   while ( fgets(my_input_string, my_size, infile) != NULL )
   {
printf("\n\nInput: %s, length: %d\n\n", my_input_string, (int)strlen(my_input_string));
fflush(stdout);
        if ( (strlen(my_input_string) == 2) 
            && (my_input_string[0] == '\x0d')
            && (my_input_string[1] == '\x0a') )
        {
          break;
        }

        if ( (my_token1 = strtok(my_input_string, ":\r\n\x0a\x0a")) != NULL)
        {
printf("\ntoken1: %s", my_token1);
fflush(stdout);
            if ( (my_token2 = strtok(NULL, ":\r\n\x0d\x0a")) != NULL)
            {
printf("\nmy_token2: %s\n", my_token2);
fflush(stdout);
            }
            else
            {
               my_token2[0] = '\0';
            }
        }
printf("\nresulting outputs: %s, %s\n\n", my_token1, my_token2); 
fflush(stdout);            
   }


```
my input file only has this:```
Type:Version 
Version:AB 0.3.0 
 
Type:Entry 
Email:xxxx@comcast.net 
Alias: 
Name:first, last
Primary Phone: 
Birth: 
Address: 
Deleted:0 
Time:1300446059 
 
Type:Entry 
```
The output from running the program is:```
dave@davePC:~/juno-address-book$ gcc save-nvconvert.c -o test
dave@davePC:~/juno-address-book$ ./test junk.nv juno testout gmail-csv


Input: Type:Version
, length: 14


token1: Type
my_token2: Version

resulting outputs: Type, Version



Input: Version:AB 0.3.0
, length: 18


token1: Version
my_token2: AB 0.3.0

resulting outputs: Version, AB 0.3.0



Input: 
, length: 2

dave@davePC:~/juno-address-book$ 
```
So, the program is stopping after processing the "record" containing the CRLF only.  This is evident by the the last output:  it show a string followed by a comma, and since the comma is on a newline, the string contains the CRLF.  It also knows it's length is 2.  It never gets to the printf's showing it has parsed that input.  It also never goes back to get the next "record".

No segmentation fauilt, but not the correct result either.  What am I not understanding?  My head knows from my years ago experience it should be simple - really simple.  But my knowledge all disapeared in the 20 years it's been since I was working.  I *think* I know how to do something but obviously not.

Remember - a true beginner again here ;)  Can you tell me what I'm "missing" in how this works?

Thanks again!


EDIT:  ok, for this code, it is my fault - I had put a temporary check in for CRLF as the only thing in the input and put in a break, which exited the while with the fgets.  I'll be taking that out and trying again.  Sorry!

---

### Post by squakie on 2014-03-05
I thought I should note that my previous post had an "x" instead of the code snippet.  I went back in and put in the code snippet, in case anyone had only gotten the "x" instead of the code.

---

### Post by squakie on 2014-03-05
I would think the first printf would output "email",  while the 2nd would be "foo@bar.org".

Now, what happens when the entire buf is replace with '\x0d' and '\x0a' ?

And, if the buf was actually coming from a fgets, and there are more "records" to follow, what happens?

---

### Post by squakie on 2014-03-05
Ok, I'm just getting problem after problem.  I changed my code:```
 
   while ( fgets(my_input_string, my_size, infile) != NULL )
   {
printf("\n\nInput: %s, length: %d\n\n", my_input_string, (int)strlen(my_input_string));
fflush(stdout);


        if ( (my_token1 = strtok(my_input_string, ":\r\n\x0a\x0a")) != NULL)
        {
printf("\ntoken1: %s", my_token1);
fflush(stdout);
            if ( (my_token2 = strtok(NULL, ":\r\n\x0d\x0a")) != NULL)
            {
printf("\nmy_token2: %s\n", my_token2);
fflush(stdout);
            }
            else
            {
               my_token2[0] = '\0';
            }
        }
printf("\nresulting outputs: %s, %s\n\n", my_token1, my_token2); 
fflush(stdout);
```

my_token2 is not getting "cleared" when it loops back to the fgets.  I put the "else" after the attempt to get the 2nd token so that if the strtok returns a "pointer to NULL" (I hate to admit, but I don't really understand that - I thought that the token would be an empty null terminated string), I force token2 to be a null terminated empty string.  However, something is amiss with my understanding of how this is working yet, so the string isn't getting cleared.  It still has the previous value in it instead of the null terminated string it should have when the input string is CRLF.

So I get the segmentation fault again:```
    dave@davePC:~/juno-address-book$ gcc save-nvconvert.c -o test
dave@davePC:~/juno-address-book$ ./test junk.nv juno testout gmail-csv


Input: Type:Version
, length: 14


token1: Type
my_token2: Version

resulting outputs: Type, Version



Input: Version:AB 0.3.0
, length: 18


token1: Version
my_token2: AB 0.3.0

resulting outputs: Version, AB 0.3.0



Input: 
, length: 2


resulting outputs: (null), AB 0.3.0

Segmentation fault (core dumped)
dave@davePC:~/juno-address-book$ 
```

I just don't understand - obviously.  I still think it's centered on having nothing more in the input string (it should have been converted to 2 '\0' characters.  But I still think this is messing up the parse on the 2nd strtok. I just don't see how, and I don't see how my "else" after the 2nd strtok isn't setting token2 to an empty string.

---

### Post by dwhitney67 on 2014-03-06
A couple of thoughts... First, declare a const char pointer for your delimeter (it seems you have inconsistent values).  Second, post your data file (from Windows land), removing any personal identifiable information.  Don't post the contents, but the actual file itself (you may need to change the file extension to ".txt").

```

const char* delimeter = ":\n\r";
char buffer[256];

while (fgets(buffer, sizeof(buffer), file) != NULL)
{
    char* my_token1 = strtok(buffer, delimeter);
    char* my_token2 = strtok(NULL, delimiter);

    printf("my_token1 = %s   my_token2 = %s\n",
            (my_token1 == NULL ? "NULL" : my_token1),
            (my_token2 == NULL ? "NULL" : my_token2));
}

```

---

### Post by trent.josephsen on 2014-03-06
[quote=The New Hacker's Dictionary]shotgun debugging: n.

    The software equivalent of Easter egging; the making of relatively undirected changes to software in the hope that a bug will be perturbed out of existence. This almost never works, and usually introduces more bugs.[/quote]
Do you not see a problem with the following code?
```
            if ( (my_token2 = strtok(NULL, ":\r\n\x0d\x0a")) != NULL)
            {
printf("\nmy_token2: %s\n", my_token2);
fflush(stdout);
            }
            else
            {
               my_token2[0] = '\0';
            }
```

(aside: the way you're unindenting the printfs makes it harder to read your code. I suggest not doing that.)

---

### Post by squakie on 2014-03-06
Nope - don't see what's wrong - if I did I wouldn't have to ask for help ;)

I still think it has to do with the record containing only CRLF and that's it.  

As for the input file, the entire input file I'm testing with (the "real" one is way too big) is already posted above in hex and with the text next to it (-C option on hexdump).  It's the way I was used to getting dumps of files and memory a long, long time ago, so please forgive me if there's supposed to be another way.  This is the "DOS"-type delimited file - hence the CR and LF's (0d and 0a).  This is a snippet of the real file (but I did go back and change the personal data - thank you!).

EDIT:  Since you pointed out my accidental posting of personal data, I'll save you have to go back to the very first post and put the hexdump output here:

dave@davePC:~/juno-address-book$ hexdump -C junk.nv
00000000  54 79 70 65 3a 56 65 72  73 69 6f 6e 0d 0a 56 65  |Type:Version..Ve|
00000010  72 73 69 6f 6e 3a 41 42  20 30 2e 33 2e 30 0d 0a  |rsion:AB 0.3.0..|
00000020  0d 0a 54 79 70 65 3a 45  6e 74 72 79 0d 0a 45 6d  |..Type:Entry..Em|
00000030  61 69 6c 3a 78 78 78 78  40 63 6f 6d 63 61 73 74  |ail:xxxx@comcast|
00000040  2e 6e 65 74 0d 0a 41 6c  69 61 73 3a 0d 0a 4e 61  |.net..Alias:..Na|
00000050  6d 65 3a 66 69 72 73 74  2c 20 6c 61 73 74 0d 0a  |me:first, last..|
00000060  50 72 69 6d 61 72 79 20  50 68 6f 6e 65 3a 0d 0a  |Primary Phone:..|
00000070  42 69 72 74 68 3a 0d 0a  41 64 64 72 65 73 73 3a  |Birth:..Address:|
00000080  0d 0a 44 65 6c 65 74 65  64 3a 30 0d 0a 54 69 6d  |..Deleted:0..Tim|
00000090  65 3a 31 33 30 30 34 34  36 30 35 39 0d 0a 0d 0a  |e:1300446059....|
000000a0  54 79 70 65 3a 45 6e 74  72 79 0d 0a 0d 0a        |Type:Entry....|
000000ae
dave@davePC:~/juno-address-book$ 



Thanks! ;)

---

### Post by squakie on 2014-03-06
Forgot to mention - the only reason the printf's aren't indented is that I wanted to tell myself they were "debugging" statements.  I suppose there's no reason not to indent and just search on "printf" when the code is working and I don't need them anymore.  Sorry if that made it hard to read ;)

---

### Post by dwhitney67 on 2014-03-06
I just realized (and I should have earlier) that I can create a text file that is similar to yours, and either use it in the Linux format, or make it a Windoze format using unix2dos.

Anyhow, using this data:
```

Type:Entry
Email:myemal@mine.com
Alias:
Name:Foo Manchoo
Primary Phone:800-5551212
Birth:04/01/1950
Address:123 Main Street, Anywhere, USA 12345
Deleted:0
Time:1300446059

```

Which appears as such if ingested by hexdump:
```

00000000  54 79 70 65 3a 45 6e 74  72 79 0d 0a 45 6d 61 69  |Type:Entry..Emai|                      
00000010  6c 3a 6d 79 65 6d 61 6c  40 6d 69 6e 65 2e 63 6f  |l:myemal@mine.co|                      
00000020  6d 0d 0a 41 6c 69 61 73  3a 0d 0a 4e 61 6d 65 3a  |m..Alias:..Name:|                      
00000030  46 6f 6f 20 4d 61 6e 63  68 6f 6f 0d 0a 50 72 69  |Foo Manchoo..Pri|
00000040  6d 61 72 79 20 50 68 6f  6e 65 3a 38 30 30 2d 35  |mary Phone:800-5|
00000050  35 35 31 32 31 32 0d 0a  42 69 72 74 68 3a 30 34  |551212..Birth:04|
00000060  2f 30 31 2f 31 39 35 30  0d 0a 41 64 64 72 65 73  |/01/1950..Addres|
00000070  73 3a 31 32 33 20 4d 61  69 6e 20 53 74 72 65 65  |s:123 Main Stree|
00000080  74 2c 20 41 6e 79 77 68  65 72 65 2c 20 55 53 41  |t, Anywhere, USA|
00000090  20 31 32 33 34 35 0d 0a  44 65 6c 65 74 65 64 3a  | 12345..Deleted:|
000000a0  30 0d 0a 54 69 6d 65 3a  31 33 30 30 34 34 36 30  |0..Time:13004460|
000000b0  35 39 0d 0a                                       |59..|
000000b4

```

Can be processed using:
```

#include <string.h>
#include <stdio.h>

int main(int argc, char** argv)
{
    if (argc != 2)
    {
        fprintf(stderr, "Usage: %s <data file>\n", argv[0]);
        return -1;
    }

    FILE* file = fopen(argv[1], "r");

    if (file)
    {
        char buffer[256];

        while (fgets(buffer, sizeof(buffer), file) != NULL)
        {
            char* my_token1 = strtok(buffer, ":\n\r");
            char* my_token2 = strtok(NULL, ":\n\r");

            printf("my_token1 = %s   my_token2 = %s\n",
                (my_token1 == NULL ? "NULL" : my_token1),
                (my_token2 == NULL ? "NULL" : my_token2));
        }
    }
    else
    {
        fprintf(stderr, "Cannot open file %s.\n", argv[1]);
        return -1;
    }
    return 0;
}

```
Output will appear as:
```

my_token1 = Type   my_token2 = Entry                                                                
my_token1 = Email   my_token2 = myemal@mine.com                                                     
my_token1 = Alias   my_token2 = NULL                                                                
my_token1 = Name   my_token2 = Foo Manchoo                                                          
my_token1 = Primary Phone   my_token2 = 800-5551212                                                 
my_token1 = Birth   my_token2 = 04/01/1950                                                          
my_token1 = Address   my_token2 = 123 Main Street, Anywhere, USA 12345                              
my_token1 = Deleted   my_token2 = 0                                                                 
my_token1 = Time   my_token2 = 1300446059

```

---

### Post by squakie on 2014-03-06
That looks good.  Could you try it with a blank line between any of the existing lines?  That seems to be when it has always caused another segmentation fault.   After the processing of the terminators, the entire input string would be empty (I'm assuming that it still null terminates the string? ).  The first value - my_token1 - always comes out ok (prints as (null) ), but the second strtok causes a problem then.  I think I know why, but I don't know how to code for it:I think the internal "pointer" (still remembered with null on the second call to strtok)is pointing beyond the end of the string.  I don't know how to prove it though.

So, if you wouldn't mind trying a blank "line" (just the DOC terminators CR and LF) between 2 of the "records" and retest, I would appreciate it.  Once I know that works, then I will bring the code over into my program and look at it again to be sure I understand it.  I think I understand it all now except for one thing, which I just can't get straight even looking up strtok:  is the output string of strtok null terminated  when the input string is empty?

Also - I *thought* I remembered something about the newline terminator in linux being different from the newline terminator in DOS/Windows.  In particular I thought linux's terminator is is single character, while the DOS/Windows one is obviously 2 - CR/LF.  Does the code cover a x0d and x0a?  I see it checking newline via \n, but isn't that going to have the linux 1-character representation instead of the DOS/Windows 2-character representation?

---

### Post by trent.josephsen on 2014-03-06
> **squakie said:**
> Nope - don't see what's wrong - if I did I wouldn't have to ask for help ;)
What if I wrote it like this?
```
my_token2 = strtok(NULL, ":\r\n\x0d\x0a");
if (my_token2 == NULL)
{
    my_token2[0] = '\0';
}
else
{
    printf("\nmy_token2: %s\n", my_token2);
    fflush(stdout);
}
```

---

### Post by squakie on 2014-03-06
> **trent.josephsen said:**
> What if I wrote it like this?
```
my_token2 = strtok(NULL, ":\r\n\x0d\x0a");
if (my_token2 == NULL)
{
    my_token2[0] = '\0';
}
else
{
    printf("\nmy_token2: %s\n", my_token2);
    fflush(stdout);
}
```



I think this comes down to the question I had about strtok - *if* it null terminates the output string, even when the inpu string is empty (strlen 0) after removing the terminators, then I woudn't need the extra set of my_token2 to a null.  This is one of those things I haven't found the answer for in the references - they all say "NULL" is returned from the call, but I don't know if token =... will then make the token null.

Now consider that the input string only contains a CR and a LF.  The first token will come out as null, but the second token, at least in my previous tests, ends up walking past the end of the string.  What happens?

---

### Post by squakie on 2014-03-06
> **trent.josephsen said:**
> (emphasis mine)

Here's a sample program to demonstrate. See if you can predict what it will print before you run it.
```
#include <stdio.h>
#include <string.h>

int main(void)
{
    char buf[] = "email:foo@bar.org";
    char *tok = NULL;

    printf("buffer: <%s>\n", buf);

    if ((tok = strtok(buf, ":\r\n")) != NULL) {
        puts("----------------------------------------");
        printf("token:  <%s>\n", tok);
        printf("buffer: <%s>\n", buf);
    }
    tok[0] = '\0';
    puts("----------------------------------------");
    printf("token:  <%s>\n", tok);
    printf("buffer: <%s>\n", buf);
        return 0;
}
```
I'm confused on this as well.  If null, it returns a pointer to a null.  So the output string contains a pointer and not just the line terminator?  I just want the strlen of the output string to be 0, so I would want the output string to contain '\0', not a pointer.  So I'm not understanding this as well.  Any help in understanding this would be greatly appreciated ;)

---

### Post by steeldriver on 2014-03-06
I think your fundamental issue is not understanding the difference between a **NULL pointer-to-char** and a **pointer to a NULL char**

A **NULL pointer (to-char** or to any other type) is a special memory address that says 'nothing to see here, this address does not contain a valid object' whereas a **pointer to a NULL char** is a regular valid memory address that happens to contain a zero-value byte '\0' - which (since that is how C denotes the end of a string) is equivalent to an empty string. **It is an error to attempt to assign a value to the NULL pointer**, as you are doing here:```

if (my_token2 == NULL) /* this is a NULL POINTER (i.e. an unreachable ADDRESS) */
{
    my_token2[0] = '\0'; /* this is a NULL CHARACTER (i.e. a zero-value byte) */
}

```

---

### Post by squakie on 2014-03-06
so does this mean the token actually has the terminator?  I ask this because I use those values elsewhere, not expecting any kind of pointer or anything, just a normal '\0' terminated string, so that strcpy of the token to another string will actually result in the string being simple empty  as in a null-terminated string with nothing in it (length of 0).

You are absolutely correct in saying I don't understand this! ;)

---

### Post by squakie on 2014-03-07
If I'm reading what you are saying correctly, the output string has just the '\0' - a string terminator, so the length of that string would be 0, and any reference to it - such as in an strcpy, would result in it being treated as an "emtpy" string.

---

### Post by squakie on 2014-03-07
Okay, I tried the code - it didn't segment fault, that is until I actually tried do something with the output strings:```
oid input_is_juno()
{

  char file_buffer[my_size];
  const char* delimeter = ":\n\r";


  my_token1 = malloc(my_size);
  my_token2 = malloc(my_size);
 
  while (fgets(file_buffer, sizeof(file_buffer), infile) != NULL)
  {
      my_token1 = strtok(file_buffer, delimeter);
      my_token2 = strtok(NULL, delimeter);
  
/*      if (0 == strcmp(my_token1, "Email") )
      {
         printf("\nAt email, token1: %s\n", my_token1);
         fflush(stdout);
         printf("\nAt email, token2: %s\n", my_token2);
         fflush(stdout);
         strcpy(csv_email, my_token2);
         printf("\nCopied email address\n");
         fflush(stdout);
      }   */
  }
```  If I try to actually do something with the strings - my_token1 and my_token2 - then I get a segment fault right away, none of the trace printf's show up:```
oid input_is_juno()
{

  char file_buffer[my_size];
  const char* delimeter = ":\n\r";


  my_token1 = malloc(my_size);
  my_token2 = malloc(my_size);
 
  while (fgets(file_buffer, sizeof(file_buffer), infile) != NULL)
  {
      my_token1 = strtok(file_buffer, delimeter);
      my_token2 = strtok(NULL, delimeter);
  
      if (0 == strcmp(my_token1, "Email") )
      {
         printf("\nAt email, token1: %s\n", my_token1);
         fflush(stdout);
         printf("\nAt email, token2: %s\n", my_token2);
         fflush(stdout);
         strcpy(csv_email, my_token2);
         printf("\nCopied email address\n");
         fflush(stdout);
      }  
  } 
``` Results in:```
dave@davePC:~/juno-address-book$ gcc save-nvconvert.c -o test
dave@davePC:~/juno-address-book$ ./test junk.nv juno testout gmail-csv
Segmentation fault (core dumped)
dave@davePC:~/juno-address-book$ 
```

So, either the strings are invalid, or I don't see how I'm doing anything stupid by trying to copy the strings.

Help??  ;)

---

### Post by squakie on 2014-03-07
I slightly modified the code - I put in a printf to trace what the values are after the parsing.  It shows correct, and the program runs without a segmentation fault.  However, I had to remove the string compare and instead do a test of "if (my_token1 == "Email")".  It never passes this test as the printf for tracing inside the "if" where I check the value of my_token1 never happens.{code]  while (fgets(file_buffer, sizeof(file_buffer), infile) != NULL)
  {
      my_token1 = strtok(file_buffer, delimeter);
      my_token2 = strtok(NULL, delimeter); 

      printf("\nfound tokens: %s, %s\n", my_token1, my_token2);
      fflush(stdout);
  
      if ( my_token1 == "Email" )
      {
         printf("\nAt email, token1: %s, %s\n", my_token1, my_token2);
         fflush(stdout);
         printf("\nAt email, token2: %s\n", my_token2);
         fflush(stdout);
         strcpy(csv_email, my_token2);
         printf("\nCopied email address\n");
         fflush(stdout);
      } 
  }[/code]
Snippet of output - to show what happens (and doesn't happen) when my_token1 contains "Email" (at least it *should*): ```
found tokens: Type, Version

found tokens: Version, AB 0.3.0

found tokens: (null), (null)

found tokens: Type, Entry

found tokens: Email, xxxx@comcast.net

found tokens: Alias, (null)
```

I have got to be the stupidest person on the face of the earth as I'm just not getting any of this now.  I understand the 2 strtok's, and understand the resulting values (and yes to my question, the "record" containing on \x0d\x0a did really parse out correctly.  I really don't understand how a strcmp can cause the segmentation fault, and when I replaced it with the "if", I don't understand why the condition of the "if" isn't met when indeed my_token1 is "Email" (as shown by the tracing printf after the 2 strtok's).

I'm sorry I'm so dang stupid.  I don't know if unconsiously my mind is trying to figure out something from what I *used* to know, which would all now be no good, and mixing it in with the code, or if I'm just being that stupid.

Any help is again greatly appreciated.

BTW Steeldriver - I see what you were getting at with setting my_token1[0] to \0 - if the string is null, there IS NO my_token1[0], correct?  So I was addressing something I shouldn't have been.

---

### Post by squakie on 2014-03-07
I think I still have a bad, or perhaps more accurately, lack of understanding on what is actually in the output string when strtok doesn't find anything in the string except what it is deleting.  So, can someone explain to me in real simple terms:  if the result of strtok is NULL, what, if anything is in the output string?  I thought it would be '\0'.  However, when I try to get the strlen of a string I know definetly has nothing in it, I get a segmentation fault.  Can't I use any string functions on the output?  If not, then I need to know how to code for it - do I say something like:```
if (my_token1 != NULL)......
```?

---

### Post by squakie on 2014-03-07
I think I still have a bad, or perhaps more accurately, lack of understanding on what is actually in the output string when strtok doesn't find anything in the string except what it is deleting.  So, can someone explain to me in real simple terms:  if the result of strtok is NULL, what, if anything is in the output string?  I thought it would be '\0'.  However, when I try to get the strlen of a string I know definetly has nothing in it, I get a segmentation fault.  Can't I use any string functions on the output?  If not, then I need to know how to code for it - do I say something like:```
if (my_token1 != NULL)......
```?

---

### Post by squakie on 2014-03-07
Okay, I tried checking each token agains NULL before accessing it:```
      if (my_token1 != NULL)
      {  
              if ( 0 == (strcmp(my_token1, "Email")))
               {
                  printf("\nAt email, token1: %s, %s\n", my_token1, my_token2);
                  fflush(stdout);
                  printf("\nAt email, token2: %s\n", my_token2);
                  fflush(stdout);
                  if (my_token2 != NULL)
                  {
                     strcpy(csv_email, my_token2);
                  }
                  printf("\nCopied email address\n");
                  fflush(stdout);
              }
     } 
```

This seems to work now - I'm getting the printf's as I should for the "Email" entry, and it copies the email address to csv-email, and as result of the rest of the code the output "record" got written and it contained exactly what it should!  So, now I just need to process the rest of the possiblities in my_token1.  And I guess this answers my question - the output string from strtok DOES NOT contain '\0', instead it is what ever this pointer to null business is about - and I definetly don't understand that.  I just know that checking for != NULL prior to trying to anything string related seems to work.

So, obviously I didn't know what the h e double-toothpicks I was doing when I wrote the code the 1st and 2nd and , well you know, times.  I have a little better understanding of what's going on and why, still don't understand that pointer to NULL stuff at all. ;)

---

### Post by squakie on 2014-03-07
Well, I ran into a dumb problem, and I mean in dumb in that I just don't see a coding error which is stopping from compiling now.  All I've done is added a series of "elseif"s to process the rest of the possibilities of my_token1.  Now it fails in compilation at:
```
      if (my_token1 != NULL)
      { 
              if ( 0 == (strcmp(my_token1, "Email")))
              {
                  if (my_token2 != NULL)
                  {
                     strcpy(csv_email, my_token2);
                  }
              }
              elseif ( 0 == (strcmp(my_token1, "Alias")))
              {
              ^
               |  with: save-nvconvert.c:275:15: error: expected &#8216;;&#8217; before &#8216;{&#8217; token 
```

Maybe it's because it's late and I need to be up in 3.5 hours to drive 250 miles, but more likely I'm being dumb again.  At least things have gotten this far! 
Help???  ;) ;)

Thanks again!

---

### Post by spjackson on 2014-03-07
The problem is elseif. There needs to be a space between the else and the if.

---

### Post by squakie on 2014-03-07
Oh man, it must have been getting too late!  Can't believe I did that as that is one I actually did know ;)

Thanks!

---

### Post by squakie on 2014-03-07
Okay, I want to extend a BIG THANK YOU to everyone who has contributed here!  You stayed patient with a very befuddled person and helped me get everything over to strings, in code I do understand now.  It made thins MUCH more compact and easier to follow and modify.

I really can't thank you all enough.  I never would have figured out that NULL stuff (at least, I *think* I understand it now ;) ) and would never have gotten it working.

If any of you are interested, this program actually has some use, at least for me ;)  My brother in-law's PC has been bitten thanks to Conduit, and it is running TERRIBLE - and that's when it even lets you TRY to do anything.  He still uses Juno, and Juno has now refused to start, so I'm converting him over to Gmail for now (working on converting him to Ubuntu, but it's a hard sell ;) ).

This program reads the few known tokens I see in his Juno address book and can creates a comma-seperated-values file in Gmail or Thunderbird format.  I am now working on adding Yahoo! online email as well.  That won't take long.

So what you've all been an invaluable help on is parsing the input address book known entries and storing the values.  From there, it's a simple matter to create the CSV files for import into the various email clients.  If anyone would have a need for it I have a thread open in the Ubuntu forums for it and will keep adding the updated code at the end as things are added.

I truely can't thank you enough.

I'll be closing this, since this problem is solved.  I may open other threads with more dumb questions - just remember how green I am and help like all have in this thread.  It's greatly appreciated!

Dave ;)

---

