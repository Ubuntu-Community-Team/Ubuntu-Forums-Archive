---
title: "Convert binary to text"
date: 2010-01-13
forum: Programming Talk
---

### Post by DBQ on 2010-01-13
Hi everybody. I have a file in binary format (e.g. 1's and 0's). Somewhere in that file, in the binary format, there is encoded a string which I want to search for. I need to convert the file to text. How may I do that? I want that string to be converted from  binary to ASCII. 

Also, if you know of other ways without converting the file, I would love to hear them too. Help is appreciated.

---

### Post by ssam on 2010-01-13
there is a command called strings that will show you all the bits of ascii in a binary file.

```
strings fileanme
```

---

### Post by baizon on 2010-01-13
[http://en.wikipedia.org/wiki/Binary_file]("http://en.wikipedia.org/wiki/Binary_file")
I hope i understand your question right.
This is how a binary file look like. You need a tool to convert from a binary file to a source code file. Then you can try to search for "strings". 
You can search without converting the binary file (to a source code file) and search there for ASCII, thats the easy way :)

---

### Post by worseisworser on 2010-01-13
> **DBQ said:**
> Hi everybody. I have a file in binary format (e.g. 1's and 0's). Somewhere in that file, in the binary format, there is encoded a string which I want to search for. I need to convert the file to text. How may I do that? I want that string to be converted from  binary to ASCII. 

Also, if you know of other ways without converting the file, I would love to hear them too. Help is appreciated.


How one would go about this depends entirely upon the binary format used. I.e., there is no *general* answer to this question.

edit: Uh, or am I missing something here; why not just open for reading in "text mode" and read+search? Or you could convert the search token to binary first, then search for that in the opened-in-binary-mode file.

---

### Post by DBQ on 2010-01-13
What I mean is this: suppose the program has written a string "hello world" to the file using write/fwrite. How can I retrieve this string in text format in a file?

---

### Post by lisati on 2010-01-13
> **DBQ said:**
> What I mean is this: suppose the program has written a string "hello world" to the file using write/fwrite. How can I retrieve this string in text format in a file?

Maybe something like this: ```
strings {filename} > strings.txt
```

---

### Post by DBQ on 2010-01-13
I tried this, and it does not work. Any other ideas?

---

### Post by lisati on 2010-01-13
Usually when I've been curious about the strings in a binary file an approach like "strings {filename}" has been adequate.

I'm beginning to wonder if a [disassembler]("http://en.wikipedia.org/wiki/Disassembler") or [decompiler]("http://en.wikipedia.org/wiki/Decompiler") might be in order, or would that be overkill? Perhaps some kind of hex-based editor with search facilities or a debugger might be better....

edit: I just remembered, one of the magazines buried in a box in a spare room has a listing for dumping the contents of a file in hex but I don't have the patience to look at the moment. Shouldn't be too hard to write one.

---

### Post by DBQ on 2010-01-13
I am trying hex right now, but so far no luck

---

### Post by MindSz on 2010-01-14
This is a small program that converts a binary file to ascii, but it looks for integers, so if you want to look for text you need to modify it.

```
#include <stdlib.h>
#include<stdio.h>

int integers[8192*4]; //4096*2*bytes_por_int
int i;

FILE *archivo;
FILE *salida;

int main(){

  archivo = fopen("bin_in.txt","r");
  salida = fopen("ascii_out.txt","w");

  for (i = 0; i<8192; i=i+4096)
    fread(integers, 1, 4096, archivo);

  for (i = 0; i<8192; i++){
    fprintf(salida, "%d", integers[i]);
    if((i%10) == 0) fprintf(salida, "\n");
    else fprintf(salida, " ");
  }

  return 0;
}

```

---

