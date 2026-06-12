---
title: "C code problem"
date: 2009-11-03
forum: Programming Talk
---

### Post by cmwarre on 2009-11-03
Hi.  I'm taking a c programming class and I'm having problems getting this particular problem to compile.  I believe that the problem is all in the calls to my sub routines and I'm having trouble trying to find examples on how to define an array as a parameter without getting this error.  
It could also be a problem in the terminal that I don't know about because I'm including a custom header file for the first time.  Is there something like "gcc example.c *-lm*"
with the "-lm" for the header file?  

also do you guys know how to compress a folder as a .tar.gz with a mac when your not using ubuntu?

---

### Post by terry_a_g on 2009-11-04
Compiled fine here using gcc -g -o hw7 -lm book_type_prob.c

You're getting the warnings because you're passing an array of ints to a function that's expecting an array of doubles without using an explicit cast.

For future reference function prototypes usually go in .h files, and their implementations go in .c files.

Your program gets caught in an endless loop in because fp is never changed.

```
void getval(FILE *fp, double arr[]) {
    int y = 0;
    
    while (fp != NULL) {
        fscanf(fp, "%lf", &arr[y]);
        y++;
    }
}
```You were close, but not quite right.  You should be checking the return value of fscanf and using that as your loop condition.

As far as creating tar.gz files goes, change into the directory that contains the directory you want to archive and use tar czf YOUR_FILENAME.tar.gz YOUR_DIRECTORY  This works for gnu tar, which I'm almost positive is the default tar on OSX.  If it complains use  tar cf YOUR_FILENAME.tar YOUR_DIRECTORY and then gzip YOURFILENAME.tar

Change YOUR_FILENAME and YOUR_DIRECTORY as needed.

---

### Post by cmwarre on 2009-11-04
Thanks!!!  It's up and working now!  I appreciate you help :D

---

