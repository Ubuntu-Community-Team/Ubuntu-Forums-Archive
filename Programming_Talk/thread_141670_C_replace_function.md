---
title: "C replace function"
date: 2006-03-08
forum: Programming Talk
---

### Post by zootreeves on 2006-03-08
Is there a function in C to replace a string within a string, like php's str_replace()? I need to replace ' with &#145; before an sql query.

---

### Post by hod139 on 2006-03-08
If you mean [c++ std::string]("http://www.cppreference.com/cppstring/index.html"), then there is a [replace]("http://www.cppreference.com/cppstring/replace.html") command

---

### Post by zootreeves on 2006-03-08
No i'm using plain C.

I'm having a go writing one myself, but it just produces seg faults.

```
    char string[100];
    char newstring[100];
    strcpy(string, "This is my string with ' in it");

          x = 0;
           while (string[x]) {
            if (strcmp(string[x], "'")) {
               printf("%s", string[x]);
             }
           x++;
           } 
```

---

### Post by rplantz on 2006-03-08
[QUOTE=zootreeves]```

            if (strcmp(string[x], "'")) {
               printf("%s", string[x]);
             }
           x++;
           } 
```[/QUOTE]

Both arguments to strcmp must be char *. string[x] is a char. I think you want something like
```

        if (string[x] == (char)39)

```
39 is the decimal value of the ' character.

Also, %s requires a string pointer. So you should use
```

        printf("%c", string[x]);

```

---

### Post by hod139 on 2006-03-08
I just whipped this up.

```

#define MAX_STR_LENGTH 100

int main(void)
{
  char string[MAX_STR_LENGTH]="This is my string with ' in it";
  char newstring[MAX_STR_LENGTH]; // Holder for copy of string

  printf (" original string contents are: %s\n", string);

  // Copy first MAX_STR_LENGTH characters into newstring
  strncpy(newstring, string, MAX_STR_LENGTH); 
  //explicitly set the last byte of the buffer to 0 after calling strncpy
  newstring[MAX_STR_LENGTH - 1] = 0; 

  unsigned int i = 0;
  for(i = 0; i < MAX_STR_LENGTH; ++i){
     if (newstring[i] == '\''){  // Look for a '
         newstring[i] = '`'; // replace with a `
     }
  }

  printf (" new string contents are: %s\n", newstring);
}

``` 
I use strncpy, not strcpy, it is slightly safer but you still have to null terminate it. I then check for the character ', not a string. Hope this helps. Let me know if you have any questions about it.

---

### Post by zootreeves on 2006-03-08
Thanks for the help it's working perfectly now. I don't think i'm ever going to go back to php, C is so much better.

---

### Post by sapo on 2006-03-08
[QUOTE=zootreeves]Thanks for the help it's working perfectly now. I don't think i'm ever going to go back to php, C is so much better.[/QUOTE]
I think you just say this cause you didnt try python yet :mrgreen:

---

### Post by hod139 on 2006-03-08
Uh Oh... Are we about to get into a language debate.  I've been a fan of Java lately, but would suggest almost any other language but C for string processing.  The str* commands are just horrible.

---

### Post by jerome bettis on 2006-03-08
```
void strrep(char *str, char old, char new)  {
    char *pos;
    while (1)  {
        pos = strchr(str, old);
        if (pos == NULL)  {
            break;
        }
        *pos = new;
    }
}
```

---

### Post by hod139 on 2006-03-08
[quote=jerome bettis]```
void strrep(char *str, char old, char new)  {
    char *pos;
    while (1)  {
        pos = strchr(str, old);
        if (pos == NULL)  {
            break;
        }
        *pos = new;
    }
}
```[/quote]

I have 2 problems with this code.  First, while(1) loops are always dangerous.  They are a potential infinite loop, no matter how good the programmer is. Second, this function only replaces the first occurence of the char, not all of them.

---

### Post by jerome bettis on 2006-03-08
[quote=hod139]I have 2 problems with this code.  First, while(1) loops are always dangerous.  They are a potential infinite loop, no matter how good the programmer is. Second, this function only replaces the first occurence of the char, not all of them.[/quote] 
no it replaces all of them, try it.   what do you think the loop is there for?

i disagree with you about the while (1). saying while (whatever) {} vs while (1) { if (whatever) break; } are the same thing in this context.

---

### Post by hod139 on 2006-03-09
> try it. what do you think the loop is there for? Did you even try running your code? It doesn't run, it seg faults. I rewrote your code so it wouldn't segfaul, and was actually very surprised that it did replace all the chars. It took me some time to realize why.

The following code block is how I would have written the loop.
```

#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int main( )
{
    char string[]={"this is a string"};

    char searchchar = 'i';
    char replacechar = 'X';
    char *valueptr; // will store pointer retrieved from strchr 

    valueptr = strchr(string, searchchar);
    if(valueptr != NULL) // Check for NULL
         *valueptr = replacechar;
    
    // Loop until end of string
    while (valueptr !=NULL) {
        valueptr = strchr(valueptr + 1, searchchar);
        if(valueptr != NULL) // Check for NULL
             *valueptr = replacechar;
    }

    printf (" new string contents are: %s\n", string);
    return 0;
}

``` 
As you can see in my code, future calls to strchr take for arguments (valueptr + 1, searchchar).  Your loop is doing this:
```

valueptr = strchr(str, searchchar);
*valueptr = replacechar;
valueptr = strchr(str, searchchar);
*valueptr = replacechar;
repeat

``` It took me a while to realize that this approach does actually work, and it does only because you were replacing the char with something different so a subsequent call with the altered string will find the next char to replace. One downside is that you wrote an O(n^2) algorithm, when you only need a linear one.

> 
i disagree with you about the while (1). saying while (whatever) {} vs while (1) { if (whatever) break; } are the same thing in this context.
 
Your code is a good example why while(1) is bad practice. Your code would enter an infinite loop if the old and new chars were the same. Mine won't.

---

### Post by jerome bettis on 2006-03-09
of course i tried it, no segfaults if you initialize the string properly.  i like the + 1 thing instead of starting at the beginning, that's much better

> Your code would enter an infinite loop if the old and new chars were the same. Mine won't. 

true, but that's not because of the while(1).  the only reason your's isn't infinite is because you did strchr(x  + 1, y) instead of strchr(str, y).  again, the logic of while(1) { if (something) break; } vs while (!something)  {} is the same.  i'm not sure why you don't understand that, it's just another way of writing something, they work the same way.  

if strchr doesn't return null for you your's will be infinite, as will mine.  if the characters are the same and we use the +1, it will return null when it gets to the \0 eventually.  but if we start at the beginning every time it will get stuck, no matter how you write the loop.  so we don't have to check the characters, but we will anyway cause it's stupid not too.  

here's a better version.  i'm sure there's still lots of things to improve, lets stop the pissing match and make this good.

```
#include <stdio.h>
#include <string.h>
#define MAX_STR_LEN 100

void strrep(char *str, char old, char new)  {
    if (new == old) {
        return;
    }
    char *pos = strchr(str, old);
    while (pos != NULL)  {
        *pos = new;
        pos = strchr(pos + 1, old);
    }
}

int main(int argc, char* argv[])  {
    char str[MAX_STR_LEN];
    memset(str, 0, MAX_STR_LEN);
    strcpy(str, "ab''ab'ab''ab''a");
    printf("Before: %s\n", str);
    strrep(str, '\'', '`');
    printf("After: %s\n", str);
    return 0;
}
```

---

### Post by hod139 on 2006-03-09
[quote=jerome bettis]wrong, your's still will be infinite. [/quote] 
Why would mine be infinite?  I replace the char at index i, then continue searching starting at index 1+1.  

> 
again, the logic of while(1) { if (something) break; } vs while (!something) {} is the same. i'm not sure why you don't understand that, it's just another way of writing something, they work the same way
 This isn't quite right. In the former, you have to catch all somethings, and hope you didn't miss one (like you did in your first code example of old char == new char). In the latter, you are specifically stating the something that conditions termination (In my code I performed a single loop over the string, and can guarentee finish).

I'm getting too tired to form good arguments against while(true) loops, but I'll do my best. For one, it conveys no information about what the loop is doing. It is like writing for( ; ; ). The other problem is that try as hard as you like, you can't prove loop termination. You set up a loop without a termination condition, and have to hope that you were smart enough to catch and break for all possible somethings. With the termination conditions in the while loop, you can use loop invariant analysis to prove "correctness" and termination. Including the conditions also improves maintainability and readability of the code. The argument is similar to why not to use goto, the code becomes unstructured. 

Ultimitely, it may come down to personal taste. If I have a loop, I want to know what it is doing, and what the exit condition is.

---

### Post by rplantz on 2006-03-09
And I would have done something like:
```

#include <stdio.h>

int main( )
{
    char string[]={"this is a string"};

    char searchchar = 'i';
    char replacechar = 'X';
    char *ptr;    // current position in string

    ptr = string;
    // Loop until end of string
    while (*ptr != '\0') {
        if(*ptr == searchchar)
             *ptr = replacechar;
        ptr++;
    }

    printf (" new string contents are: %s\n", string);
    return 0;
}

```
which doesn't require any library calls. I suppose this shows my background in assembly language programming.

---

### Post by zootreeves on 2006-03-09
I've being playing around with this a bit more. I now need to replace the single quote, with \'. I have the working function below, but I have couple of questions.


```
      char string[100];
      char newstring[100];
      int loop_number;
      /* array of directory parts */
      char matches_array[8][100];

      strcpy(matches_array[0], "My first ' string  'is:");
      strcpy(matches_array[1], "My 2nd string  '"); 
      strcpy(matches_array[2], "My 3rd string which is ' longer '");
      strcpy(matches_array[3], "My 4th short ' longer '");


                               /* For some reason you have to empty the strings first */
                               /* Empty string */
                               for (x=0; x < 100; ++x) {
                               string[x] = NULL;
                               }
                               
                               for (x=0; x < 100; ++x) {
                               newstring[x] = NULL;
                                }

                                /* Replace add a \ before any ' */
                                /* matches_array seems to have another value (which is less than 5 chars, I don't know what it is but i don't want to process it */
                           for(loop_number=0; strlen(matches_array[loop_number]) > 5; ++loop_number) {
                            printf("Processing %s \n", matches_array[loop_number]);
                            strcpy(string, matches_array[loop_number]);
                            for(x = 0; x < strlen(matches_array[loop_number]); ++x){
                              if (string[x] == '\''){  // Look for a '
                                                newstring[x] = '\\';
                                                /* Assign the next character in the string the ' */
                                                newstring[x + 1] = '\'';
                                                /* increse x by one because the string has gained a new character */
                                                x++;
                                                } else {
                                                /* if it didn't match just put it straight into the new string */
                                                newstring[x] = string[x];
                                                }
                               }
                               /* copy the procesed string to the array */
                               strcpy(matches_array[loop_number], newstring);

                               /* Empty the strings again because the next value in the array might be shorther than this one */
                               /* Empty string */
                               for (x=0; x < 100; ++x) {
                               string[x] = NULL;
                               }                               
                               for (x=0; x < 100; ++x) {
                               newstring[x] = NULL;
                                }
                                
                                /* Print the new value */
                                 printf ("New String is: %s \n\n", matches_array[loop_number]);
                               }

```

Why do i have to NULL the values of string & newstring the first time. I have only just assigned them, so surely they should already be empty? If i do not null them i get a bunch of wierd characters at the end of the first processed string.

I have only assigned 4 values to the matches array, but there seems to actually be 5. The last one is full of nonsense characters again.

---

### Post by lovebyte on 2006-03-09
```
char string[100];
```
The line above does not initialise your array of characters.  You could initialise them to the 0 character (and not NULL):
```
char string[100] = {'\0'};
```

A string corresponds to a 0 (i.e. '\0'} terminated array of characters.

---

### Post by rplantz on 2006-03-09
> **lovebyte]```
char string[100] said:**
>  = {'\0'};
```

A string corresponds to a 0 (i.e. '\0'} terminated array of characters.

I believe the character is called "NUL" in ASCII. Use "man ascii" in a terminal window to see the table. In C/C++ you can use '\0'. But this doesn't work in the gnu assembler. In any case, it's a single byte with all the bits set to zero.

I understand what you're saying here, but "0 character" can be taken to mean the byte with the bit pattern 00110000, that it '0'. And to be really picky, ASCII is a seven-bit code, so the highest-order bit can be 1 or 0. (The Apple II used this bit as a busy/done flag for keyboard input.)

---

### Post by jerome bettis on 2006-03-09
```
for (x=0; x < 100; ++x) {
    string[x] = NULL;
}
for (x=0; x < 100; ++x)  {
     newstring[x] = NULL;[FONT=monospace]
[/FONT]}
```

whoa why not just put both those in the same loop?  and you can use
memset(string, 0, MAX_LEN); to do that nicely, no loop needed.

i tried reading the rest but your indentation and comments are all over the place, i'm too lazy to sift through it.

---

### Post by zootreeves on 2006-03-09
memset works nicely thanks.

> i tried reading the rest but your indentation and comments are all over the place

I blame that on learning php first ;) 

Is there an explode function as well? But explode by a string, not just by a character.

---

### Post by hod139 on 2006-03-09
If you are going to be working with strings a lot, I would suggest you look into C++.  Strings are correctly handled in C++ and there are plenty of [string functions. ]("http://www.cppreference.com/cppstring/index.html")
The C str* functions are **really** bad.  If you really want to stick with C, [this page]("http://www.cs.cf.ac.uk/Dave/C/node19.html") has a good description of String handling in C.

---

### Post by rplantz on 2006-03-09
[QUOTE=hod139]
The C str* functions are **really** bad.  If you really want to stick with C, [this page]("http://www.cs.cf.ac.uk/Dave/C/node19.html") has a good description of String handling in C.[/QUOTE]

And this is the reason why I write my own string handling functions. C-style strings are simple char arrays with a NUL character ('\0') at the end of the characters (and not beyond the end of the allocated array). A sentinel-controlled loop is almost always the best solution. The '\0' is the sentinel character.

If processing two strings, intialize two pointers, say fromPtr and toPtr, to the beginning of each string. Then,
```

    while (*fromPtr != '\0') {
        *toPtr = *fromPtr;
     /* whatever processing you need to do */
        fromPtr++;
        toPtr++;
    }
    *toPtr = '\0';

```
There is no need to intialize the array to all zeroes. Anything beyond the '\0' character is considered garbage.

---

### Post by zootreeves on 2006-03-10
Well i've started writing my program now in C, maybe i'll change to C++ for my next project. Why has nobody made a decent set of string functions or why are they not included in the standard libaries?

---

### Post by LeDroid on 2010-09-24
Seems strange that for a 30+ year language it's so difficult to find one on the Net. I made this one with dynamic memory allocation and an optional counter:

```
#include <stdlib.h>
#include <stdio.h>
#include <string.h>

/* ---------------------------------------------------------------------------
  Name       : replace - Search & replace a substring by another one. 
  Creation   : Thierry Husson, Sept 2010
  Parameters :
      str    : Big string where we search
      oldstr : Substring we are looking for
      newstr : Substring we want to replace with
      count  : Optional pointer to int (input / output value). NULL to ignore.  
               Input:  Maximum replacements to be done. NULL or < 1 to do all.
               Output: Number of replacements done or -1 if not enough memory.
  Returns    : Pointer to the new string or NULL if error.
  Notes      : 
     - Case sensitive - Otherwise, replace functions "strstr" by "strcasestr"
     - Always allocates memory for the result.
--------------------------------------------------------------------------- */
char* replace(const char *str, const char *oldstr, const char *newstr, int *count)
{
   const char *tmp = str;
   char *result;
   int   found = 0;
   int   length, reslen;
   int   oldlen = strlen(oldstr);
   int   newlen = strlen(newstr);
   int   limit = (count != NULL && *count > 0) ? *count : -1; 

   tmp = str;
   while ((tmp = strstr(tmp, oldstr)) != NULL && found != limit)
      found++, tmp += oldlen;
   
   length = strlen(str) + found * (newlen - oldlen);
   if ( (result = (char *)malloc(length+1)) == NULL) {
      fprintf(stderr, "Not enough memory\n");
      found = -1;
   } else {
      tmp = str;
      limit = found; /* Countdown */
      reslen = 0; /* length of current result */ 
      /* Replace each old string found with new string  */
      while ((limit-- > 0) && (tmp = strstr(tmp, oldstr)) != NULL) {
         length = (tmp - str); /* Number of chars to keep intouched */
         strncpy(result + reslen, str, length); /* Original part keeped */ 
         strcpy(result + (reslen += length), newstr); /* Insert new string */
         reslen += newlen;
         tmp += oldlen;
         str = tmp;
      }
      strcpy(result + reslen, str); /* Copies last part and ending nul char */
   }
   if (count != NULL) *count = found;
   return result;
}



/* ---------------------------------------------------------------------------
   Samples
--------------------------------------------------------------------------- */
int main(void)
{
   char *str, *str2;
   int rpl;

   /* ---------------------------------------------------------------------- */
   /* Simple sample */
   rpl = 0; /* Illimited replacements */
   str = replace("Hello World!", "World", "Canada", &rpl);
   printf("Replacements: %d\tResult: [%s]\n\n", rpl, str);
   /* Replacements: 1        Result: [Hello Canada!] */
   free(str);

   /* ---------------------------------------------------------------------- */
   /* Sample with dynamic memory to clean */
   rpl = 0; /* Illimited replacements */
   str = strdup("abcdef");
   if ( (str2 = replace(str, "cd", "1234", &rpl)) != NULL ) {
      free(str);
      str = str2;
   }
   printf("Replacements: %d\tResult: [%s]\n\n", rpl, str);
   /* Replacements: 1        Result: [ab1234ef] */
   free(str);

   /* ---------------------------------------------------------------------- */
   /* Illimited replacements - Case sensitive & Smaller result */
   str = replace("XXXHello XXXX world XX salut xxx monde!XXX", "XXX", "-",NULL);
   printf("Result: [%s]\n\n", str);
   /* Result: [-Hello -X world XX salut xxx monde!-] */
   free(str);

   /* ---------------------------------------------------------------------- */
   rpl = 3; /* Limited replacements */
   str = replace("AAAAAA", "A", "*", &rpl);
   printf("Replacements: %d\tResult: [%s]\n\n", rpl, str);
   /* Replacements: 3        Result: [***AAA] */
   free(str);

  return 0;
}

```

---

### Post by TachionTank on 2011-10-12
If you are only looking to replace one kind of character, you can do something like this:

```
char * tmp;
char * line = "testing-123";

while ((tmp = strstr(line, "-") != NULL)
{
    *tmp = '_';
}
```

---

