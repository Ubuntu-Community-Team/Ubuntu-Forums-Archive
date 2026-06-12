---
title: "[SOLVED] strings and ints in files"
date: 2008-02-14
forum: Programming Talk
---

### Post by Zeotronic on 2008-02-14
I need to figure out how to load chars from a file as ints, I also need to figure out how to load strings (spaces and all) from files, but am not sure the best way to do this. The ints, I'm sure, would be simple enough, but I need to be able to load strings that would be able to describe a file directory.
In reality, I actually need to know how to load short ints and long ints, but I figured int would be clearer.
The strings in question are not in any perticular format yet because I don't know the best format for them to be in.
*Oh...* I'm a C++ coder in case you didn't gather it from above.

---

### Post by lisati on 2008-02-14
> **Zeotronic said:**
> Correct me if I'm wrong, but a char is 8 bits, and a int is 3 chars... I need to figure out how to load chars from a file as ints, I also need to figure out how to load strings (spaces and all) from files, but am not sure the best way to do this. The ints, I'm sure, would be simple enough, but I need to be able to load strings that would be able to describe a file directory.
In reality, I actually need to know how to load short ints and long ints, but I figured int would be clearer.
The strings in question are not in any perticular format yet because I don't know the best format for them to be in.
*Oh...* I'm a C++ coder in case you didn't gather it from above.

It may be necessary to open the file in binary mode and use something equivalent to C's getch() function.....

Depending on what you're doing, it may also be useful to think in terms of unsigned bytes rather than chars or ints.

---

### Post by aks44 on 2008-02-14
> **Zeotronic said:**
> int is 3 chars...

What does this code output? ;)

```
#include <iostream>
int main()
{
  std::cout << sizeof(int) << std::endl;
  return 0;
}
```

---

### Post by Zeotronic on 2008-02-14
> It may be necessary to open the file in binary mode and use something equivalent to C's getch() function..... I used to use fstream to extract the chars into an array and then multiply and add them together.
```
long=char[0]*16777216+char[1]*65536+char[2]*256+char[3];
```
... But I would like to think there is a different way... and I am also not sure that my method is entirely correct.
> What does this code output? 
I didn't ACTUALLY need to know! :(

Maybe someone knows some links to sites that may have the answers/be useful?

---

### Post by cb951303 on 2008-02-14
read the ints as a string and use[ atoi()]("http://www.cplusplus.com/reference/clibrary/cstdlib/atoi.html") ;)

---

### Post by slavik on 2008-02-14
there is also fread and fwrite. :)

---

### Post by Zeotronic on 2008-02-14
> read the ints as a string and use atoi() 
Ok, you seem to be misunderstanding what I'm saying... something I was trying to prevent. The values arnt stored in the file as "178"... no, that would be easy. They are stored as in (00,00,00,B2) (array of chars)... you know what I'm saying? I'm sorry, I don't know how to be any clearer.
> there is also fread and fwrite. 
I looked them up on cplusplus.com (more specifically I looked up fread)... I'm not entirely sure I understand... does this read the number of characters specified from the file and write them into where-ever the pointer points? Are you trying to say that I could unload the chars into a int? And it would work? I'll have to try that next time I get a chance.

Now then, since that may possibly be dealt with, perhaps someone could help me with storing strings in files... I need to be able to find file directories with them, and life isn't an ideal world where spaces don't exist in filepaths. How can I get around that? I know how to load strings, spaces and all, but I haven't tried it, and I'm not sure how I would divide the filenames then.

---

### Post by Geekkit on 2008-02-14
> **Zeotronic said:**
> Correct me if I'm wrong, but a char is 8 bits

That depends on:

a.) the programming language you are using and;
b.) the encoding of the file that you are reading

---

### Post by cb951303 on 2008-02-15
> **Zeotronic said:**
> Ok, you seem to be misunderstanding what I'm saying... something I was trying to prevent. The values arnt stored in the file as "178"... no, that would be easy. They are stored as in (00,00,00,B2) (array of chars)... you know what I'm saying? I'm sorry, I don't know how to be any clearer.

ah sorry about the misunderstanding, so you're trying to get data from a binary file?if so, the most simple way to extract data from it is to build a structure and fread all the data you want into it.

---

### Post by ruy_lopez on 2008-02-15
see "/usr/include/limits.h" for definitions of char and int on your system. Mine gives an int as 32bit, four bytes.

---

### Post by ruy_lopez on 2008-02-15
Rudimentary version, which will read data from file in this format:

```
(ff,b2,c3,d4),(2c,3c,4c,5c),(1a,aa,af,a3)
```

At present, it swallows everything into one array. Put your own code where I've commented, to get it to do more. Commas between the subarrays are unnecessary. In fact, it should be able to handle garbage between the subarrays, but not between members.

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <errno.h>

#define MAXCHARS 65536

int hexstr_to_int(char *);
size_t file_size(FILE *fd);
char read_char(char *);
int parse_data(char *, int *);

int main(void)
{
	FILE *fd;
	size_t n = 0, i = 0, end;
	char buf[MAXCHARS];
	int array[100];

	/* replace 'file' with path to your file */
	if ((fd = fopen("file", "r")) == NULL) {
		fprintf(stderr, "fopen error: %s\n", strerror(errno));
		return 1;
	}

	if ((end = file_size(fd)) > MAXCHARS) {
		fprintf(stderr, "filesize exceeds 65536 bytes.\n");
		return 1;
	}
	
	fread(buf, sizeof(char), end, fd);
	
	n = parse_data(buf, array); /* n = items returned */
	printf("%d items:\n", n);	

	for (i = 0; i < n; i++)	/* do addition etc. here */
		printf("%d\n", array[i]);

	return 0;
}

int parse_data(char *data, int *array)
{
	char *open_p, *close_p, *end_p, c, buf[strlen(data) + 1];
	int i = 0, n = 0;

	open_p 	=  strchr(data, '(');
	close_p =  strchr(data, ')');
	end_p 	= strrchr(data, ')'); 	/* effective end of data */
	open_p++;
	while (open_p < end_p) {
		for ( ; open_p < close_p; open_p++) {
			c = read_char(open_p);
			if (c == ',') { 	/* array delimiter */
				buf[i] = '\0';
				*array++ = hexstr_to_int(buf);
				i = 0;
				n++;
				continue;
			}
			buf[i++] = c;
		}
		/* end of set */
		buf[i] = '\0';
		*array++ = hexstr_to_int(buf);
		i = 0;
		n++;

		/* The next set of brackets is handled below. If you want
		 * to do anything with the subarray, do it here. Otherwise
		 * it gets swallowed up in one main array */

		if ((open_p = strchr(close_p, '(')) == NULL) /* next '(' */
			break;
		if ((close_p = strchr(open_p, ')')) == NULL) /* next ')' */
			break;
		open_p++;
	}
	return(n); 
}

char read_char(char *ptr)
{
	char buf[strlen(ptr) + 1];
	
	strncpy(buf, ptr, strlen(ptr) + 1);

	return (buf[0]);
}

size_t file_size(FILE *fd)
{
	size_t end;

	fseek(fd, 0, SEEK_END);
	end = ftell(fd);
	fseek(fd, 0, SEEK_SET);

	return (end);
}	

int hexstr_to_int(char *ptr)
{
	int h;

	sscanf(ptr, "%x", &h);
	
	return h;
}
```

---

### Post by Zeotronic on 2008-02-16
> That depends on:

a.) the programming language you are using and;
b.) the encoding of the file that you are reading
> see "/usr/include/limits.h" for definitions of char and int on your system. Mine gives an int as 32bit, four bytes. 
I have removed my opening statement, you can now stop correcting me.
> *Insert ruy_lopez's code here*
Ok, well after studying it, I definently know how to load values from files, but how do I load strings that are capable of discribing file paths from files? Everybody is jumping at answering how to load values... but no one has said anything about loading strings... is it really that hard?

---

### Post by aks44 on 2008-02-16
> **Zeotronic said:**
> no one has said anything about loading strings... is it really that hard?

No, it's very straightforward. Basically you have two cases:

1. You store the string as-is, and settle for a string terminator (eg. \n or \0). Reading it is only a matter of reading each and every byte until you meet the terminator.
Warning: using this method you can't preallocate a correctly-sized buffer, so watch out for buffer overflows! Be sure to take care that your in-memory string actually ends with \0 after reading it.


2. You first store the string length, then the string itself (you can even avoid storing the final \0). To read the string, first read its length, then the bytes.
Using this method you know the string length by advance, so you can preallocate a buffer with the correct size, hardly any chance to get buffer overflows. Again, take care that the final \0 is there in your in-memory string.


In both cases you have to make sure you know the character encoding you're storing/reading. The best way to avoid any problems is to use UTF-8.

---

### Post by popch on 2008-02-16
> **aks44 said:**
> (...) Reading it is only a matter of reading each and every byte until you meet the terminator.(...) The best way to avoid any problems is to use UTF-8.

Are you quite sure that UTF-8 does not contain any bytes of zero value? After all, unicode characters are more than 8 bits wide.

---

### Post by aks44 on 2008-02-16
> **popch said:**
> Are you quite sure that UTF-8 does not contain any bytes of zero value? After all, unicode characters are more than 8 bits wide.

UTF-8 has been specifically designed to be compatible with legacy (8-bit) ASCII applications: ASCII characters < 128 are represented the same way in UTF-8 than in ASCII.

So the **only** null byte in UTF-8 is the Unicode code point 0, equivalent to ASCII's NUL character (whether you would want to store that character or not is a whole other matter).

---

### Post by Zeotronic on 2008-02-16
> You store the string as-is, and settle for a string terminator (eg. \n or \0).
I had tried that once appon a time, but I had problems, so I have avoided it ever sense... it seems to work now though... weird.

---

