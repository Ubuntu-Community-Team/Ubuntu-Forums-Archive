---
title: "[c] printing out characters"
date: 2010-05-15
forum: Programming Talk
---

### Post by Serious George on 2010-05-15
Hello, I'm currently going through the programming challenges (at challenge 2) but have run into a problem. On print of the array, it just prints out smily faces. Does anyone know why?

Thank you.

```
#include <stdio.h>
#define BUF_SIZE 60
void printchars(char arr[]);

int main() {
    char forumname[BUF_SIZE];
    int age, userid, i = 0;
    
    printf("Please enter your name.\n");
    while(forumname[i] = getchar() != '\n') {
        i++;
    }
    printchars(forumname);
}

void printchars(char arr[]) {
    int i = 0;
    while(arr[i] != '\0') {
        printf("%c ", arr[i]);
        i++;
    }
}
```

---

### Post by MadCow108 on 2010-05-15
you need parentheses around your while argument. compile with -Wall and the compiler even suggests it.
but then note that when inputing int he terminal by pressing return you insert 2 characters the character and newline
so you have to press ctrl+d (= EOF) after each char to get your code to work

consider using line based functions like fgets

---

### Post by Serious George on 2010-05-15
Thanks for the reply. I should have mentioned it was being compiled on Windows (laptop is at uni dorms). Got it working, I forgot to add a null terminator to the end.

Edit:
```
#include <stdio.h>
#define BUF_SIZE 20
void printchars(char arr[]);

int main() {
    char forumname[BUF_SIZE] = {0};
    int age, userid, i = 0;
    
    printf("Please enter your name.\n");
    while(i<BUF_SIZE-1) {
        forumname[i] = getchar();
        if(forumname[i] == '\n') {
            forumname[i] = '\0';
            break;
        }
        i++;
    }
    //forumname[i+1] = '\0';
    printchars(forumname);
    //printf("Please enter your age.\n");
    //scanf("%d",  &age);
}

void printchars(char arr[]) {
    int i = 0;
    while(arr[i] != '\0') {
        printf("%c", arr[i]);
        i++;
    }
    printf("\n");
}
```I put in some bound checking, it's set to 20 now for ease of input to test. At the 19th index, the terminator gets added. Im having a bit of trouble comprehending the throw-away of the characters that are out of the arrays bounds (they are shown as if they have gone into and overflowed the array). The only thing I can think of is the cmd still displays chars until the condition is met (enter) even though it has already met the condition? (i don't know, just me rambling here ^^). Could someone explain this?

---

