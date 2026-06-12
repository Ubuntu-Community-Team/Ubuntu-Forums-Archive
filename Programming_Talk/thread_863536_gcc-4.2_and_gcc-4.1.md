---
title: "gcc-4.2 and gcc-4.1"
date: 2008-07-18
forum: Programming Talk
---

### Post by podiyan on 2008-07-18
I have written a small c program but i got different answers when i compiled with gcc-4.2 and gcc-4.1. Can you please tell me whether my code is incorrect or its problem with gcc.

code k.c
********
#include<stdio.h>

int main(){
int i,j,k,a,b,c;
int nocc,nvirt;
int index;

scanf("%d %d",&nocc,&nvirt);
printf("You typed %d and %d\n",nocc,nvirt);

for(i=0 ; i<nocc; i++) {
for(j=0 ; j<i ; j++)   {
for(k=0 ; k<j ; k++)   {
for(a=0 ; a<nvirt; a++){
for(b=0 ; b<a ; b++)   {
for(c=0 ; c<b ; c++)   {
index = index + 1;
}}}}}}
printf("%d \n",index);

return (0);
}

compilation and run
*******************
$ gcc-4.1 k.c
$ ./a.out 
3 3
You typed 3 and 3
1 

$ gcc-4.2 k.c
$ ./a.out 
3 3
You typed 3 and 3
32607

---

### Post by WW on 2008-07-18
The difference is probably because you didn't initialize index.  Add the line **index = 0;** before entering the mega-loop.

---

### Post by podiyan on 2008-07-18
Thanks a lot

---

