---
title: "problems with pointer and segfault in a very basic prog"
date: 2008-12-27
forum: Programming Talk
---

### Post by MeLight on 2008-12-27
Hi, I'm writing a program in c for a school project, one of the modules of the program is getting two arguments (patt and repl) and is also taking lines from stdin (using getline()) and must replace every occurrence of patt with repl.
Two problems:
A. I get segmentation faults when I'm trying to free the pointer allocated by getline()
B. Even if I comment out that free() statement, the string I get after running the replace function is printed as if no replacement occured! I'm passing a pointer to that string to the replacing function. 
here's the short version of the code:

[PHP]
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <string.h>

int strreplace(char *str, char *patt, char *repl);

int main(int argc, char** argv) {
    char *str;             //replace pattern
    size_t rsize;           //num of read files by getline()
    int nbytes;
    
    char *patt = argv[1];   //pattern to look for
    char *repl = argv[2];   //replace found pattern with this
    
    str = NULL;     //getline() needs NULL and 0 in order to allocate new mem
    rsize = 0;

    //getline() allocates the need memory for the line in to *str
    //it is user's responsibility to free() the allocated mem
    if((nbytes = getline(&str, &rsize, stdin)) < 0) {   //end of file
        exit(1);
    }
    
    if( argc == 3 && (strstr(str, patt) != NULL) ) {
        strreplace(str, patt, repl);        //this function replaces patt with repl
        printf("str: %s", str);
    }
    
    return (EXIT_SUCCESS);
}

int strreplace(char *str, char *patt, char *repl) {
    char *occ = NULL;              //ptr to first char of first occurence of the pattern in str
    char *temp;             //temp string to hold str
    int poss, pose;         //poss - pos of the first char of patt in str, pose - after last char of patt
    int diff = (strlen(repl) - strlen(patt));
    int tempsize;   
    
    while((occ = strstr(str, patt)) != NULL) {
        tempsize = strlen(str) + diff + 1;
        temp = (char*)malloc(sizeof(char)*(tempsize));
        
        poss = strlen(str) - strlen(occ);       //getting the pos of the first char of patt in str
        pose = poss + strlen(patt);             //getting pos of the char after last char of patt in str
        
        memcpy(temp, str, poss);
        memcpy(temp + poss, repl, strlen(repl));
        memcpy(temp + poss + strlen(repl), str + pose, strlen(&(str[pose])));
        temp[tempsize] = '\0';

        free(str);          // here I get the seg.fault if i don't comment this out

        str = (char*)malloc(sizeof(char)*tempsize);
        memcpy(str, temp, tempsize);

        free(temp);

        //printf("-----\nstr: %s strlen: %d\n------\n", str, strlen(str));
    }
    
    return 0;   //success
}
[/PHP]

---

### Post by jbrackett on 2008-12-27
str comes from outside of the while loop but its freeing inside the while loop so its probably freeing twice and seg faulting the second time through.

Hmm maybe I was hasty I didn't notice the new initialization of str

---

### Post by jbrackett on 2008-12-27
Maybe the problem lies elsewhere in the code.  I can run this reduced version just fine.  What inputs are you using?

---

### Post by MeLight on 2008-12-27
the arguments are:
f XXXX

when you give it lines like:
f jshk  f fff fkjshjfff

(lots of f's to be replaced) and please take a look and tell me if it actually prints out a different pattern

---

### Post by nvteighen on 2008-12-27
Hmm... Your problem is the following:strreplace() accepts str as a pointer to some place in memory. Perfect. Then, you resize it by deallocating and then, allocating new memory using str as the pointer to it. 

But you surely know that anything declared inside a function, including the parameters, is destroyed after the function returns. So, the 'str' the function uses is wiped out. So, the original variable you passed to the function is also blanked out.

And I'm sure the segfault is occurring somewhere else. Have you checked gdb?

Ideas:
1) There's already a function that resizes heap-allocated memory: realloc()

2) When you want to manipulate pointers to memory from one function to another, you have two possibilities: either make the function return the new pointer or make the function accept a double pointer so that you are able to modify the original pointer (when the function returns, you'll lose the pointer to the pointer).

Also, your example code will issue a warning, as getline() is a non-POSIX GNU extension (and I don't know how to make gcc aware of them...)

---

### Post by dwhitney67 on 2008-12-27
> **nvteighen said:**
> Hmm... Your problem is the following:strreplace() accepts str as a pointer to some place in memory. Perfect. Then, you resize it by deallocating and then, allocating new memory using str as the pointer to it. 

But you surely know that anything declared inside a function, including the parameters, is destroyed after the function returns. So, the 'str' the function uses is wiped out. So, the original variable you passed to the function is also blanked out.

And I'm sure the segfault is occurring somewhere else. Have you checked gdb?

Ideas:
1) There's already a function that resizes heap-allocated memory: realloc()

2) When you want to manipulate pointers to memory from one function to another, you have two possibilities: either make the function return the new pointer or make the function accept a double pointer so that you are able to modify the original pointer (when the function returns, you'll lose the pointer to the pointer).

Also, your example code will issue a warning, as getline() is a non-POSIX GNU extension (and I don't know how to make gcc aware of them...)

I believe Idea #2 is correct, yet the program works by chance (see comment at the end of this post) when the following statement is modified (btw, this is where the bug lies); change
[php]
temp[tempsize] = '\0';
[/php]
to be:
[php]
temp[tempsize-1] = '\0';
[/php]
However, as nvteighen has pointed out, the address of str should be passed to the function.  The fact that the system returned the same address from malloc() that was just relinquished using free() is sheer coincidence.  As is, the code is hiding a dormant bug that could explode if other data items had been allocated directly after the original space allocated to str.

---

### Post by MeLight on 2009-01-02
Ok, thanx a lot everyone, I got it working, a function which replaces patt1 with patt2 in a given string and changes it's size if needed. It also takes care of special cases - empty second pattern, when first pattern is a substring of the second pattern and vice versa.
I'm also pretty sure there are no memo leeks! :D

```
//replace all patt with repl in str
int strreplace(char **str, char *patt, char *repl) {
    char *t;
    char *occ = NULL;                       //ptr to first char of first occurence of the pattern in str
    int diff = strlen(repl) - strlen(patt); //to calculate if we need to realloc
    int poss, pose, posne;

    int strsize = strlen(*str) + 1; //including '\0'
    char *temp;

    temp = malloc(sizeof(char)*(strsize));
    strcpy(temp, (*str));

    int p = 0;  //tells us where to start searching for pattern
    while((occ = strstr(&(*str)[p], patt)) != NULL) {
        poss = strlen(*str) - strlen(occ);                  //start of occurence
        pose = strlen(*str) - (strlen(occ) - strlen(patt)); //end of occurence
        posne = pose + diff;                                //end of new pattern

        if(diff > 0) {  //realloc()ing if more space is needed
            strsize += diff;
            if((t = realloc(*str, strsize)) == NULL) {
                perror("filter: failed to realloc");
                free(temp);
                return -1;
            }
            else
                *str = t;

            if((t = realloc(temp, strsize)) == NULL) {
                perror("filter: failed to realloc");
                free(temp);
                return -1;
            }
            else
                temp = t;
        }

        strcpy(&((*str)[poss]), repl);
        strcpy(&((*str)[posne]), &temp[pose]);
        strcpy(temp, *str);

        p = posne;  //start searching in new iteration from posne
    }

    free(temp);
    return 0;
}
```

---

