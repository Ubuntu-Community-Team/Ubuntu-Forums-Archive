---
title: "GCC not working?? - real newbie"
date: 2010-11-26
forum: Packaging and Compiling Programs
---

### Post by dkramer on 2010-11-26
I hope there is some simple help here - already tried two other forums.
Running 10.4 from flash drive (in live mode - not sure what that is)
 
From terminal tried to compile simple test program using gcc
(alreadey loaded sudo.....get_essentials)
 
Source code stored in both Ubuntu root and a new Documents folder
from terminal:
Gcc test_code.c
 
it reurns with no errors (back to terminal prompt)  but .o or .exe not found in any folders....
 
Confused......

---

### Post by SevenMachines on 2010-11-26
Its difficult to tell unless you post more information, files, commands, etc. But, heres a simple example...

# make sure the build-essential package is installed, only needed once!
>  $ sudo apt-get install build-essential# Create a simple c file
test.c:
> #include <stdio.h>

int main(int args, char ** argv){
    printf("Hello world!\n");
    return 0;
}
# compile 'test.c' file and output(-o) executable 'test', otherwise it defaults to outputting 'a.out'
> $ gcc -o test test.c# Success!!
> $ ./test 
Hello world!

---

### Post by ender4 on 2010-11-26
by default gcc will delete the .o files, and it compiles to a file called a.out, my guess is you just want to add the -o flag with the name of the file you want (note that on linux executables generally don't have any extension, whereas on windows they generally have a .exe extension), so you would use

gcc test_code.c -o test_exec

then call the program with
./text_exec

---

