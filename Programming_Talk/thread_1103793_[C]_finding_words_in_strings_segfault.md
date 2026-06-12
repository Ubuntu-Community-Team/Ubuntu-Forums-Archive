---
title: "[C] finding words in strings: segfault"
date: 2009-03-23
forum: Programming Talk
---

### Post by hey_ram on 2009-03-23
hi all,

i have been trying this simple version of the "grep" utility on Linux systems. this is an example from k&r. 

problem: the program segfaults. i ran it with gdb, but after the program has finished executing, just after return 0, the debugger comes up with "cannot find bounds of current function". i have been scouring the net for sources of error, but have drawn a blank. i am hoping someone from these forums would be able to shed some more light on this.

some details about the program itself.
1. the program reads character data from a file  on the command line (argv[1]) and stores it in a string.

2. the string to be searched for is also from the command line (argv[2]). 

3. these two strings are passed to the function "patternFinder".

4. the function "lineCount" counts the no. of lines (separated by '\n').

5. the function lineStorer stores every single line. the expression to be found (in the program, the string "find") is then compared with the line.

6. if a match is found, the line number and the line where it was found are printed, else nothing.

i just wanted to make it easier to read the code, which is why i gave a small description of the same. 

the code is as follows:
[PHP]/*program to find a string located in a given user-entered string. the output is the lines containing the search string. this is similiar to the "grep" program. from k&r, page 59.*/

#include<stdio.h>
#include<stdlib.h>
#include<string.h>

void patternFinder(const char *str, const char *find);  /*function declaration. takes source string and string to find a pattern in.*/
int lineCount(const char *str);  /*function to count no. of lines in a text.*/
char *lineStorer(const char *str);  /*line that returns the next line.*/
char *strNcpy(char *str, int start, int end);  /*returns the N characters in str from start to end.*/

int main(int argc, char *argv[])
{
    char *str, *find, ch;
    int i = 0;
    FILE *fid;   /*this is the file identifier.*/

    /*entering (taking) in the target string from the file to be read.*/
    fid = fopen(argv[1], "r");   /*open the file for reading from.*/
    str = (char *)malloc(1*sizeof(char));
    while( (ch = fgetc(fid)) != EOF )   /*read the character from the file stream and compare with EOF.*/
    {
        str = (char *)realloc(str, (i + 1)*sizeof(char));
        *(str + i++) = ch;
    }
    *(str + i) = '\0';

    strcpy(find, argv[2]);  /*the third command line argument is the string to be found.*/

    patternFinder(str, find);   /*calling the function.*/

    fclose(fid);  /*closing the file stream.*/
    free(str);
    free(find);

    return 0;
}

void patternFinder(const char *str, const char *find)
{
    int i = 0, nLines = 0, m = 0, FLAG = 0;
    char *temp;   /*this char pointer holds every line.*/
    char *match;   /*this string stores strlen(find) characters from temp. it is compared with find for a match.*/

    nLines = lineCount(str);

    for(i = 0; i < nLines; i++)
    {
        temp = lineStorer(str);  /*stores the next line in temp.*/

        for(m = 0; (*(temp + m) != '\0') && (strlen(temp) - m >= strlen(find)); m++) /*searching for string in temp (line).*/
        {
            match = strNcpy(temp, m, (m + strlen(find) - 1));
            if( strcmp(match, find) == 0 ) /*match = find.*/
            {
                    fprintf(stdout, "Found %s at line no. %d.\n", find, (i + 1));
                    fprintf(stdout, "%s\n", temp);
                    FLAG = 1;
            }
            free(match);  /*match is re-assigned some memory, so this can be freed.*/
        }
        if( FLAG == 1 )
        {
            break;   /*breaking out of for loop once a match has been found.*/
        }
        free(temp);  /*temp also reassigned after this, so can be freed.*/
  }
    free(temp);
    free(match);
    return;
}

int lineCount(const char *str)
{
    int i = 0, nLines = 0;

    for(i = 0; *(str + i) != '\0'; i++)
    {
        if( *(str + i) == '\n' )
        {
            ++nLines;   /*counting the no. of lines in the program. */
        }
    }

    return nLines;
}

char *lineStorer(const char *str)  /*this function returns the line in temp. helps reduce the clutter from patternFinder.*/
{
    static int i, j = 0;  /*this counter keeps track of the position in string.*/
    int k = 0;
    char *temp;

    while( (*(str + i) != '\n') && (*(str + i) != '\0') )
    {
        i++;  /*i keeps track of the position of the string.*/
        k++;   /*using this line, the length of one line in the string is computed. on this basis, the temp is pre-assigned all the memory it will need to store one line in one go. this prevents complex memory mgmt such as realloc etc.*/
    }

  }

    temp = (char *)malloc(k*sizeof(char));
    k = 0;
    while( *(str + j) != '\n' )
    {
        *(temp + k++) = *(str + j++);
    }
    *(temp + k) = '\0';

    return temp;
}

char *strNcpy(char *str, int start, int end)
{
    char *temp;
    int i = 0, j = 0;

    temp = (char *)malloc((end - start + 1)*sizeof(char));
    for(i = start; ((i <= end) && (*(str + i) != '\0')); i++)
    {
        *(temp + j++) = *(str + i);
    }
    *(temp + j) = '\0';

    return temp;
}
[/PHP]

some general comments on the code, such as if it was commented properly and if the logic could use some improvement, are also most welcome.

thanx!

---

### Post by monkeyking on 2009-03-23
I've never seen this errormsg.
Try setting some breakpoints.

Or use valgrind.
I would use valgrind

---

### Post by dwhitney67 on 2009-03-23
You are making things very difficult.  Consider using strstr() to determine if the pattern is present within a given string.

Also, tidy up your application.  For instance, there is no need to make a copy of argv[] values.  Just pass these values around as needed.

This is how I would solve the puzzle:

1.  Open the file (argv[1])
2.  Call a function that reads each line in the file, and keeps a count of the number of lines read.
3.  For each line read, use strstr() to determine if the pattern, which also is passed to the function (argv[2]), is present within the line.
4.  If the pattern is present, then print the line number followed by the line itself.
5.  Return from the function.
6.  Close the file.

I do not see any need to allocate any memory in this program, much less use any static variables.  If I have missed a requirement, then accept my apologies.

For information on strstr(), refer to the man-page:
```

man strstr

```

---

### Post by hastur on 2009-03-23
hi,

I only read quickly but if I'm not wrong you do :
```

char *find;
strcpy(find,argv[2]);

```
this may be your segfault : strcpy doesn't allocate memory for the destination string, so you should either
```

char *find = malloc(strlen(argv[2])+1);
strcpy(find,argv[2]);

```
or
```

char *find = argv[2];

```

some comment on the code :
- I think you should test the arguments (what happens if the user doesn't give a filename and a string to find).
- on a more general basis, test every function you use (test if fopen found the file, if malloc returns null, etc)
- I would not read the input byte by byte through a stream. maybe more efficient would be to read big chunks of data (like 1024 bytes) with "read". saves time as in the end you only want a memory copy of the file content. you could also read the first chunk, then parse it, before freeing it and reading the next chunk, thus reducing the amount of memory used for very big files.
- you use memory copies too much : why not just load the string at the beginning, then just parse it with pointers in the string ?
that's just my opinion though :)

---

### Post by Frank Kotler on 2009-03-23
I'm not much of a C programmer, but I agree with hastur! As I see it, you've got "find", a local/automatic/stack variable - a pointer to char, but it doesn't actually point to anything. You copy argv[2] to it... and then free it ("a ghastly error" - k&r). Either malloc  memory for it, or "find=strdup(argv[2]" will give you something you can free. (fastest code is the code that doesn't exist - don't copy it at all). Reading the file in chunks is good... but you're doing buffered input anyway... and pattern-matching across chunk boundaries is a PITA. How 'bout mmap?

Best,
Frank

---

### Post by dwhitney67 on 2009-03-23
As I indicated in my earlier reply, this program should be fairly trivial.  There is no need to make it more complicated by reading in huge gobs of data at a given time or even using a memory map.

Something like the following would probably suffice, unless I have missed a requirement (or two).
```

#include <stdio.h>
#include <string.h>

void findStringPattern(FILE* fd, const char* pattern);


int main(int argc, char** argv)
{
  if (argc != 3)
  {
    fprintf(stderr, "Usage: %s <filename> <pattern>\n", argv[0]);
    return 1;
  }

  FILE* fd = fopen(argv[1], "r");

  if (!fd)
  {
    fprintf(stderr, "Error: Cannot open file '%s'\n", argv[1]);
    return 1;
  }

  findStringPattern(fd, argv[2]);

  fclose(fd);

  return 0;
}


void findStringPattern(FILE* fd, const char* pattern)
{
  for (unsigned int lineNum = 1; !feof(fd); ++lineNum)
  {
    char line[1024] = {0};

    if (fgets(line, sizeof(line), fd) && strstr(line, pattern))
    {
      fprintf(stdout, "%u: %s", lineNum, line);
    }
  }
}

```

---

### Post by hastur on 2009-03-23
> **dwhitney67 said:**
> There is no need to make it more complicated by reading in huge gobs of data at a given time or even using a memory map.

no, you're right, usually there is no need for such things.
it's just, recently I had to make these kind of things on very big files in a non-posix environnment (in almost-real-time :( ) and found that using big chunks of read would speed up the process drastically (still using strtok and strstr to find the lines/strings).
of course it's very likely speed won't be a problem here... it's just I tend to be a little too mono-obsessional :)

---

### Post by Krupski on 2009-03-23
> **dwhitney67 said:**
> You are making things very difficult.  Consider using strstr() to determine if the pattern is present within a given string.

Also, tidy up your application.  For instance, there is no need to make a copy of argv[] values.  Just pass these values around as needed.

This is how I would solve the puzzle:

1.  Open the file (argv[1])
2.  Call a function that reads each line in the file, and keeps a count of the number of lines read.
3.  For each line read, use strstr() to determine if the pattern, which also is passed to the function (argv[2]), is present within the line.
4.  If the pattern is present, then print the line number followed by the line itself.
5.  Return from the function.
6.  Close the file.

I do not see any need to allocate any memory in this program, much less use any static variables.  If I have missed a requirement, then accept my apologies.

For information on strstr(), refer to the man-page:
```

man strstr

```

One thing I noticed is that argc isn't first checked to see if both command line parameters are actually given.

Whenever I write programs like this that access argv[n], if I forget to enter a parameter and then try to use the argv[n] that (this time) doesn't exist, I get a segfault.

Maybe that's what's going on? [IMG]http://www.gunsnet.net/forums/images/smilies/oh.gif[/IMG]

---

