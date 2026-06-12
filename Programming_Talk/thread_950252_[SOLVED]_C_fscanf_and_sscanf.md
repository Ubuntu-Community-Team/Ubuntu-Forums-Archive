---
title: "[SOLVED] C fscanf and sscanf"
date: 2008-10-16
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-10-16
can one use sscan in this manner
```
sscanf(char * str, "\n%s\t%s", char * beforetab, char * aftertab);
```
This code "should" take string str and split (everything after) it based upon the \t

can one use fscan in this manner
```
fscanf(FILE * infile, "\n%s\t%s", char * beforetab, char * aftertab);
```
This code "should" read FILE infile and split (everything after) it based upon the \t


If either isn't possible then please suggest alternatives

---

### Post by dwhitney67 on 2008-10-17
Why don't to put together a program with 10 lines of code or less to test out whether it works or not?  Jeez, I wonder if UF issues "Lazy Person of the Year" awards?

To answer your question, yes it works.

[php]
#include <stdio.h>

int main()
{
  const char* str = "Hello\tWorld";

  char word1[20] = {0};
  char word2[20] = {0};

  sscanf(str, "%s\t%s", word1, word2);

  printf( "word1 = %s\n", word1);
  printf( "word2 = %s\n", word2);

  return 0;
}
[/php]

---

### Post by Mr.Macdonald on 2008-10-17
> Segmentation fault

This is all I get in return to trying to use that function. And upon achieving this error printf statements fail and thus my debugging method was undermined. So its not laziness it is simply incapability to test it with success.

---

### Post by dwhitney67 on 2008-10-17
The example program I provided earlier took all of about one minute to write and compile/link.  I tested it and it worked.

Now, would I normally write code like that?  Nope.  One cannot be assured that a buffer overflow will not happen.  In my example, the two strings ('hello' and 'world') are only 6-characters in size (5 + null), and I declared my word-variables to be 20 characters long.  So no problem there.

However, if the strings had been longer, say "ProgrammingIsForTheBirds\tAin'tLifeGrand", then the program either would crash or gibberish would be spit out when I attempted to print word1 and word2.

P.S.  You're probably wondering how I would solve the problem "safely".  Well, I would use a tokenizer, such as strtok(), or perhaps rely on strchr() and buffer arithmetic.

---

