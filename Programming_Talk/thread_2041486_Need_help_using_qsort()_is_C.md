---
title: "Need help using qsort() is C"
date: 2012-08-12
forum: Programming Talk
---

### Post by scorpious on 2012-08-12
I've read the man page and done lots of googleing but I still don't understand what I should be putting in the 3rd argument of qsort(). I realize that is is some sort of comparison but that’s it. I've even tried copy and pasting some code directly from [COLOR=Blue]_[this ]("http://roseindia.net/c-tutorials/c-array-sort.shtml")_[/COLOR]website but that just gives me a "makes pointer without cast" error. Can anyone help me out here? I'm wanting to sort the words alphabetically. 


Here's my code. I've put the qsort line in bold. 
```
/**********************************************************************
 * Word sorter
 * sorts a list of words and prints them out
 * compleated:
 * Author:
 * ********************************************************************/

#include <stdio.h>
#include <stdlib.h>

#define MAX_WORD_SIZE 20
#define MAX_WORDS 100

void insertwords(char** array, int numberWords){
    /*Inserts the words into 'array'*/
    int i = 0;
    for (i = 0;i<numberWords;i++){
        array[i] = malloc(MAX_WORD_SIZE);
        fgets(array[i], MAX_WORD_SIZE, stdin);
    }
}

void printwords(char** array, int numberWords){
    /*prints the words. Each word will be printed on a new line.*/
    int i = 0;
    for (i = 0;i<numberWords;i++){
        printf("%s\n", *(array+i));
    }
}

    

int main(){
    
    int numbers[2] = {'\0'};
    scanf("%d %d", &numbers[0], &numbers[1]);
    char **array;
    array = malloc(sizeof(char*)*MAX_WORDS);

    
    insertwords(array, numbers[0]);
    printwords(array, numbers[0]);
    
    
    printf("after the sort\n\n");
**    qsort(array, MAX_WORDS, ?????);**
    printwords(array, numbers[0]);
    
    
    
    return 0;
}
```Here's my test file if anyone is wanting to run it.
```
10 1
abracadabra
xylophone
fnurdle
abracadabra
oxcart
xylophone
aaa
zzz
fnurdle
oxcart
```

---

### Post by Bachstelze on 2012-08-12
So you have read the man page. It says:

```
       The contents of the array are sorted in ascending order according to a comparison function pointed to by  com&#8208;
       par, which is called with two arguments that point to the objects being compared.

       The comparison function must return an integer less than, equal to, or greater than zero if the first argument
       is considered to be respectively less than, equal to, or greater than the second.  If two members  compare  as
       equal, their order in the sorted array is undefined.

```

Which part of that do you not understand?

---

### Post by spjackson on 2012-08-12
If you paste the example cmpstringp funstion from the man page, then you want:
```

qsort(array, numbers[0], sizeof(char *), cmpstringp);

```Note that there are 4 parameters and the comparison function is the 4th, not the 3rd. If you use MAX_WORDS as the 2nd parameter, then you are telling qsort to access memory you have not allocated.

---

### Post by scorpious on 2012-08-12
[LEFT]@[Bachstelze]("http://ubuntuforums.org/member.php?u=51114")
That makes sense but lets look at the example.

It appears to me that they call the function cmpstringp with no arguments but the function takes in two arguments. I don't understand how that works. Does qsort put 2 arguments in automatically? 
[/LEFT]

---

### Post by scorpious on 2012-08-12
@spjackson 

thanks for your help.

---

### Post by trent.josephsen on 2012-08-12
> **scorpious said:**
> 
```
    array = malloc(sizeof(char*)*MAX_WORDS);
```

malloc(MAX_WORDS * sizeof *array) would be better.

---

### Post by Barrucadu on 2012-08-13
> **scorpious said:**
> It appears to me that they call the function cmpstringp with no arguments but the function takes in two arguments. I don't understand how that works. Does qsort put 2 arguments in automatically? 

Where? Here?

```
qsort(array, numbers[0], sizeof(char *), cmpstringp);
```

That's not calling the function cmpstringp with no arguments (that'd be "cmpstringp()"), that's passing a pointer to cmpstringp.

---

