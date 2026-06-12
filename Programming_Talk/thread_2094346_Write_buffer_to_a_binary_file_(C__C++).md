---
title: "Write buffer to a binary file? (C / C++)"
date: 2012-12-13
forum: Programming Talk
---

### Post by Kdar on 2012-12-13
Hello everyone,

I am working on one program that generates a lot of data...eventually it can be in GB range. And the way I am doing it now is just by writing to ascii file everything time... like this:
```
ofstream flowC("outputfile.out"); // declared at the start
flowC << prevsid << ", " << threadid << endl; // inside working block
//repeats many many times
```
However, this is not very efficient. First because I am writing ascii and because I am writing to **** every single time.

To improve this.. I want to write 2nd line above to a buffer of size 2048 or bigger. And then when buffer gets full I would write it to a file and emptry it. So I would write file in chunks of 2048 or so.... I also want to avoid writing file in ascii, but instead generate a binary file.

Can someone help me how to make this work correctly? I found some examples of how to write to a buffer but I am not sure how to write it from there to binary file.
```
char buffer[2048];
flowC.rdbuff()->pubsetbuf(buffer, 2048);
.......
flowC << prevsid << ", " << threadid << endl;
```
I also eventually would like to compress the buffer before I write it to a file. I am not sure how this can be done yet in C or C++.

---

### Post by Bachstelze on 2012-12-13
Make up your mind, C or C++?

---

### Post by MG&amp;TL on 2012-12-13
> **Kdar said:**
> 
Can someone help me how to write it to buffer and then to binary file (not ascii) in C++ or C.
I also eventually would like to compress the buffer before I write it to a file... I mean like pipe it to gzip or some other compressor from a buffer and then to a file. I am not sure how this can be done yet in C or C++

What Bachstelze said. I'm assuming you're going with C++, as you've got some C++-specific code in there.

Binary files and ASCII files are the same thing. All files are binary, but text editors interpret binary as ASCII. If you want to view a file as binary, get a binary viewer/editor. I like *bless*.

Either write a compression algorithm for the data at hand (For instance, if there is going to be a lot of repetition in your code, you could simply output a number and then the data set...data has peculiarities of its own, work out what's best for yours), or you can actually [gzip it.]("http://www.boost.org/doc/libs/1_38_0/libs/iostreams/doc/classes/gzip.html")

---

### Post by Kdar on 2012-12-13
well, sorry about that, C++.

But how can I make it save a bit of space? I was thinking if I write to some binary format (non-human readable) I could save space... and then I can have another program to decode and read that binary file.

---

### Post by Bachstelze on 2012-12-13
Just gzip/bzip2/xz it, depending on your speed/space requirements.

---

### Post by dwhitney67 on 2012-12-13
> **Kdar said:**
> well, sorry about that, C++.

But how can I make it save a bit of space? I was thinking if I write to some binary format (non-human readable) I could save space... and then I can have another program to decode and read that binary file.

Here's a clue:

```

#include <fstream>

int main()
{
   std::fstream binFile("outputfile.out", std::ios::out | std::ios::binary);

   int value = 10;

   binFile.write(reinterpret_cast<char*>(&value), sizeof(value));
}

```

---

