---
title: "C - number of lines in a text file"
date: 2010-01-20
forum: Programming Talk
---

### Post by ApEkV2 on 2010-01-20
This is probably something stupid I've missed.
I'm trying to fopen() two text files and then find how many lines they contain.
The problem is the result is bogus (ie returns 52 when actually there are 174).

[php]#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <unistd.h>

int main(int argc, char *argv[])
{
	if (argc < 2)
		printf("Usage: [command] [file1] [file2]");

	FILE* fp1;
	FILE* fp2;

	fp1 = fopen(argv[1],"r");
	fp2 = fopen(argv[2],"r");

	if (fp1 == NULL || fp2 == NULL)
		printf("[FAIL] fopen()");

	int file1_lines, file2_lines;

	file1_lines = line_count(fp1);
	file2_lines = line_count(fp2);

	printf("File1 lines %d\nFile2 lines %d\n", file1_lines, file2_lines);

	fclose(fp1);
	fclose(fp2);

	return 0;
}

int line_count(FILE *n)
{
	char c; 
	int lines = 0;

	while ((c = fgetc(n)) != EOF)
	{
		if (c == '\n') ++lines;
	}

	return lines;
}[/php]

---

### Post by andrewc6l on 2010-01-20
This looks OK to me. I'd be tempted to loop while(!feof(n)) instead of explicitly checking for EOF, but that's about it. You might want to print out each character to stdout as you get it, so you can see what's going on. Also, the command line tool od (and in particular od -c) might give you a better idea of what's going on.

---

### Post by ApEkV2 on 2010-01-20
Thanks for the quick reply. Ok I put printf in the loop and everything looks fine.

EDIT:It seems that stdout says the end of the files have been reached.

---

### Post by johnl on 2010-01-20
Hi,

You will find that fgetc() returns an int instead of a char, since EOF is defined to be -1 and a valid character is an 'unsigned char'.  It's possible that your problem is that by casting to a char you are running into a character which is accidentally being interpreted as the EOF.

I would modify your code like so:

```

int line_count(FILE *n)
{
    int c; 
    int lines = 0;

    while ((c = fgetc(n)) != EOF)
    {
        if (c == '\n') ++lines;
    }

    return lines;
} 

```

Or perhaps use fgets() to read a line at a time and simply count the number of reads.

Also it might be good to mention that this:

```

while(!feof(fp)) { /* ... */ }

```

is almost always wrong.  It doesn't tell you if the next read will fail due to EOF -- it tells you if your previous read failed due to EOF.

---

### Post by ApEkV2 on 2010-01-20
I changed char c; to int c; and the problem is still there.
I will probably try using fgets instead if I can't this to work.

---

### Post by johnl on 2010-01-20
Can you post the files you are using to test with? I just ran your unmodified code and compared it to 'wc -l' and it returned the correct results for me.

---

### Post by ApEkV2 on 2010-01-20
Found the problem, it was the files.
They were originally text copy pasted from a pcap file.
The weird thing is the real EOF's have been reached, it's the counting method that failed.

EDIT: I know I should've checked for a new post.

---

### Post by ApEkV2 on 2010-01-20
[attach]144310[/attach]

---

### Post by John Bean on 2010-01-20
> **johnl said:**
> Can you post the files you are using to test with? I just ran your unmodified code and compared it to 'wc -l' and it returned the correct results for me.

My thought exactly. I suspect the use of "\n" is a bit naive if the files originated on a system other than the one that compiles the code, since the representation of "\n" is system dependant and could be any permutation of CR and/or LF. On *nix it's LF, on Windows/DOS it's CR+LF, on Old Apple systems it's... Well, 'nuff said.

---

### Post by John Bean on 2010-01-20
> **ApEkV2 said:**
> [attach]144310[/attach]

Not text of any sort that I can see.

---

### Post by ApEkV2 on 2010-01-20
Did you try saving it instead of just opening?
I tried to open and it wouldn't open, but I downloaded it and then it magically could be opened.
I'll try it again.

---

### Post by ApEkV2 on 2010-01-20
[attach]144311[/attach]

This is what I get when I try to open it.
"/tmp/stream-1.txt could not be opened, because the associated helper application does not exist. Change the association in your preferences."

This is trying to making me angry

---

### Post by John Bean on 2010-01-20
> **ApEkV2 said:**
> Did you try saving it instead of just opening?
I tried to open and it wouldn't open, but I downloaded it and then it magically could be opened.
I'll try it again.

I saved it so I could open it with a hex editor to check the type of newlines it uses. There were no (meaningful) newlines or text, just binary garbage.

Anyhow I'll leave you to it; the "text" files appear to be the root of your problem.

---

### Post by ApEkV2 on 2010-01-20
it's the actual data from network packets

saving it and using a hex editor works for me.....I get the hexadecimal 0D and 0A as a \n

What do newlines look like in hexadecimal? I thought it was just 0A?

---

### Post by ApEkV2 on 2010-01-20
I found sort of a unique fix......I wonder if this works for all possible values of c
```
int line_count(FILE *n)
{
    char z_str[3];
    int c, lines = 0;

    while ((c = fgetc(n)) != EOF)
    {
	[color=red]sprintf(z_str,"%x",c);[/color]
        if ([color=red](strlen(z_str)) == 1[/color]) ++lines;
    }

    return lines;
}
```

---

### Post by dwhitney67 on 2010-01-20
From the file 'stream.txt' that was posted, I found 123 lines (using the code below).

It seems that some lines end with a LF (or a '\n'), whereas other lines end with a CR (or a '\r').

Here's the code:
```

#include <stdio.h>

int main(int argc, char** argv)
{
   FILE* file = fopen(argv[1], "r");

   if (file)
   {
      char buf[4096] = {0};
      unsigned int lines = 0;

      while (fgets(buf, sizeof(buf), file))
      {
         for (const char* ptr = buf; *ptr != '\0'; ++ptr)
         {
            if (*ptr == '\n' || *ptr == '\r')
            {
               ++lines;
            }
         }
      }

      fprintf(stdout, "There are %u lines in the file %s.\n", lines, argv[1]);
   }
   else
   {
      fprintf(stderr, "Failed to open file %s\n", argv[1]);
      return -1;
   }
   return 0;
}

```

Note that I read the data in large chunks, rather than a wimpy byte at a time.  It is more efficient to do.

As for the OP, I'll let him decide what marks the end of a line (a LF or CR).

Btw, I examined the file using the 'od' utility:
```

od -A d -x -v stream.txt

```
One can reference the ASCII table to get the corresponding hex values for LF and CR.
```

man ascii

```


P.S.  If I replace the fgets() with an fread(), then the results are that there are 128 lines.

Oops!  I found an error in my code when using fread(), and of course it caused me to yield an incorrect result.  There are indeed 123 lines in the file.  The bug correction is posted in the code below.
```

#include <stdio.h>
#include <string.h>
...
      while (fread(buf, 1, sizeof(buf), file))
      {
         ...

         memset(buf, 0, sizeof(buf));   /* required to reset buf to nulls */
      }
...

```

---

### Post by ApEkV2 on 2010-01-20
> ....rather than a wimpy byte at a time.
I love the word choice lol.

Thanks everyone for your replies, now I got more than three working solutions to this problem.

@ dwhitney67, thanks for putting together some code. I'm going to have to use fgets now.
Also I wondered why fread would do that, I was just about to ask why so.

---

### Post by LKjell on 2010-01-21
> **ApEkV2 said:**
> I love the word choice lol.

Thanks everyone for your replies, now I got more than three working solutions to this problem.

@ dwhitney67, thanks for putting together some code. I'm going to have to use fgets now.
Also I wondered why fread would do that, I was just about to ask why so.

Could be when fread reach at the end of file it reads less than 4g so it just replace the first bytes it reads and leaves the rest intact.

Of course if dwhitney67 used what fread returns in his for loop rather than looping till '\0' the problem would not occur.

---

### Post by dwhitney67 on 2010-01-21
> **LKjell said:**
> Could be when fread reach at the end of file it reads less than 4g so it just replace the first bytes it reads and leaves the rest intact.

Of course if dwhitney67 used what fread returns in his for loop rather than looping till '\0' the problem would not occur.

You are correct on both counts.  I "cheated" by merely clearing the read buffer.

---

