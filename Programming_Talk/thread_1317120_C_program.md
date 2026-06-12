---
title: "C program"
date: 2009-11-06
forum: Programming Talk
---

### Post by cmwarre on 2009-11-06
hey guys.  I had this same problem up earlier this week and someone helped me make it compile and I got it to run fine.  But now, I keep getting a segmentation fault.

---

### Post by 0cton on 2009-11-06
I am not that much of a C programmer but AFAIK you must not have function signatures in book_type_prob.c since they are already defined in cody.h
also double mean returns an int (even if it's upcasted it should better return a double)

---

### Post by RaptorJesus on 2009-11-06
*sigh*, HEADERS ARE FOR PASSING FUNCTIONS AND VARIABLES OVER TO OTHER C FILES IN AN ORGANIZED WAY, YOU DO NOT USE THEM FOR WRITING CODE. I assume the reason why it doesn't work is, normally, when you want to compile two different c source files connected with a header, you do something like:
gcc code1.c code2.c 
The header file isn't even mentioned. So, the code is not really being compiled, I think (could be wrong). Solution: put all of your functions in the main .c file, try again, and if that fails, reply again. It also could be that you stored your data file as an incompatible type (.dat), but I didn't take a good enough look at your code to find out.

---

### Post by Druke on 2009-11-06
.dat is plaintext so it should work.

You need to put all your header code in an implementation file like cody.cpp . that's how I'd do it in cpp, not positive with c. Either way, you can't have code that allocates memory in a header file. a rule of thumb, prototypes in a header file, definitions in an implementation file (cody.cpp in this case).

---

### Post by dwhitney67 on 2009-11-06
```

void getval(FILE *fp, double arr[]) {
        int y = 0;
        
        //arr[y] = 1;   WHAT IS THE POINT OF THIS?
        
        //while (arr[y] != EOF) {   THIS CAUSED THE SEGFAULT

        while (!feof(fp)) {
                fscanf(fp, "%lf", &arr[y]);
                y++; }
}

```

P.S.  You should refrain from putting implemented code in header files, but that issue is not the cause of the segfault.  The others who posted before me offered good advice, albeit from an inexperienced developer's perspective.

---

### Post by wolterh on 2009-11-06
RaptorJesus, there is no need to speak in caps. I think everyone can read lower case letters.

But yes, there are many errors.
First, you should only declare data in your header files, not define it.

A good practice is to only include your header file in your c file. Include everything else in the header file.

Do not declare your identifiers in both the header and the source (c) file. Its not necessary and can be a pain when you need to modify a function's declaration.

About the segmentation fault, you could get a debugger. A very popular one is gdb (GNU debugger). I noticed your segfault is in the getval function. 
Clearly, the fault is about the loop going beyond arr's limits (I don't think EOF (end of file) is working here). You have to use the '\0' character, which is the standard ending byte. Now, you might as well use a for loop and iter until the size (which you need to calculate earlier) of the array is reached.

Please paste your code next time in [ code ] tags, and if you do a zip, make sure it is not in that weird MACOSX structure.

---

### Post by dwhitney67 on 2009-11-06
> **woli said:**
> ... You have to use the '\0' character, which is the standard ending byte...
For strings, but not for all types of data.

---

### Post by cariboo on 2009-11-07
It is  against forum policy to do homework problems for you, I think you've had enough help. This thread is closed.

---

