---
title: "[C/C++] Extracting a Resource from within Executable"
date: 2011-11-27
forum: Programming Talk
---

### Post by dodle on 2011-11-27
I have an archive, files.tgz, that I converted into an object file with [color=red]objcopy[/color] and linked it into my executable. But, I have no idea of how to access it and extract it. Here is what I want to happen: When the executable is run files.tgz is extracted and placed into the directory.

I used [color=red]readelf[/color] to find the tags in the executable:
```
$ readelf -a test | grep -i "files_tgz"
    73: 0804a0a4     0 NOTYPE  GLOBAL DEFAULT   25 _binary_files_tgz_end
    75: 00000074     0 NOTYPE  GLOBAL DEFAULT  ABS _binary_files_tgz_size
    80: 0804a030     0 NOTYPE  GLOBAL DEFAULT   25 _binary_files_tgz_start
```

So now how do I use this in my code? Do I use a preprocessor to define the data?

[php]#define _binary_files_tgz_end
#define _binary_files_tgz_size
#define _binary_files_tgz_start[/php]

I found the following at [http://stackoverflow.com/questions/4864866/c-c-with-gcc-statically-add-resource-files-to-executable-library](http://stackoverflow.com/questions/4864866/c-c-with-gcc-statically-add-resource-files-to-executable-library), but it is unclear to me what I need to do.
> **ndim]I have used objcopy (GNU binutils) to link the binary data from a file foo-data.bin into the data section of the executable:

```
objcopy -B i386 -I binary -O elf32-i386 foo-data.bin foo-data.o
```

This gives you a foo-data.o object file which you can link into your executable. The C interface looks something like

```
/** created from binary via objcopy */
extern uint8_t foo_data[]      asm("_binary_foo_data_bin_start") said:**
>  asm("_binary_foo_data_bin_size");
extern uint8_t foo_data_end[]  asm("_binary_foo_data_bin_end");
```

so you can do stuff like

```
for (uint8_t *byte=foo_data; byte<foo_data_end; ++byte) {
    transmit_single_byte(*byte);
}
```

or

```
size_t foo_size = (size_t)((void *)foo_data_size;
void *foo_copy = malloc(foo_size);
memcpy(foo_copy, foo_data, foo_size);
```

If your target architecture has special constraints as to where constant and variable data is stored, or you want to store that data in the .text segment to make it fit into the same memory type as your program code, you can play with the objcopy parameters some more.

---

### Post by dodle on 2011-11-27
Okay, I think I figured out how to access it from that link I posted about. Now I need to figure out how to extract it.

[php]#include <iostream>
using namespace std;

int main()
{
    extern size_t files_data[] asm("_binary_files_tgz_start");
    extern size_t files_data_size[] asm("_binary_files_tgz_size");
    extern size_t files_data_end[] asm("_binary_files_tgz_end");
    
    for (size_t *byte = files_data; byte < files_data_end; ++byte)
    {
        cout << byte << endl;
    }
    
    return 0;
}[/php]

Output:
```
0x804a028
0x804a02c
0x804a030
0x804a034
0x804a038
0x804a03c
0x804a040
0x804a044
0x804a048
0x804a04c
0x804a050
0x804a054
0x804a058
0x804a05c
0x804a060
0x804a064
0x804a068
0x804a06c
0x804a070
0x804a074
0x804a078
0x804a07c
0x804a080
0x804a084
0x804a088
0x804a08c
0x804a090
0x804a094
0x804a098
```

---

### Post by gateway67 on 2011-11-27
> **dodle said:**
> ...  Now I need to figure out how to extract it.

Does "tar" offer a C API?  If so, I'm unaware of it.

You could simply recreate the compressed-tar file on the disk, and then use system() to extract the contents.  Something like this:
```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int main(int argc, char** argv)
{
   extern char _binary_files_tgz_start;
   extern char _binary_files_tgz_size;

   const char*  tgz_data = &_binary_files_tgz_start;
   const size_t tgz_size = (size_t)((void*) & _binary_files_tgz_size);

   const char* TGZ_FILE = "/tmp/files_restored.tgz";

   FILE* tgz = fopen(TGZ_FILE, "w+");

   if (tgz)
   {
      char cmd[80];

      fwrite(tgz_data, sizeof(char), tgz_size, tgz);

      fclose(tgz);

      sprintf(cmd, "tar xzvf %s", TGZ_FILE);

      system(cmd);

      unlink(TGZ_FILE);   /* optional */
   }
   else
   {
      perror("Error restoring compressed tar file");
   }

   return 0;
}

```
P.S.  You may want to consider creating the compressed file in the /tmp directory.  You should not assume that you will have write permissions in the current working directory, nor should you rely on the user having a valid USER or HOME environment variable defined.

---

### Post by dodle on 2011-11-27
Thanks that is way cool! Exactly what I needed.

[php]#include <fstream>
using namespace std;

int main()
{
    extern char _binary_files_tgz_start;
    extern char _binary_files_tgz_size;
    
    const char* tgz_data = &_binary_files_tgz_start;
    const size_t tgz_size = (size_t((void*) &_binary_files_tgz_size));
    
    ofstream outfile("out.tgz", ofstream::binary);
    
    int stop = tgz_size;
    int current = 0;
    for (current; current < stop; current++)
    {
        outfile.put(tgz_data[current]);
    }
    
    outfile.close();
    
    return 0;
}[/php]

I was also given another option here: [http://cplusplus.com/forum/general/56128/](http://cplusplus.com/forum/general/56128/)

Thanks again!

---

