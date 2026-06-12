---
title: "Computer Science student; help please"
date: 2007-10-17
forum: Programming Talk
---

### Post by nite owl on 2007-10-17
Hi I have recently received an assesment that states that:

Present an on-screen menu of operations
Read in the text file: sales.txt
Convert the data in the file into record structured format and store in a binary file.
Read the data in the file and create at least one B-tree of the key fields: item number
(this is the only unique key), customer number, item description.
Add and save new records
Delete records
Query the database, search, find and display records matching the query.
Ideally queries should be in the following string format:
<field identifier> = <field value> {AND/OR next test }

...Obviously this is just a snippet of what they gave us. The basic concept is that you create a text file named sales.txt and create a few records inside it as if it were a small database.

Anyway I can read the file in, open it, display and close it with the current program I have written. However I am now completely lost in regards to the program being able to convert the file into record structured format and storing it in a binary file? What is a binary file? 

Any help would be greatly appreciated.

---

### Post by Lord Illidan on 2007-10-17
Er, wikipedia : [http://en.wikipedia.org/wiki/Binary_file](http://en.wikipedia.org/wiki/Binary_file) ?

---

### Post by nite owl on 2007-10-17
Hi thanks for the reply Lord. I had seen that wiki page, but was hoping for abit more insight as to how you would actually go about converting a text file to a binary file using the c programming language.

sorry I left out that the program was to be written in c.

---

### Post by Dirty Ole on 2007-10-17
In a text file every character takes as much as 1byte ie if you write 2.76543,  the file will be of 2*1byte(size of char data type) = 7 bytes(storing 2.4 => 3bytes ...) while if you did the same with binary file only 4bytes will be used because you are storing a float.

To sum it up, in a binary file ,the space used for storage is the size of the data type  being stored. 

ie int will use 2bytes, float 4bytes, double 8 bytes and so on.

Hope you got it...

---

### Post by Wybiral on 2007-10-17
You can write binary data using [fread]("http://cppreference.com/stdio/fread.html") and [fwrite]("http://cppreference.com/stdio/fwrite.html").

Binary files store the bytes, not the characters. So if you store an integer, it will likely be four bytes, whereas storing the string representation can require any number of bytes.

---

### Post by j_g on 2007-10-17
Binary format simply means that numbers are stored as char, unsigned char, short, unsigned short, long, unsigned long, float, etc (depending upon the precision you need). You don't store them as a series of ascii numeric digits (ie, '0' to '9') like you do in your text file.

For example, if you load your text file into a hex editor program, and look at the number 1008 stored there, it will look like this (in hexadecimal):

31 30 30 38

These are the values for 4 ascii characters of '1', '0', '0', '8'.

If you convert to binary format, then you'd perhaps store this as a short. (ie, If the numbers in your database fall between 0 and 65535, then this falls into the range of an unsigned short. If the numbers are in the range -128 to 127, then this falls into the range of a signed char. Etc).

So if you load the binary file into a hex editor, you'll see two bytes of:

F0 03

This is a short (ie, two bytes). It is stored in little endian (ie, Intel, versus Motorola's big endian) order. So the LSB is first, and the MSB is second. Therefore, it's equivalent to this:

short MyValue = 0x03F0;  // That's the value 1008

I'm not sure what your text data file looks like. You say it has an item number, customer number, and description. The description is not numeric. It's text. So that can't be converted to binary. It will be stored as text in your binary data file, but you'll need some way of "encapsuling" it. (ie, essentially you need to know how long the text is). The other two items are numeric. So you'll store them as a char, short, long, etc. Let's assume that you'll use an unsigned long to store each value.

So your text file looks something like this (Item #5, Customer #20, description of "Bank Funds"):

5, 20, Bank Funds

(This text format is known as CVS. Each field is separated by a comma. Each entry is on its own line).

Let's assume that no description will be longer than 255 characters. This means that you can store the length in an unsigned char. So one easy approach would be to preface the description with its length. Here are the bytes (hexadecimal) that would appear in your binary data file (and I've included comments, which of course, are NOT in the file) for the above entry:

05 00 00 00  // Item number, stored as an unsigned long (4 bytes). LSB is first (little endian order)
14 00 00 00  // Customer number, stored as an unsigned long (4 bytes). LSB is first (little endian order)
0A // Length of the description (ie, description will be the next 10 bytes)
42 61 6E 6B 20 46 75 6E 64 73  // The string "Bank funds", minus any terminating nul char

So your binary entry consists of 20 bytes.

Now, when someone mentions a "record", usually they mean that every entry is the same size. What this means is that you'll set an amount of text that a description must be, for example 16 characters. If the description is less than this, you'll pad it out with spaces. If longer than 16 chars, you'll throw away any text beyond the 16th character. Since you know that the description will always be 16 chars, then there's no need to store the length. So, here's the entry as a "record". Note the space pad characters: 

05 00 00 00
14 00 00 00
42 61 6E 6B 20 46 75 6E 64 73 20 20 20 20 20 20

The good thing about every entry being the same size (ie, 24 bytes above) is that it's really easy to seek() to a particular entry. For example if you need to locate the fourth entry in your data file, you seek (from the beginning of the file) 4 * 24 bytes. Now you read in the next 24 bytes, and there's your entry. The first 4 bytes are an unsigned long. That's the item number. The next 4 bytes are another unsigned long. That's the customer number. And the remaining 16 bytes are the description. So assuming you've got an open handle to your binary file, here's how to read in the fourth entry. (Error checking omitted. Please do it though!)

```
unsigned long item, customer;
char description[17];

// Seek to fourth entry
seek(handle, 4 * 24,   SEEK_SET);
// Read in the item number as an unsigned long
fread(&item, sizeof(unsigned long), 1, handle); 
// Read in the customer number as an unsigned long
fread(&customer, sizeof(unsigned long), 1, handle); 
// Read in the description
fread(&description[0], sizeof(char), 16, handle);
description[16] = 0;
printf("Item = %u, Customer = %u, Description = %s\n", item, customer, &description[0]);
```

---

### Post by Wybiral on 2007-10-17
> **j_g said:**
> 
...
```
 fread(&description[0], sizeof(char), 16, handle); 
```
...


j_g, I'm curious about the use of "&description[0]" instead of "description". I've seen other people do the same in their code. Is it just to keep the style of using the reference operator or is it for portability (maybe some compilers only support this?). Anyway, just curious.

---

### Post by j_g on 2007-10-17
As you know, there's no difference between these two lines:

```
fread(&description[0], sizeof(char), 16, handle);

fread(description, sizeof(char), 16, handle);
```

The compiler knows that description is an array, not a pointer. So it does the correct thing and essentially substitutes the more explicit former line. But a human looking at the latter line wouldn't know offhand whether description is a pointer, or an actual reference to an array member. He has to go look for the declaration of description in order to find out.

I do it the latter way because it explictly shows that "description" is **not** a pointer to something, but rather, a reference to an array member. You don't need to look for the declaration of "description" to know that it's an array. You can tell just from that fread call.

It's actually more versatile to do it the latter way. For example, if you later change description to be a pointer, then you don't have to change the latter fread call. You do have to change the former line.

But anal retentive programmers like myself, who are notoriously diligent about commenting and documenting, prefer to code in a way that is more explicitly understandable to anyone reading the code. Other programmers prefer to do things "the easy way".

For the same reason, some people use a pointer to an array like this:

```
char *MyPtr;

MyPtr = malloc(40);
MyPtr[10] = 0;
```

I would instead write that last line as:

```
*(MyPtr + 10) = 0;
```

The latter shows that MyPtr is indeed a pointer, whereas in the former, you can't be sure until you look at the declaration of MyPtr.

---

### Post by mjwood0 on 2007-10-17
Binary read and write is actually quite useful.  Essentially, you're writing your struct directly to the file.  The beauty of this is that you can read them all in using a simple fread command with no need to read in strings and convert back to the struct that you originally had before you wrote them out.

To use, you open the file doing using the "b" option:
```

inFile = fopen(TEMP_FILE, "rb");

if (inFile != NULL)
{
   /* your code here */
}
```

As j_g mentions below, you can seek directly to an entry as well.  However, I would strongly caution against doing the math for yourself as he suggests with his 4*24 size.  This should always be done using something like:
```
seek(inFile, 4 * sizeof(STRUCT_TYPE), SEEK_SET)
```

> **j_g said:**
> 
```
unsigned long item, customer;
char description[17];

// Seek to fourth entry
seek(handle, 4 * 24,   SEEK_SET);
// Read in the item number as an unsigned long
fread(&item, sizeof(unsigned long), 1, handle); 
// Read in the customer number as an unsigned long
fread(&customer, sizeof(unsigned long), 1, handle); 
// Read in the description
fread(&description[0], sizeof(char), 16, handle);
description[16] = 0;
printf("Item = %u, Customer = %u, Description = %s\n", item, customer, &description[0]);
```


The other huge benefit to binary files is that if you have an array of structures, you can read in the whole array with a simple command.

```

time_t times[NUM_TIMES];
unsigned int numItems;

/* assuming the file is open for binary reading */
/* and that you wrote the integer count of items in the file to the beginning of the file */

/* Read in the number of items in the file */
returnValue = fread(&numItems, sizeof(unsigned int), 0x1, inFile);
if (returnValue != 0x1) /* didn't read one as requested */
{
  fclose (inFile);
  return ERROR_CODE;
}

returnValue = fread(&times, sizeof(time_t), numItems, inFile);
if (returnValue != numItems)
{
  fclose(inFile);
  return ERROR_CODE;
}

```

You can also do writes like this.

Hope this helps!

---

### Post by j_g on 2007-10-17
> **mjwood0 said:**
> I would strongly caution against doing the math for yourself as he suggests with his 4*24 size.

That was just for illustration and explanation, so I chose the most direct way of expressing it.

Yes, it would be better to define some "struct" that describes the record, being careful to account for any compiler alignment issues by using pragma(1) if necessary. (But if the guy is just learning programming, this is just going to confuse him, and give him an extra potential source of problems. Let him do it this way for now).

---

### Post by Wybiral on 2007-10-17
> **j_g said:**
>  ... 

That makes sense.  I haven't ran into any problems with mixing pointers and arrays personally, but thinking about it, I can see how they could cause some major misuse. Especially if your client didn't know what they were doing (like using "sizeof" on an array, or trying to rereference an array as if it were a pointer).

---

### Post by nite owl on 2007-10-18
Hi sorry for the late reply, its been crazy at the moment. Going from my job to uni then getting 3 hours sleep lol. Thanks especially to mjwood & j_g for the indepth responses they really helped me get my mind around the concept.

Say I set up my sales.txt file to  look like this:

20, 3, Drumset
8, 2, guitar
16, 9, computer
....etc

However in regards to the conversion to binary I am still unsure of the exact code to do this? Thanks for all the help so far :)

---

### Post by mjwood0 on 2007-10-18
In C (not necessarily C++) the following would be used:

```

typedef struct RECORD_T
{
  int firstNum;
  int secondNum;
  char strItem[20];
} RECORD_TYPE;

RECORD_TYPE Data[20];
int numDataItems;

/* For each data item, read them in to the Data[x] array position */
/* Increment the numDataItems counter */

/* Open a file pointer for binary writing and do the following */
returnValue = fwrite(&numDataItems, sizeof(int), 0x1, filePointer);
if (returnValue != 0x1) /* One item written */
{
  fclose(filePointer);
  return ERROR;
}

returnValue = fwrite(&Data, sizeof(RECORD_TYPE), numDataItems, &filePointer);
if (returnValue != numDataItems) /* Wrote the number of items you expected */
{
  fclose(filePointer);
  return ERROR;
}

```

This code will embed the number of items at the beginning of the file.  In this way, when you go to read, you read an int first (which is how many records you have in the file) and then read that number of records.

There are a couple things to think about.  You have to have a constant length string defined for each item to keep the structures of even size.  This is okay as long as you know a max length (such as 40 characters or so).  Also, you really want to make sure that you are overwriting the file and not appending to it.  It's crucial that the first item in the file is the integer counter or else you won't know what's going on.  This counter can be replaced with a single structure of other information if you want, so long as it's always the first thing written and the first thing read.

Obviously, you'll want better error messages for return values than just success or fail.  These can be done via #define or enumerated types.

Hope this helps.

I don't want to do your homework for you, but you seem to be asking valid questions and are simply hung up on the syntax and procedure of binary files.

---

