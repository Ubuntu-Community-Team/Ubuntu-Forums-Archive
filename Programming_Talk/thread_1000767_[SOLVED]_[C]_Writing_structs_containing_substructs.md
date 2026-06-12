---
title: "[SOLVED] [C] Writing structs containing substructs into a binary file?"
date: 2008-12-03
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-12-03
How?

---

### Post by dwhitney67 on 2008-12-03
If your structs contain simple data types (e.g. ints, floats, chars, etc), then just write the struct using one write() statement.

If you have pointers to data within your struct, then you will have to go with the approach of writing each individual field to the file, once again, using the write() function.

Show some code if you have it.

P.S.  Never store an address of a pointer in your binary file; it would be useless if retrieved later.

P.S.S.  Concerning the first approach outlined above, be aware that compilers sometimes pad structures that are not word-aligned to the nearest word-boundary.  Write a test program to print the size of your structure to verify it is what you expect.

---

### Post by nvteighen on 2008-12-03
Well, if there are no pointers inside the structure and everything is happily allocated at stack, you should just directly use fread/fwrite.

But, if you happen to have pointers inside it, you will have to divide stuff into some format of yours and store the data by dereferencing the pointers, otherwise you'll be saving the memory address hold by them instead of the data.

But, why do you want a binary file? Why isn't a text file enough for your needs? Keep in mind that text files are "universal interfaces"... I just wonder.

---

### Post by dwhitney67 on 2008-12-03
> **nvteighen said:**
> ...

But, why do you want a binary file? Why isn't a text file enough for your needs? Keep in mind that text files are "universal interfaces"... I just wonder.
Binary files are used as a means to minimize the footprint of saved data.  It takes 4 bytes to store an int, but in ASCII it would require more if the int is greater than 9999.

Thus learning how to create a binary file, and how to read back from it are needed skills if one wants to consider themselves a proficient programmer.

Learning how to write data in ASCII format is also a skill that is needed; in such a case, one would have to insert delimiters between fields, so that it is possible to determine where one field ends and another begins.  And btw, those delimiters just add to the size of the file.

---

### Post by Sydius on 2008-12-03
Besides, text files are just binary files with a limited range for the value of each byte.  There's nothing inherently universal about text files, except that endianness doesn't matter on the byte level.  Two programs must still know how to interpret the file, and since that requirement is already there, interpreting endianness properly is easy to include.  There's also the issue that text editors in various platforms like to use different standards for line breaking, so a program must be able to deal with any of them or risk breaking if a user opens and re-saves such a file with their text editor.

---

### Post by nvteighen on 2008-12-03
> **Sydius said:**
> Besides, text files are just binary files with a limited range for the value of each byte.  There's nothing inherently universal about text files, except that endianness doesn't matter on the byte level.  Two programs must still know how to interpret the file, and since that requirement is already there, interpreting endianness properly is easy to include.  There's also the issue that text editors in various platforms like to use different standards for line breaking, so a program must be able to deal with any of them or risk breaking if a user opens and re-saves such a file with their text editor.
When I say "universal interface" is in the sense that it's not program/implementation-dependent. If you store in binary, you're transferring your memory to a file and that will only be read by a program that uses exactly the same memory "arrangement" (except in trivial cases where you just use built-in data types). In one word: the implementation details get mixed into the interface and that's not quite good... any change in your internal workings may affect the file's format.

So, if you store your data into a text file, you increase the possibility on having that file being read by many different tools with the sole requirement of telling them what your file format is.

---

### Post by Mr.Macdonald on 2008-12-03
Text files are binary, as far as I know you can't make a "Binary" file. That would mean writing to single bits (in my opinion), not bytes. Linux can read any file as text, try cat <binary file>. when your write a struct, cast it to char[] and write. Without pointers life is easy (yet not very versitile).

if you have a pointer, then maybe write the length as an int, then write the array, but you need to design a format.

One of the great thing you can do with C is anything you want, just doing it correctly is the problem.

byt the way, and integer is just 4 charecters "sizeof(int);"

---

### Post by dwhitney67 on 2008-12-04
> **Mr.Macdonald said:**
> Text files are binary, as far as I know you can't make a "Binary" file. That would mean writing to single bits (in my opinion), not bytes. Linux can read any file as text, try cat <binary file>. when your write a struct, cast it to char[] and write. Without pointers life is easy (yet not very versitile).

if you have a pointer, then maybe write the length as an int, then write the array, but you need to design a format.

One of the great thing you can do with C is anything you want, just doing it correctly is the problem.

byt the way, and integer is just 4 charecters "sizeof(int);"

-1

Text files are NOT binary.

An integer is four bytes, not four characters.  I thought I made this clear in a previous post.  The number 9999 takes up four characters, which is the same if it were represented as an int(eger).  But if the number were 10000 (or greater) then it would take 5+ characters to represent the number.  As long as the value is less than 2^32, then only 4 bytes are necessary in binary format.


Examples of a text file and a file in binary format:
/boot/config-`uname -r`
/boot/vmlinuz-`uname -r`

---

### Post by crazyfuturamanoob on 2008-12-13
But how to read the structure's data?

---

### Post by nvteighen on 2008-12-13
Use fread(), of course, you have to "reverse" the steps you took to fwrite() them...

Create a format and write its "standard"... Conform to that "standard" to read and write. If you know how your file is divided, reading and writing should be easy. This may sound trivial, but it's what you have to actually do... (in a binary or an ASCII file...)

---

### Post by crazyfuturamanoob on 2008-12-14
I just learned how to hex-edit, and I'm so exited about it. :D

But I'm wondering, how does a C program write a structure into binary file?

Is it just the structure's contents in linear order, one by one, or is there some other data which says "this is a structure"?

---

### Post by dwhitney67 on 2008-12-14
> **crazyfuturamanoob said:**
> ...

But I'm wondering, how does a C program write a structure into binary file?

Is it just the structure's contents in linear order...?

Yes.  For example:

[php]
#include <stdio.h>
#include <stdlib.h>
#include <assert.h>

struct Foo
{
  int  val;
  char ch;
  int* ptr;
};

void printData(const char* str, struct Foo* foo);

int main()
{
  FILE* fp = fopen("file.bin", "w");

  assert(fp != 0);

  // declare/initialize a Foo object
  struct Foo foo;
  foo.val = 5;
  foo.ch  = 'a';
  foo.ptr = malloc(sizeof(int));
  *(foo.ptr) = 10;

  // print original data
  printData("original", &foo);

  // write it to a file
  fwrite(&(foo.val), sizeof(foo.val), 1, fp);
  fwrite(&(foo.ch), sizeof(foo.ch), 1, fp);
  fwrite(foo.ptr, sizeof(int), 1, fp);
  fclose(fp);

  // reopen file, and read the data
  FILE* fp2 = fopen("file.bin", "r");
  struct Foo foo2;

  assert(fp2 != 0);

  fread(&(foo2.val), sizeof(foo2.val), 1, fp2); 
  fread(&(foo2.ch), sizeof(foo2.ch), 1, fp2); 
  foo2.ptr = malloc(sizeof(int));
  fread(foo2.ptr, sizeof(int), 1, fp2); 

  // print data from file
  printData("from file", &foo2);

  return 0;
}


void printData(const char* str, struct Foo* foo)
{
  printf("%s:\n", str);
  printf("\tval  = %d\n", foo->val);
  printf("\tch   = %c\n", foo->ch);
  printf("\t*ptr = %d\n", *(foo->ptr));
}
[/php]
Btw, the pointer address of foo.ptr was not written to the binary file.  Only the data value referred to by this pointer (10).

Also it is helpful to recognize that the Foo structure has been padded with extra bytes by the GCC compiler.  This is because the structure fields are not word-aligned.  There is an option one can pass GCC to instruct it not to pad the structure size, but I forgot what it is.

Anyhow, since you have closed this thread, please save any additional questions for a new thread.  Also I would encourage you to write code, such as what was written above, to experiment for yourself how to write/read binary data.

---

