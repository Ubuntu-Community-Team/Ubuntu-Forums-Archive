---
title: "How can I detect what is causing this segmentation fault in my C file ???"
date: 2016-02-07
forum: Programming Talk
---

### Post by Caue_Sousa on 2016-02-07
Hello everyone !! How are you doing ?? I'm working on a program that use a sorting algorithm (Selection Sort). I'm trying to program a function called SelectionSort that applies the Selection Sort method in a vector, but every single time I try to run the program I get the "Segmentation fault (core dumped)" message. I think that the problem is in the line where I call the function, but I'm not sure. Please, help me !!! Thank you all in advance ^^

Here is my code :
```

#include <stdio.h>
#include <stdlib.h>

#define MAX 5
void SelectionSort(int vet[],int n){
    int aux,i,j;
    for(i = 0; i < n; i++){
        for(j = i+1; j < n; j++){
            if(vet[i] > vet [j]){
                aux = vet[i];
                vet[i] = vet[j];
                vet[j] = aux;
            }
        }
    }
}

int main(){
    int i;
    int array[MAX] = {3,5,2,1,4};
    SelectionSort(array,MAX);

    for( i = 0; i < MAX; i++){
        printf("%d\t", array[i]);
    }
    return 0;
}

```

---

### Post by Caue_Sousa on 2016-02-07
Thank you all, but I have solved the problem by myself and since we cannot delete our own posts ... I'm so sorry ...

---

### Post by steveo314 on 2016-02-07
You don't have MAX declared nor initialized.

---

### Post by mfvpcrec on 2016-02-13
Hello Caue_Sousa I saw that you have resolved this problem but nobody answered your question. How can I detect what is causing this segmentation fault in my C file ? Or How can I detect where is the segmentation fault in my C file ? There is two options or you see and understand all the code and detect where is the segmentation fault or use a tool that help to find where is the problem, this tools are called debuggers. In Linux , believe me, the BEST debugger that I used (for C) is gdb on console without GUI interface. At the very beginning when I started to programming I used the GUI interface of GDB that codeblocks has but the last time I saw that GDB in console is more powerful. To find quickly the segmentation fault compile the C with -g flag and in the console you must write gdb <the name of the executable> then press r (to run the program) and when the segmentation fault happen you must write bt (backtrace) to show the stack and where the segmentation fault happened. This is the quickly way but the real way is like this : You must put breakpoints in the code and execute the code step by step , when the program failed in that line there is  the error and you must understand in that line why the error happened.
In this link explains better GDB than me :) [http://condor.depaul.edu/glancast/373class/docs/gdb.html](http://condor.depaul.edu/glancast/373class/docs/gdb.html)
I hope to not have me wrong

Bye!

---

