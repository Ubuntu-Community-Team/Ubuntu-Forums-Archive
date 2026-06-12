---
title: "C, fread, binary and text file. What's the difference?"
date: 2009-02-10
forum: Programming Talk
---

### Post by tneva82 on 2009-02-10
Trying to understand what's the difference between those two and where I should use binary. Made quick and simple conversion program that was supposed to copy text from my 3d model file and write it in binary and then read it and write it to another text file(just to check it didn't mess it up anywhere). However both the binary file and new text file are same as old one(except for scandinavian letters getting messed up in the process).

Am I doing it wrong? Here's the code. Isn't doing anything complex. Opens 2 files, one for reading, one for binary writing. Then reads original file until end of file comes and writes it to new file. Then same in reverse.

```

#include <stdio.h>
#include <stdlib.h>

int main( int argc, char **argv )
{
  FILE *pFile=fopen("test.m3d", "r");
  FILE *pFile2=fopen("testbin.m3d", "wb");
  int i;
  do {
    
    i=fgetc(pFile);
    printf("%i", i);
    fputc(i, pFile2);
  } while (i!=EOF);

  fclose(pFile);
  fclose(pFile2);
  pFile=fopen("testbin.m3d", "rb");
  pFile2=fopen("testtext.m3d", "w");

  do {
    i=fgetc(pFile);
    fputc(i, pFile2);
  } while (i!=EOF);
  fclose(pFile);
  fclose(pFile2);
}

```

---

### Post by mnasimh on 2009-02-10
For text representation, you need to supply the string formatter in your read/write function calls. You are reading a byte from text and putting it in binary. You should read formatted text from the text file then convert it to binary and save it. After that, you need to read the binary in the form you got it in the original text file. Reading byte from binary file, loses your information what are the data types. Therefore instead of fgetc and fputc you need to use following, where d defines your data structure (here, d1 is integer, d2 is float):

data d;

        fscanf(pFile, "%d%f", &d.d1, &d.d2);
        fwrite((char *)&d, 1, sizeof(data), pFile2);

and
        fread((char *)&d, 1, sizeof(data), pFile);
        fprintf(pFile2, "%d%f", d.d1, d.d2);

---

### Post by geirha on 2009-02-10
Binary mode vs text mode is a windows thing. Reading and writing a file in text mode in windows, just means that it will translate '\n' to '\r\n' when you write to it, and the opposite when reading. In linux, you always open files in binary mode.

---

### Post by Krupski on 2009-02-10
> **tneva82 said:**
> Trying to understand what's the difference between those two and where I should use binary.

My own personal opinion is that you should use binary for EVERYTHING.

The concept of a "text" file or a "binary" file is only in your mind. In reality, bits are bits.

You should open all files for binary and read or write exactly what you get. If stray carriage returns or linefeeds bother you, deal with them in your program.

That way, you never have to worry "did it add a linefeed?" or "did it copy correctly?"

Think of the FTP protocol. The guy who put ASCII mode into FTP should be shot! I wonder how many files have been corrupted over the years by someone forgetting to type "bin" before they FTP'd a file?  :)

---

### Post by nvteighen on 2009-02-10
> **geirha said:**
> Binary mode vs text mode is a windows thing. Reading and writing a file in text mode in windows, just means that it will translate '\n' to '\r\n' when you write to it, and the opposite when reading. In linux, you always open files in binary mode.
No. Binary files do exist in GNU/Linux. The difference is not clear to me, but it seems just to be that Windows distinguishes binary files and UNIX/Unix-like systems don't, so using the 'b' mode is useless. So, it boils down just to a calling convention issue.

Anyway, the difference is that the binary file is just to dump the memory's content into your file. This makes your file exactly as big as what you're saving it in. In ASCII mode, every character is 1-byte long, so a 2-digit number will be 2-byte long where in binary, it will be much less than 1-byte.

But, binary formats are "proprietary". They depend on your implementation, because to read them you need to know how the memory's structured (for an integer this is trivial, but what about a struct... or in C++, a class?). A text file is more transparent, as it's also human readable.

---

### Post by tneva82 on 2009-02-11
> **Krupski said:**
> You should open all files for binary and read or write exactly what you get. If stray carriage returns or linefeeds bother you, deal with them in your program.

But can one edit file I'm going to read by hand? Ie is it still same old text lines? Or do I need to write converter that changes text file to binary file?

And what's the effect going to be to my program if I change my fopen commands to binary? Will I need to change code to account for doing it in binary mode?

---

### Post by nvteighen on 2009-02-11
> **tneva82 said:**
> 
And what's the effect going to be to my program if I change my fopen commands to binary? Will I need to change code to account for doing it in binary mode?

In GNU/Linux, BSD, etc., nothing. 'b' is there just for compatibility issues. If you use fprintf(), then you're writing in ASCII mode. If you use fwrite(), in binary mode and that's it.

Windows needs to know beforehand whether the file you're opening is going to be ASCII or binary.

---

### Post by Krupski on 2009-02-11
> **tneva82 said:**
> But can one edit file I'm going to read by hand? Ie is it still same old text lines? Or do I need to write converter that changes text file to binary file?

And what's the effect going to be to my program if I change my fopen commands to binary? Will I need to change code to account for doing it in binary mode?

What you think of as "text" is ASCII encoding which is almost universally used today.

For example, the "text" string "hello" will always consist of the 5 hexadecimal characters 68, 65, 6C, 6C, 6F.

To show the end of the string to programs, Windows will add a carriage return AND a linefeed to the string, so in Windows the string is now:

68, 65, 6C, 6C, 6F. 0D. 0A  (the 0D,0A are cr and lf)

In Linux, only a linefeed is used to show the end of a line:

68, 65, 6C, 6C, 6F, 0A

On a MAC, they use a carriage return!

68, 65, 6C, 6C, 6F, 0D

Inside most PROGRAMS, the data is stored with a null (a zero) at the end of the line to mark the true end of the line. In a compiled C program in Linux, the string, in the program, would be stored like this:

68, 65, 6C, 6C, 6F, 0A, 00

However, no matter what happens, the "hello" or "68, 65, 6C, 6C, 6F" always stays the same.

Problems occur when the 0D or the 0A are part of legitimate machine language code.

For example, if I had a program in assembler that had this statement:

    ldaa   #13  ;load register a with decimal 13

It would compile to this machine code:

86, 0D

Now what if some program ASSUMED that the "0D" was a carriage return and "fixed it" and I ended up with:

86, 0A

or...

86, 0D, 0A

(note: the FTP "ascii" mode does exactly this hideous kind of thing!)

Obviously my binary program would be corrupted and no longer work.

That's why I said "always read and write in binary mode" because binary mode really just means "don't mess with the data - read and write it exactly as it is - bit for bit, byte for byte".

Make sense?

-- Roger

---

