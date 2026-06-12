---
title: "[C] Code in Binary"
date: 2011-01-04
forum: Programming Talk
---

### Post by jakash3 on 2011-01-04
With this tool, you will be able to code a program using pure binary. Save the ascii 1's and 0's in a text file and this program will take every 8 characters, convert the value to a byte, and output it to the specified file. Example usage:

I have this text file called hello.bin:
```

10110100 00001001
10111010 00001001 00000001
11001101 00100001
11001101 00100000
01101000 01100101 01101100 01101100 01101111 00100100

```Which translates to this in assembly:
```

mov ah,09
mov dx,0109
int 21
int 20
db "hello$"

```Just run the following command:
```

./bincode hello.com hello.bin

```Now you can run hello.com in dosbox and watch the magic happen.
Of course, you can also use it to write PE executables, ELF, images, text files, anything.

bincode.c
```

#include <stdio.h>
#include <stdlib.h>

void help(char* fname) {
    printf(
        "Code programs in binary - by Jakash3\n"
        "Usage: %s outfile infile"
        "Notes:\n"
        "   infile = Text file containing ascii 1's and 0's.\n"
        "            8 bits per byte, all other characters\n"
      "            and whitespace ignored.\n"
        "   outfile = Name of program to create and write to.\n",
        fname
    );
    exit(1);
}

int main(int argc, char** argv) {
    if (argc!=3) help(argv[0]);
    FILE *dst, *src;
    dst = fopen(argv[1],"wb");
    if (!dst) { printf("Could not create or truncate %s\nQuitting...",argv[1]); return 1;}
    src = fopen(argv[2],"r");
    if (!src) { printf("Could not open %s\nQuitting...",argv[2]); return 1;}
    char c, byte=0;
    int i=0, count=0;
    while (!feof(src)) {
        if (i==8) { fwrite(&byte,1,1,dst); byte=0; i=0; count++; }
        fread(&c,1,1,src);
        switch (c) {
            case '1':
                byte |= ((c=='1') << (7-i));
            case '0':
                i++;
        }
    }
    fclose(src);
    if (!fclose(dst)) 
        printf("Wrote %d bytes to %s\n",count,argv[1]);
    return 0;
}

```

---

### Post by worksofcraft on 2011-01-04
> **jakash3 said:**
> With this tool, you will be able to code a program using pure binary.

Lol

While I can empathize with your enthusiasm, IMO serve better purpose if you make this part of an MIX emulator to accompany Knuth's "The Art of Computer Programming" series ISBN 0-201-03809-9 etc...

---

