---
title: "Comments on this C code please?"
date: 2009-02-20
forum: Programming Talk
---

### Post by Krupski on 2009-02-20
Hi all,

I wanted a quick and dirty Linux version of the "FC.EXE" program is MS-DOS to compare files as pure binary (i.e. FC file1 file2 /b) and found that the "diff" command wasn't what I wanted.

So, I put together a small "fc" clone with the binary compare only part (for now).

I'm a self teaching C "programmer" and I am still climbing the learning curve, which is why I'm asking for comments on the following code.

Specifically, did I do anything wrong, or the "hard way" or whatever? How about coding style?

Comments and criticisms welcomed please.

(P.S. I am *not* a student and this is not homework)

Thanks in advance!

-- Roger


```

////////////////////////////////////////////
// bc - binary file compare sorta
// like ms-dos 'fc /b' command
// compares files byte for byte
// and displays mismatches as
// address: byte1 byte2
////////////////////////////////////////////

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(int argc, char *argv[])
{
    FILE *infile1; // file pointers
    FILE *infile2;

    int d1, d2, count, mmf;

    if(argc != 3) { // quick & dirty param check
        fprintf(stderr, "\nusage: bc file1 file2\n\n");
        exit(1);
    }

    infile1 = fopen(argv[1], "rb"); // try to open files
    infile2 = fopen(argv[2], "rb");

    if(infile1 == NULL || infile2 == NULL) { // exit if either or both failed

        fprintf(stderr, "\nbc: unable to open\n");

        if(infile1 == NULL) {
            fprintf(stderr, "[%s]\n", argv[1]);
        }

        if(infile2 == NULL) {
            fprintf(stderr, "[%s]\n", argv[2]);
        }

        fprintf(stderr, "\n");
        exit(1);
    }

    count = 0; // init "address"
    mmf = 0; // init mismatch flag

    while(1) { // run until first EOF breaks

        d1 = fgetc(infile1); // read a byte...
        d2 = fgetc(infile2); // ...from each file

        if(d1 == EOF || d2 == EOF) { // if either or both are EOF...
            if(d1 != d2) {
                fprintf(stdout, "\nbc: [%s] is %s than [%s]\n\n",
                argv[1], (d1 < d2) ? ("smaller") : ("larger"), argv[2]);
            } else {
                if(!mmf) {
                    fprintf(stdout, "\nbc: no differences encountered\n\n");
                }
            }
            break; // ...then exit the while loop
        }

        if(d1 != d2) { // got 2 good reads, if difference, show it
            fprintf(stdout, "%08X: %02X %02X\n", count, d1, d2);
            mmf = 1; // flag "mismatch found"
        }
        count++; // "address" of next read
    }

    fclose(infile1); // close both files
    fclose(infile2);

    exit(0); // done
}



```

---

### Post by hastur on 2009-02-20
> **Krupski said:**
> 
I wanted a quick and dirty Linux version of the "FC.EXE" program is MS-DOS to compare files as pure binary (i.e. FC file1 file2 /b) and found that the "diff" command wasn't what I wanted.


"diff" ? no. but "cmp" is (or at least could be) what you want.

for the program, nothing big comes to mind, except you could use "open/read" instead of "fopen/write", as they work in binary and avoid the use of streams...

---

### Post by Krupski on 2009-02-20
> **hastur said:**
> "diff" ? no. but "cmp" is (or at least could be) what you want.

for the program, nothing big comes to mind, except you could use "open/read" instead of "fopen/write", as they work in binary and avoid the use of streams...

Thanks for the comments.

I ran across "cmp" as well, but I didn't "like" it's output format.

I really wanted (because I'm used to) the output format of FC.EXE which would show something like this:

```

0000F9C4: 43 FC

```

Which is "address of difference: byte_file1 byte_file2"

As far as "open" vs. "fopen", I'm just in the habit of using the "f" functions (like fopen, fclose, fprintf, etc...) because they are always the same syntax, regardless of whether I use file pointers or STDIN / STDOUT.

Thanks again for the input!

-- Roger

---

### Post by Martin Witte on 2009-02-20
I would change two things
[LIST]
[*]use a do while loop to exit the loop, you see more direct how the loop exits
[*]use return instead of exit, main is defined to return an integer and you avoid inclusion of stdlib.h, it saves a few bytes on the executable size
[/LIST]

You get then
```
////////////////////////////////////////////
// bc - binary file compare sorta
// like ms-dos 'fc /b' command
// compares files byte for byte
// and displays mismatches as
// address: byte1 byte2
////////////////////////////////////////////

#include <stdio.h>
#include <string.h>

int main(int argc, char *argv[])
{
	FILE *infile1; // file pointers
	FILE *infile2;

	int d1, d2, count, mmf;

	if(argc != 3) { // quick & dirty param check
		fprintf(stderr, "\nusage: bc file1 file2\n\n");
		return 1;
	}

	infile1 = fopen(argv[1], "rb"); // try to open files
	infile2 = fopen(argv[2], "rb");

	if(infile1 == NULL || infile2 == NULL) { // exit if either or both failed

		fprintf(stderr, "\nbc: unable to open\n");

		if(infile1 == NULL) {
			fprintf(stderr, "[%s]\n", argv[1]);
		}

		if(infile2 == NULL) {
			fprintf(stderr, "[%s]\n", argv[2]);
		}

		fprintf(stderr, "\n");
		return 1;
	}

	count = 0; // init "address"
	mmf = 0; // init mismatch flag

	do { // run until first EOF breaks

		d1 = fgetc(infile1); // read a byte...
		d2 = fgetc(infile2); // ...from each file

		if(d1 != d2) {
			fprintf(stdout, "\nbc: [%s] is %s than [%s]\n\n",
			argv[1], (d1 < d2) ? ("smaller") : ("larger"), argv[2]);
			fprintf(stdout, "%08X: %02X %02X\n", count, d1, d2);
			mmf = 1; // flag "mismatch found"
		}
		count++; // "address" of next read
	} while (!(d1 == EOF || d2 == EOF));
	if(!mmf) {
		fprintf(stdout, "\nbc: no differences encountered\n\n");
	}
	fclose(infile1); // close both files
	fclose(infile2);

	return 0; // done
}
```

---

### Post by Krupski on 2009-02-20
> **Martin Witte said:**
> I would change two things
[LIST]
[*]use a do while loop to exit the loop, you see more direct how the loop exits
[*]use return instead of exit, main is defined to return an integer and you avoid inclusion of stdlib.h, it saves a few bytes on the executable size
[/LIST]



Cool! Thanks for the editing effort. You're right - the loop looks cleaner. I didn't really like the convoluted "if / if / else" mess I had. Your method is much nicer.

Thanks again!

-- Roger

P.S. I noticed you use 8 space tabs. Is there anything "wrong" with using 4 space tabs as I did?

---

### Post by Martin Witte on 2009-02-20
> **Krupski said:**
> Cool! Thanks for the editing effort.
Appreciated

> **Krupski said:**
> I noticed you use 8 space tabs. Is there anything "wrong" with using 4 space tabs as I did?
Of course there is nothing wrong with that, in fact in gedit my tab width is set to four spaces, I guess they show up as 8 spaces in the forum (in your post the code had spaces, I replaced those with tabs)

---

### Post by nvteighen on 2009-02-20
> **Krupski said:**
> 
P.S. I noticed you use 8 space tabs. Is there anything "wrong" with using 4 space tabs as I did?

Nope if you stay consistent (or when working in a project, you have to adhere to whatever standard the project uses).

EDIT: Looking at your code... it's wise to initialize all pointers you declare (either to NULL or to another value)... so you avoid the possibility of dereferencing a random memory location.

---

### Post by Krupski on 2009-02-20
> **Martin Witte said:**
> Appreciated


Of course there is nothing wrong with that, in fact in gedit my tab width is set to four spaces, I guess they show up as 8 spaces in the forum (in your post the code had spaces, I replaced those with tabs)

Yup that's what happened. I pasted the code into a different editor and it was set to tabs=8.

Since I knew I had used spaces instead of tabs, I thought you purposely converted my 4 to 8 and figured "hey it must be important enough if he changed it" :)

Thanks again for your help!

-- Roger

---

