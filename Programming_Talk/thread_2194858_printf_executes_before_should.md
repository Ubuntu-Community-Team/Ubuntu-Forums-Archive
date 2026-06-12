---
title: "printf executes before should"
date: 2013-12-21
forum: Programming Talk
---

### Post by wingnut2626 on 2013-12-21
```
#include <stdio.h>



char stringA[256];
char stringB[256];


char *pointerA;
char *pointerB;
char selection;
char selection2;


int main(){


  pointerA = stringA;   
  pointerB = stringB;


  void getFirstString(char *pointer);
  void getSecondString(char *pointer);
  void appendString(char *A, char *B);
  


  getFirstString(pointerA);
  getSecondString(pointerB);
  appendString(pointerA,pointerB);


  return 0;




}






void getFirstString(char *pointer){


  void getValue(char *ptr);
  do{
    printf("What is the first string : ");
    getValue(pointer);
    printf("So your 1string is ");
    puts(pointer);
    printf(" Is this correct?  Y or N : ");
    scanf("%c",&selection);
    }while(selection != 'Y');


}


void getSecondString(char *pointer){
  void getValue(char *ptr);
  do{
    printf("What do you wish to append?");
    getValue(pointer);
    printf("So your 2string is ");
    puts(pointer);
    printf(" Is this correct? Y or N : ");
    scanf("%c",&selection2);
    }while(selection2 != 'Y');


}




void getValue(char *ptr){


  fgets(ptr,120,stdin);




}









```


For some reason in getSecondString, the printf statement 'So your 2string is' executes before the fgets statement, looking like:

```

What do you wish to append?So your 2string is

```

Anyone know why?

---

### Post by GeneralZod on 2013-12-21
> **wingnut2626 said:**
> For some reason in getSecondString, the printf statement 'So your 2string is' executes before the fgets statement


That's actually not what is happening; add some strategic debugging statements to get a clearer view of what is going on, here :)

---

### Post by ofnuts on 2013-12-21
By default, when the output is to console, it is line-buffered (in other words output happens when there is a "\n"). So your statement is executed, but the corresponding output is delayed. You have to flush the stream to force output to happen, or you can set the buffering mode for the stream. See [http://www.gnu.org/software/libc/manual/html_node/Controlling-Buffering.html#Controlling-Buffering](http://www.gnu.org/software/libc/manual/html_node/Controlling-Buffering.html#Controlling-Buffering)

---

