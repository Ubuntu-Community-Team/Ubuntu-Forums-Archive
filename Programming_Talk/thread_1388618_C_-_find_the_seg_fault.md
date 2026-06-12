---
title: "C - find the seg fault"
date: 2010-01-23
forum: Programming Talk
---

### Post by ApEkV2 on 2010-01-23
I ran into a seg fault in the program I'm working on and can't figure this out. If anyone could help to find the problem, many thanks indeed.

I know the seg fault is inside the function named "file_compare" somewhere. 
In the function "line_char_count" for fseek can I make the offset negative, because isn't it the current location plus the offset?

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <unistd.h>

int main(int argc, char *argv[])
{
	if (argc < 2)
	{
		printf("\nUsage: [command] [file1] [file2] [file3]\n\n");
		return 1;
	}

	FILE* fp1 = fopen(argv[1],"r");
	FILE* fp2 = fopen(argv[2],"r");
	FILE* fp3 = fopen(argv[3],"r");

	if (fp1 == NULL || fp2 == NULL || fp3 == NULL)
	{
		printf("\n[FAIL] fopen()\n\n");
		return 1;
	}

	int file1_lines, file2_lines, file3_lines;

	file1_lines = line_count(fp1);
	file2_lines = line_count(fp2);
	file3_lines = line_count(fp3);

	file_compare(fp1, file1_lines, fp2, file2_lines, fp3, file3_lines);

	fclose(fp1);
	fclose(fp2);
	fclose(fp3);

	return 0;
}

int line_count(FILE *n)
{
	char z_str[3]; 
	int c, lines = 0;

	while ((c = fgetc(n)) != EOF)
	{
		sprintf(z_str,"%x",c);
		if ((strlen(z_str)) == 1) ++lines;
	}

	return lines;
}

int line_char_count(FILE *n)
{
	char z_str[3];
	int c, result = 0;

	while ((c = getc(n)) != EOF)
	{
		sprintf(z_str,"%x",c);
		if ((strlen(z_str)) == 1) goto finish;
		++result;
	}
	
	finish: fseek(n, -result, SEEK_CUR);
	return result;
}

int file_compare(FILE* a, int a2, FILE* b, int b2, FILE* c, int c2)
{
	int string1_length, string2_length, string3_length, byte_offset = 0, result;
	int count, total_lines = (a2 + b2 + c2), cur_line;
	int fp1_line, fp2_line, fp3_line;

	char *string1_buffer, *string2_buffer;

	fseek(a, byte_offset, SEEK_SET);
	fseek(b, byte_offset, SEEK_SET);
	fseek(c, byte_offset, SEEK_SET);

	for (count = 0; count < a2; ++count)
	{	
		cur_line = line_char_count(a);
		fgets(string1_buffer, cur_line - 1, a);
			
		for (fp2_line = 1; fp2_line <= b2; ++fp2_line)
		{
			cur_line = line_char_count(b);
			fgets(string2_buffer, cur_line - 1, b);
			result = strcmp(string1_buffer, string2_buffer);
			if (result == 0) printf("\nFile1 Line %d == File2 Line %d\n", count, fp2_line);
		}
		
		for (fp3_line = 1; fp3_line <= c2; ++fp3_line)
		{
			cur_line = line_char_count(c);
			fgets(string2_buffer, cur_line - 1, c);
			result = strcmp(string1_buffer, string2_buffer);
			if (result == 0) printf("\nFile1 Line %d == File2 Line %d\n", count, fp3_line);
		}
		
	}
	return 0;
}
```

---

### Post by Can+~ on 2010-01-23
> **ApEkV2 said:**
> In the function "line_char_count" for fseek can I make the offset negative, because isn't it the current location plus the offset?

Of course it can be negative, the only issue that this could cause, is that you're running outside of the boundries of the file.

```
fseek(a, byte_offset, SEEK_SET);
```

Well, except in this case. It can't be negative if you're using SEEK_SET, as SEEK_SET represents the beginning of the file, therefore, you'd be going behind it. But reading the code, it seems that those fseek's inside the function you mention are ok, as you go [FONT="Courier New"]fseek(a, 0, SEEK_SET)[/FONT] (which is pretty much like [FONT="Courier New"]rewind()[/FONT]).

I'll edit this post when I see something of interest in your code.

**EDIT:**
```
int line_char_count(FILE *n)
{
	char z_str[3];
	int c, result = 0;

	while ((c = getc(n)) != EOF)
	{
		sprintf(z_str,"%x",c);
		if ((strlen(z_str)) == 1) goto finish;
		++result;
	}
	
	finish: fseek(n, -result, SEEK_CUR);
	return result;
}
```

First thing, you could do that with a break and avoid [FONT="Courier New"]goto[/FONT] altogether. Now, why not, instead of jumping negative length, store the position when you started ([FONT="Courier New"]ftell()[/FONT]) and then jump back to that position? In fact, you then could obtain the length by doing end-start.

Now I wonder, why you sprintf into a string with hexadecimal format? I'd guess by the function name that you want to get the amount of characters on a line. In which case, why not just do something like:

```
for(char c; c != EOF && c != '\n'; c = getc(n));
```

---

### Post by PandaGoat on 2010-01-23
The segfault occurs at line 85:
```

fgets(string1_buffer, cur_line - 1, a);

```

This occurs because string1_buffer is not allocated. The same problem will occur with string2_buffer.  The following code is the root of the segfault:
```

char *string1_buffer, *string2_buffer;

```

You must either use malloc on both of them before you use these strings or declare them on the stack:
```

char string1_buffer[size] = {0};
...

```

I realize this is a problem since you won't know how large the lines are. Welcome to C. You can either declare a large enough buffer to handle everything or read a line in using fgetc and realloc to change the size of the buffer as needed. Also, you will probably want to reset the buffers to be filled with 0's every time you want to reuse them.

---

### Post by dwhitney67 on 2010-01-23
I believe PandaGoat has answered the OP's question.

But I have a question for the OP...  What do you think this function is doing?
```

int line_count(FILE *n)
{
	char z_str[3]; 
	int c, lines = 0;

	while ((c = fgetc(n)) != EOF)
	{
		sprintf(z_str,"%x",c);
		if ((strlen(z_str)) == 1) ++lines;
	}

	return lines;
}

```
I can tell you what it is *not* doing... it is not returning the number of lines in a file.

---

### Post by ApEkV2 on 2010-01-23
@ dwhitney67,
In the original function I was just testing whether c was a '\n' character, but some lines had a '\r'.
I used sprintf to convert c to hex and found out that the '\n' and '\r' were both one byte long.
I didn't check if any other characters were one byte long, but the four files I tried this function on, [color=blue]yielded correct results[/color].
I didn't check whether other characters like '\t' so I will probably just change it back to an if test statement.

@ Can, I kinda remember why goto was being phased out but then I forgot somewhere along the line.
Why is goto hated so much now?

@ PandaGoat, I was hoping to avoid that but it's like you said, "welcome to c."  I will have to work on it.

---

### Post by dwhitney67 on 2010-01-23
> **ApEkV2 said:**
> @ dwhitney67,
In the original function I was just testing whether c was a '\n' character, but some lines had a '\r'.


Try something like this:
```

unsigned int line_count(FILE* fp)
{
   unsigned int lines = 0;
   char buf[256] = {0};

   while (fread(buf, 1, sizeof(buf) - 1, fp) > 0)
   {
      for (const char* p = buf; *p != '\0'; ++p)
      {
         if (*p == '\n' || *p == '\r') ++lines;
      }

      memset(buf, 0, sizeof(buf));
   }

   return lines;
}

```

---

### Post by LKjell on 2010-01-23
The first thing I would have done is to convert the file to use unix new line format
To avoid any headache.

[http://www.cyberciti.biz/faq/howto-unix-linux-convert-dos-newlines-cr-lf-unix-text-format/](http://www.cyberciti.biz/faq/howto-unix-linux-convert-dos-newlines-cr-lf-unix-text-format/)

Second is to draw or formulate your intention. If you can't express yourself it will be very hard to write a program. Which means have a structure.

From your code the file comparing function is not intuily easy to figure out what it does.

Below is my function. It takes in two streams. Read a line in the first stream and compare with the other stream.

```
void file_compare(FILE *a, FILE *b)
{
	char *string_a = NULL;
	char *string_b = NULL;
	size_t size = 120;
	int line_a = 0;
	int line_b = 0;
	ssize_t size_a = 0;
	ssize_t size_b = 0;
	
	while(size_a = getline(&string_a, &size, a) != -1)
	{	
		line_a++;
		while(size_b = getline(&string_b, &size, b) != -1) {
			line_b++;
			if (size_a != size_b) 
				continue;
			
			/*Somehow the size_a and size_b does not return the correct value) 
			 */
			
			if(strlen(string_a) ==1 || strlen(string_b) == 1)
				continue;
				
			if (strcmp(string_a, string_b) == 0)
				printf("\nFile1 Line %d == File2 Line %d\n", line_a, line_b);
		}
		line_b = 0;
		rewind(b);
	}
	
	free(string_a);
	free(string_b);
}
```

Another thing is that you have not forward declared your functions.

---

### Post by dwhitney67 on 2010-01-23
Another way to compare files is to compute a CRC (Cyclical Redundancy Check) or other types of checksums to see if the files are equivalents.  However, there are limitations to such.  Here's some good reading... [http://en.wikipedia.org/wiki/MD5](http://en.wikipedia.org/wiki/MD5)

Bear in mind that not all files contain ASCII characters, much less are composed of null-terminated strings.  Thus the use of strcmp() or variants of such don't, and will not, always work.

---

### Post by ApEkV2 on 2010-01-25
Ok, I think this will not work. Got this from a reference book.
Will this allocate memory for the string buffers after each iteration?

```
	struct linelink { char *line; struct linelink *next; };
	struct linelink *head = NULL, *tail = NULL;

	char (*string1_buffer[15]), (*string2_buffer[15]);
```

```
	for (count = 0; count < a2; ++count)
	{	
		cur_line = line_char_count(a);
		while ((fgets(string1_buffer, cur_line - 1, a)) != NULL)
		{
			if (head == NULL)
			{
				head = malloc(sizeof(struct linelink));
				if (head != NULL)
				{
					head->line = malloc(strlen(string1_buffer) + 1);
					if (head->line != NULL)
					{
						strcpy(head->line, string1_buffer);
						else
							fprintf(stderr, "\nmalloc() Out of memory\n"), return -1;
					}
					else
						fprintf(stderr, "\nmalloc() Out of memory\n"), return -1;
				}
			}
		}
. . . 
```

@ dwhitney67, I'm comparing each line of each file to each other.
Trying to input the first line of file 1 and comparing that line to all the lines of file 2, 3, etc. 
Then it goes to line 2 of file 1 and does the same process above.

---

### Post by LKjell on 2010-01-25
That code won't compile. And if you do fix the the else statement it won't run much... 

You need a temp node in the linked list to iterate. I do suggest you do something easy before going full out. And don't be shy to use {} to state a given code block.

---

### Post by dwhitney67 on 2010-01-25
> **ApEkV2 said:**
> 
@ dwhitney67, I'm comparing each line of each file to each other.
Trying to input the first line of file 1 and comparing that line to all the lines of file 2, 3, etc. 
Then it goes to line 2 of file 1 and does the same process above.
Are you trying to find all occurrences of a line from File 1 within Files 2 & 3?  Or are you merely trying to ascertain if the files are the same?

The first and second sentences of your post contradict each other.

---

### Post by ApEkV2 on 2010-01-25
I was pretty sure those sentences were correct, but here.
Three files, the first one is the main file, it is by far the longest.
The program tests all lines of the first file against the other two shorter files' lines.

In other words I'm trying to find a line from file 1 in either of the two test files.

Edit: I see what you're saying about my previous post. I hate sentences

---

### Post by dwhitney67 on 2010-01-25
See if you can use the following code, or perhaps lift some ideas from it:
```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <stdbool.h>

unsigned int ingestFile(FILE* fp, char*** data);
bool compareFile(const char** data, const unsigned int numRecs, const char* filename);

int main(int argc, char** argv)
{
   if (argc < 3)
   {
      fprintf(stderr, "Usage: %s <file1> <file2> [<file3> ... <fileN>]\n", argv[0]);
      return -1;
   }

   FILE* fp1 = fopen(argv[1], "r");

   if (!fp1)
   {
      fprintf(stderr, "Unable to open file '%s'.", argv[1]);
      return -1;
   }

   char**       data    = 0;
   unsigned int numRecs = 0;

   if ((numRecs = ingestFile(fp1, &data)) > 0)
   {
      #ifdef DEBUG
      for (unsigned int i = 0; i < numRecs; ++i)
      {
         fprintf(stdout, "%s", data[i]);
      }
      #endif

      for (int a = 2; a < argc; ++a)
      {
         if (!compareFile((const char**)data, numRecs, argv[a]))
            break;
      }

      // TODO: deallocate data
   }
   else if (numRecs == 0)
   {
      fprintf(stderr, "Error: '%s' is an empty file.\n", argv[1]);
      return -1;
   }

   return 0;
}

unsigned int ingestFile(FILE* fp, char*** data)
{
   char line[1024] = {0};
   unsigned int numRecs = 0;

   while (fgets(line, sizeof(line), fp))
   {
      ++numRecs;

      if (data == 0)
      {
         *data = malloc(sizeof(char*));
      }
      else
      {
         *data = realloc(*data, numRecs * sizeof(char*));
      }

      (*data)[numRecs - 1] = strdup(line);
   }

   return numRecs;
}

bool compareFile(const char** data, const unsigned int numRecs, const char* filename)
{
   char** data2 = 0;

   FILE* fp = fopen(filename, "r");

   if (!fp)
   {
      fprintf(stderr, "Unable to open file '%s'.", filename);
      return false;
   }

   unsigned int numRec2 = ingestFile(fp, &data2);

   if (numRec2 > 0)
   {
      for (unsigned int i = 0; i < numRecs; ++i)
      {
         for (unsigned int j = 0; j < numRec2; ++j)
         {
            if (strcmp(data[i], data2[j]) == 0)
            {
               fprintf(stdout, "%s: %s", filename, data[i]);
            }
         }
      }

      // TODO: deallocate data2
   }

   return true;
}

```

---

