---
title: "Create threads just once to use them n times later in C pthread"
date: 2017-11-18
forum: Programming Talk
---

### Post by ljzb on 2017-11-18
[COLOR=#242729][FONT=Arial]The problem is a square matrix multiplication, I was given the sequential script, where the matrices are loaded from a text file. The first line of the text file contains how many pairs of matrices are and their dimensions. So they are all the same size and stored by pairs. One by one all pairs should be multiplied and the result should be stored or printed in Terminal. So, I have to build a fine-grained version of the code, where the user decides to create [/FONT][/COLOR]**n**[COLOR=#242729][FONT=Arial] threads, and for each pair of matrices those [/FONT][/COLOR]**n**[COLOR=#242729][FONT=Arial] threads should take a portion of the job. The main problem is that my fine-grained version, in spite getting correct results, takes much more time than the sequential version to do the job, I reallized the problem was that I was creating and destroying threads for every pair of matrices, which I'm assuming takes a great ammount of time. So, is there a way to create those threads just once, and call them every time I need them?

[/FONT][/COLOR]```
[COLOR=#101094][FONT=inherit]for[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#303336][FONT=inherit]k[/FONT][/COLOR][COLOR=#303336][FONT=inherit]=[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]0[/FONT][/COLOR][COLOR=#303336][FONT=inherit];[/FONT][/COLOR][COLOR=#303336][FONT=inherit] k[/FONT][/COLOR][COLOR=#303336][FONT=inherit]<[/FONT][/COLOR][COLOR=#303336][FONT=inherit]nmats[/FONT][/COLOR][COLOR=#303336][FONT=inherit];[/FONT][/COLOR][COLOR=#303336][FONT=inherit] k[/FONT][/COLOR][COLOR=#303336][FONT=inherit]++)[/FONT][/COLOR][COLOR=#303336][FONT=inherit]{[/FONT][/COLOR][COLOR=#858C93][FONT=inherit]//Loading matrices from matrices.data[/FONT][/COLOR]
[COLOR=#303336][FONT=inherit]printf[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]"\nMatrix #%d of %d\n"[/FONT][/COLOR][COLOR=#303336][FONT=inherit],[/FONT][/COLOR][COLOR=#303336][FONT=inherit]k[/FONT][/COLOR][COLOR=#303336][FONT=inherit]+[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]1[/FONT][/COLOR][COLOR=#303336][FONT=inherit],[/FONT][/COLOR][COLOR=#303336][FONT=inherit]nmats[/FONT][/COLOR][COLOR=#303336][FONT=inherit]);[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
    [/FONT][/COLOR][COLOR=#101094][FONT=inherit]for[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#303336][FONT=inherit]i[/FONT][/COLOR][COLOR=#303336][FONT=inherit]=[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]0[/FONT][/COLOR][COLOR=#303336][FONT=inherit];[/FONT][/COLOR][COLOR=#303336][FONT=inherit] i[/FONT][/COLOR][COLOR=#303336][FONT=inherit]<[/FONT][/COLOR][COLOR=#303336][FONT=inherit]matrixSize[/FONT][/COLOR][COLOR=#303336][FONT=inherit];[/FONT][/COLOR][COLOR=#303336][FONT=inherit] i[/FONT][/COLOR][COLOR=#303336][FONT=inherit]++)[/FONT][/COLOR][COLOR=#303336][FONT=inherit]{[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
        [/FONT][/COLOR][COLOR=#101094][FONT=inherit]for[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#303336][FONT=inherit]j[/FONT][/COLOR][COLOR=#303336][FONT=inherit]=[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]0[/FONT][/COLOR][COLOR=#303336][FONT=inherit];[/FONT][/COLOR][COLOR=#303336][FONT=inherit] j[/FONT][/COLOR][COLOR=#303336][FONT=inherit]<[/FONT][/COLOR][COLOR=#303336][FONT=inherit]matrixSize[/FONT][/COLOR][COLOR=#303336][FONT=inherit];[/FONT][/COLOR][COLOR=#303336][FONT=inherit] j[/FONT][/COLOR][COLOR=#303336][FONT=inherit]++)[/FONT][/COLOR][COLOR=#303336][FONT=inherit]{[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
            fscanf[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#303336][FONT=inherit]fh[/FONT][/COLOR][COLOR=#303336][FONT=inherit],[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]"%lf"[/FONT][/COLOR][COLOR=#303336][FONT=inherit],[/FONT][/COLOR][COLOR=#303336][FONT=inherit]&[/FONT][/COLOR][COLOR=#303336][FONT=inherit]a[/FONT][/COLOR][COLOR=#303336][FONT=inherit][[/FONT][/COLOR][COLOR=#303336][FONT=inherit]i[/FONT][/COLOR][COLOR=#303336][FONT=inherit]][[/FONT][/COLOR][COLOR=#303336][FONT=inherit]j[/FONT][/COLOR][COLOR=#303336][FONT=inherit]]);[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
        [/FONT][/COLOR][COLOR=#303336][FONT=inherit]}[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
    [/FONT][/COLOR][COLOR=#303336][FONT=inherit]}[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
    [/FONT][/COLOR][COLOR=#101094][FONT=inherit]for[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#303336][FONT=inherit]i[/FONT][/COLOR][COLOR=#303336][FONT=inherit]=[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]0[/FONT][/COLOR][COLOR=#303336][FONT=inherit];[/FONT][/COLOR][COLOR=#303336][FONT=inherit] i[/FONT][/COLOR][COLOR=#303336][FONT=inherit]<[/FONT][/COLOR][COLOR=#303336][FONT=inherit]matrixSize[/FONT][/COLOR][COLOR=#303336][FONT=inherit];[/FONT][/COLOR][COLOR=#303336][FONT=inherit] i[/FONT][/COLOR][COLOR=#303336][FONT=inherit]++)[/FONT][/COLOR][COLOR=#303336][FONT=inherit]{[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
        [/FONT][/COLOR][COLOR=#101094][FONT=inherit]for[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#303336][FONT=inherit]j[/FONT][/COLOR][COLOR=#303336][FONT=inherit]=[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]0[/FONT][/COLOR][COLOR=#303336][FONT=inherit];[/FONT][/COLOR][COLOR=#303336][FONT=inherit] j[/FONT][/COLOR][COLOR=#303336][FONT=inherit]<[/FONT][/COLOR][COLOR=#303336][FONT=inherit]matrixSize[/FONT][/COLOR][COLOR=#303336][FONT=inherit];[/FONT][/COLOR][COLOR=#303336][FONT=inherit] j[/FONT][/COLOR][COLOR=#303336][FONT=inherit]++)[/FONT][/COLOR][COLOR=#303336][FONT=inherit]{[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
            fscanf[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#303336][FONT=inherit]fh[/FONT][/COLOR][COLOR=#303336][FONT=inherit],[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]"%lf"[/FONT][/COLOR][COLOR=#303336][FONT=inherit],[/FONT][/COLOR][COLOR=#303336][FONT=inherit]&[/FONT][/COLOR][COLOR=#303336][FONT=inherit]b[/FONT][/COLOR][COLOR=#303336][FONT=inherit][[/FONT][/COLOR][COLOR=#303336][FONT=inherit]i[/FONT][/COLOR][COLOR=#303336][FONT=inherit]][[/FONT][/COLOR][COLOR=#303336][FONT=inherit]j[/FONT][/COLOR][COLOR=#303336][FONT=inherit]]);[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
        [/FONT][/COLOR][COLOR=#303336][FONT=inherit]}[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
    [/FONT][/COLOR][COLOR=#303336][FONT=inherit]}[/FONT][/COLOR][COLOR=#303336][FONT=inherit]

    [/FONT][/COLOR][COLOR=#858C93][FONT=inherit]//Creation of Threads[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
    [/FONT][/COLOR][COLOR=#101094][FONT=inherit]for[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#303336][FONT=inherit]t[/FONT][/COLOR][COLOR=#303336][FONT=inherit]=[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]0[/FONT][/COLOR][COLOR=#303336][FONT=inherit];[/FONT][/COLOR][COLOR=#303336][FONT=inherit] t[/FONT][/COLOR][COLOR=#303336][FONT=inherit]<[/FONT][/COLOR][COLOR=#303336][FONT=inherit]NUM_THREADS[/FONT][/COLOR][COLOR=#303336][FONT=inherit];[/FONT][/COLOR][COLOR=#303336][FONT=inherit] t[/FONT][/COLOR][COLOR=#303336][FONT=inherit]++)[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
    [/FONT][/COLOR][COLOR=#303336][FONT=inherit]{[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
        [/FONT][/COLOR][COLOR=#858C93][FONT=inherit]//The threads are created sequentially[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
        rc [/FONT][/COLOR][COLOR=#303336][FONT=inherit]=[/FONT][/COLOR][COLOR=#303336][FONT=inherit] pthread_create[/FONT][/COLOR][COLOR=#303336][FONT=inherit](&[/FONT][/COLOR][COLOR=#303336][FONT=inherit]threads[/FONT][/COLOR][COLOR=#303336][FONT=inherit][[/FONT][/COLOR][COLOR=#303336][FONT=inherit]t[/FONT][/COLOR][COLOR=#303336][FONT=inherit]],[/FONT][/COLOR][COLOR=#303336][FONT=inherit] NULL[/FONT][/COLOR][COLOR=#303336][FONT=inherit],[/FONT][/COLOR][COLOR=#303336][FONT=inherit] mm[/FONT][/COLOR][COLOR=#303336][FONT=inherit],[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#101094][FONT=inherit]void[/FONT][/COLOR][COLOR=#303336][FONT=inherit]*)[/FONT][/COLOR][COLOR=#303336][FONT=inherit]t[/FONT][/COLOR][COLOR=#303336][FONT=inherit]);[/FONT][/COLOR][COLOR=#303336][FONT=inherit]

        [/FONT][/COLOR][COLOR=#101094][FONT=inherit]if[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#303336][FONT=inherit]rc[/FONT][/COLOR][COLOR=#303336][FONT=inherit])[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
        [/FONT][/COLOR][COLOR=#303336][FONT=inherit]{[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
            printf[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]"ERROR; return code from pthread_create() is %d\n"[/FONT][/COLOR][COLOR=#303336][FONT=inherit],[/FONT][/COLOR][COLOR=#303336][FONT=inherit] rc[/FONT][/COLOR][COLOR=#303336][FONT=inherit]);[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
            exit[/FONT][/COLOR][COLOR=#303336][FONT=inherit](-[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]1[/FONT][/COLOR][COLOR=#303336][FONT=inherit]);[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
        [/FONT][/COLOR][COLOR=#303336][FONT=inherit]}[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
    [/FONT][/COLOR][COLOR=#303336][FONT=inherit]}[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
[/FONT][/COLOR][COLOR=#101094][FONT=inherit]for[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#303336][FONT=inherit]t[/FONT][/COLOR][COLOR=#303336][FONT=inherit]=[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]0[/FONT][/COLOR][COLOR=#303336][FONT=inherit];[/FONT][/COLOR][COLOR=#303336][FONT=inherit] t[/FONT][/COLOR][COLOR=#303336][FONT=inherit]<[/FONT][/COLOR][COLOR=#303336][FONT=inherit]NUM_THREADS[/FONT][/COLOR][COLOR=#303336][FONT=inherit];[/FONT][/COLOR][COLOR=#303336][FONT=inherit] t[/FONT][/COLOR][COLOR=#303336][FONT=inherit]++)[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
    [/FONT][/COLOR][COLOR=#303336][FONT=inherit]{[/FONT][/COLOR][COLOR=#303336][FONT=inherit]

        rc [/FONT][/COLOR][COLOR=#303336][FONT=inherit]=[/FONT][/COLOR][COLOR=#303336][FONT=inherit] pthread_join[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#303336][FONT=inherit]threads[/FONT][/COLOR][COLOR=#303336][FONT=inherit][[/FONT][/COLOR][COLOR=#303336][FONT=inherit]t[/FONT][/COLOR][COLOR=#303336][FONT=inherit]],[/FONT][/COLOR][COLOR=#303336][FONT=inherit]&[/FONT][/COLOR][COLOR=#303336][FONT=inherit]status[/FONT][/COLOR][COLOR=#303336][FONT=inherit]);[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
        [/FONT][/COLOR][COLOR=#101094][FONT=inherit]if[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#303336][FONT=inherit]rc[/FONT][/COLOR][COLOR=#303336][FONT=inherit])[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
        [/FONT][/COLOR][COLOR=#303336][FONT=inherit]{[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
            printf[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]"ERROR; return code from pthread_create() is %d\n"[/FONT][/COLOR][COLOR=#303336][FONT=inherit],[/FONT][/COLOR][COLOR=#303336][FONT=inherit] rc[/FONT][/COLOR][COLOR=#303336][FONT=inherit]);[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
            exit[/FONT][/COLOR][COLOR=#303336][FONT=inherit](-[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]1[/FONT][/COLOR][COLOR=#303336][FONT=inherit]);[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
        [/FONT][/COLOR][COLOR=#303336][FONT=inherit]}[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
    [/FONT][/COLOR][COLOR=#303336][FONT=inherit]}[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
    printResult[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#303336][FONT=inherit]fres[/FONT][/COLOR][COLOR=#303336][FONT=inherit],[/FONT][/COLOR][COLOR=#303336][FONT=inherit]results[/FONT][/COLOR][COLOR=#303336][FONT=inherit]);[/FONT][/COLOR][COLOR=#858C93][FONT=inherit]//Calling printing function[/FONT][/COLOR][COLOR=#303336][FONT=inherit]}[/FONT][/COLOR]
```[COLOR=#242729][FONT=Arial]

[/FONT][/COLOR][COLOR=#242729][FONT=Arial]And the text file should look like this (1 pair of 3x3 size matrices for instance):

[/FONT][/COLOR]```
[COLOR=#7D2727][FONT=inherit]1[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]3[/FONT][/COLOR]
[COLOR=#7D2727][FONT=inherit]1[/FONT][/COLOR][COLOR=#303336][FONT=inherit]-[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]5[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]20[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]0[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]3[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]4[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
[/FONT][/COLOR][COLOR=#303336][FONT=inherit]-[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]2[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]7[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]9[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
[/FONT][/COLOR][COLOR=#303336][FONT=inherit]-[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]2[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]4[/FONT][/COLOR][COLOR=#303336][FONT=inherit]-[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]3[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]11[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]8[/FONT][/COLOR][COLOR=#303336][FONT=inherit]-[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]4[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]6[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]9[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]5[/FONT][/COLOR]
```[COLOR=#242729][FONT=Arial]
[/FONT][/COLOR]

---

### Post by spjackson on 2017-11-19
Welcome to the forums.

You cannot reuse a thread that has completed. What you need to do is give each thread more work to do so that instead of doing just the one multiplication it does (number_of_multiplications/NUM_THREADS) multiplications.

---

### Post by dwhitney67 on 2017-11-26
Look into developing/using a thread-pool.  Read this:  [https://en.wikipedia.org/wiki/Thread_pool](https://en.wikipedia.org/wiki/Thread_pool)

Also, I recommend using C++ or some higher-order programming language, rather than C, because the tools necessary to complete this development task are readily available.  With C, you would need to re-invent a lot of constructs (e.g. a queue).

---

