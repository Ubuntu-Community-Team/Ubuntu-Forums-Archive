---
title: "fclose() causes segment fault on i686"
date: 2009-10-11
forum: Packaging and Compiling Programs
---

### Post by Shinping Wang on 2009-10-11
Hello
 
I am working on this problem for days. 
The program reads lines form a text file and writes these lines successively into a buffer pointed by pb_start.
The program can be compiled and run successfully on two of my x86_64 Suse 9.3 machines, however it failed both on my i686 Suse9.3 and Ubuntu 9.04 machines.
The following is the program.
```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <errno.h>
#include <unistd.h>
#define MAX_LENGTH 64  //assumming fixed line size of 64 characters

int main(int argc, char **argv) {

        FILE *F_IN;

        int n_line;                     //number of lines to be read from file
        int index = 0;

        struct string {
                char data[MAX_LENGTH];
        } *pb_start, *pb_current;       //pb_start- pointer to the start of counter, pb_current- pointer to the currnet position of counter

        if (argc < 3) {
                puts("Usage: command filename number_of_lines\n");
                exit(0);
        }

        //Open input file
        if (( F_IN = fopen (argv[1], "r")) == NULL) {
                fprintf(stderr, "Open input file failed: %s\n", strerror(errno));
                exit(0);
        }

        //Derive number of lines to be read from file 
        n_line = atoi(argv[2]);

        if ( (pb_start = pb_current = (struct string *) calloc(n_line, sizeof(struct string)) ) == NULL ) {
                fprintf (stderr, "calloc() failed: %s\n", strerror (errno));
                exit(0);
        }


        while (fgets(pb_current->data, MAX_LENGTH, F_IN) != NULL && index < n_line) {
                ++pb_current;
                ++index;
        }

        for ( index = 0, pb_current = pb_start ; index < n_line; index++) {
                printf("%s", pb_current->data);
                ++pb_current;
        }


fclose (F_IN);
free (pb_start);
return (0);
}

```

I run the program with an ASCII text file on my i686 Ubuntu 9.4 machine (Linux shuttle 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686 GNU/Linux.)

A different n_line value is chosen for each test and the each test is repeated for 1000 times. Test results are consistent. Pending on the value of n_line, 
smaller n_line values would generate segment fault while larger n_line values will passed. If the whole text is read (when n_line is larger or equal to the 
lines of the test file) then the program will complete successfully. 

I am sure calloc() and free() work fine, and I believe the problem comes form fopen() and fclose() part. The program/library seems having difficult to release memory allocated for input file when the file is partially read.  

The following show gdb trace of the program when segment fault take place. 
[code]
Program received signal SIGSEGV, Segmentation fault.
0xb7dfcfc8 in ?? () from /lib/tls/i686/cmov/libc.so.6
(gdb) bt full
#0  0xb7dfcfc8 in ?? () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#1  0xb7dfd5b6 in free () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#2  0xb7deafe4 in fclose () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#3  0x080487b0 in main (argc=3, argv=0xbfd1aab4) at t_ring_1.c:52
        F_IN = (FILE *) 0x9c9f008
        n_line = 2
        index = 2
        pb_start = (struct string *) 0x9c9f170
        pb_current = (struct string *) 0x9c9f1f0
(gdb)

I am planning to install the development version of the library and trace over the library to see what went wrong (which is actually out of my league.) So, please let me know if you have experience the same problem and possible solutions. Comments and suggestion are grateful.   Thanks.

---

### Post by MadCow108 on 2009-10-11
putting the blame on the standard library is usually wrong.
the problem is in your code.
This line is the problem:
```

while (fgets(pb_current->data, MAX_LENGTH, F_IN) != NULL && index < n_line) {

```
it executes fgets on a non existing buffer because the boundary condition is checked after fgets
Evaluation of && is from left to right (opposed to the evaluation of = which you used earlier [and which is bad style])
it should be:
```

while (index < n_line && fgets(pb_current->data, MAX_LENGTH, F_IN) != NULL) {

```
now the boundary condition is enforced before the writing

also your missing a boundary check when n_line is greater than the lines in the file while printing
add a:
```

n_line = index;

```
after the reading while loop

---

### Post by Shinping Wang on 2009-10-11
Hello MadCow

Thanks for your promptly reply. 
I follow your suggestions and revised my code, and it works.
The problem , as you point out, comes from order of evaluating && operation.
Thank you very much.   


the > **MadCow108 said:**
> putting the blame on the standard library is usually wrong.
the problem is in your code.
This line is the problem:
```

while (fgets(pb_current->data, MAX_LENGTH, F_IN) != NULL && index < n_line) {

```it executes fgets on a non existing buffer because the boundary condition is checked after fgets
Evaluation of && is from left to right (opposed to the evaluation of = which you used earlier [and which is bad style])
it should be:
```

while (index < n_line && fgets(pb_current->data, MAX_LENGTH, F_IN) != NULL) {

```now the boundary condition is enforced before the writing

also your missing a boundary check when n_line is greater than the lines in the file while printing
add a:
```

n_line = index;

```after the reading while loop

---

