---
title: "Segmentation fault error (core dumped)"
date: 2014-04-03
forum: Programming Talk
---

### Post by zinat on 2014-04-03
I am trying to run the program below with g++ but its giving error segmentation fault (core dumped)..

#include<stdio.h>
 
int main(int argc, char *argv[])
{
 char ch;
 int count=0,i=0;
char c[10];
 FILE *fptr;

fptr=fopen("res.txt","r");
 printf("\nContents of the File is:");
 while((ch=fgetc(fptr))!=EOF)
 {
    if(ch ==' ')
    { i=0;
        while(ch!='\n')
        {
        c[i]=ch;
        i++;
        }
    
    printf("%s  :",c);
  
    }
  
 }
 
fclose(fptr);
 //getch();
return 0;    
}


**res.txt file:**


big-O: 17850


big-O: 80800


big-O: 564750


big-O: 1228500


big-O: 2029500


big-O: 3966600

---

### Post by ofnuts on 2014-04-03
From the look of it, your lines are more that 10 characters long, so you overflow the "c" array, overwriting fptr so when you use to read  the next character it breaks, or overwriting the i index so you ater refer to inexisting memory locations.

Add a couple of fprintf() at the right places so see what happens.

There are ways to read full lines instead of reading them character by character...

---

