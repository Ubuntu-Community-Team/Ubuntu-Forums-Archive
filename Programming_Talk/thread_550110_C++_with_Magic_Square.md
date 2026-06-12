---
title: "C++ with Magic Square"
date: 2007-09-13
forum: Programming Talk
---

### Post by 008325 on 2007-09-13
i have a question about the magic square

for example , 3 * 3 magic square = 1,2,3,4,5,6,7,8,9

and user input to string array

1 2 3
4 5 6
7 8 9

how can i check the string array value are unique and contain 1 to 9?

---

### Post by aks44 on 2007-09-13
WRT the "1 to 9" validation, it's quite easy to test the strings / characters and see if they match the allowed character range.

Concerning their uniqueness, std::vector<bool>, std::set<int> (which would be overkill though) or even a custom bitfield could all do the trick, since your set of possible values is very small.

---

### Post by gnusci on 2007-09-13
Here one small code that can help you to find the solution:


[PHP]
// numbers.c
#include <stdio.h>

int count_number( char* s, char num ){
    int count = 0;
    while( *s ){
        if((char)*s == num){
            count++;
        }
        s++;
    }
    return count;
}

// 0-9
char NUM[10] = {'0','1','2','3','4','5','6','7','8','9'};

int main(void){

    int i, n;
    char magic[10] = {'5','1','3','3','2','5','1','7','1','9'};

    for(i=0; i<10; i++){
        n = count_number(magic,NUM[i]);
        printf("the number [%c] is %i times\n",NUM[i],n);
    }
    return 0;
}

[/PHP]

**> gcc number.c -o number**
**> ./number**

---

### Post by CptPicard on 2007-09-13
Too complex. :) All he needs to do is to convert into ints or chars (in the byte sense) when reading input, and just have a bool[9] as suggested to keep track of whether a number has been seen already. Each element should be true in the end, and just once .. trying to set true one more time should be an error. It's a few lines.

Btw, this has the dinstinct whiff of homework to it... :)

---

### Post by aks44 on 2007-09-13
> **CptPicard said:**
> Btw, this has the dinstinct whiff of homework to it... :)

That's the very reason why I kept my answer quite vague, I was waiting for more info from the OP. ;)

---

