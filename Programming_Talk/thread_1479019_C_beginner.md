---
title: "C beginner"
date: 2010-05-10
forum: Programming Talk
---

### Post by cap10Ibraim on 2010-05-10
I have a problem , first iteration runs fine 
but then while looping it doesn't wait to enter a name 
it directly request to enter id 
I was googling I tried fflush and fgets with no success 
```

#include <stdio.h>
#include <stdlib.h>
#include "employee.h"
int main(){
    int i,n;
    char name[20];
    emp_queue list1;
    initEmpQueue(&list1);
    for(i=0;i<4;i++){
        printf("\nEnter employee name ");gets(name);
        printf("\nEnter employee id ");scanf("%d",&n);
        EmpEnqueue(n,name,&list1);
    }
    Print_emp_queue(list1);
    return 0;
}
```
inserting 
```
while (getchar() != '\n') continue;
```between two scanf(_)s solved the problem

---

### Post by Portmanteaufu on 2010-05-10
When you give it an employee ID and then hit "enter", it takes the number but leaves the "enter" (\n) behind. The next time the loop runs and it goes to read a name, it finds the \n still in the input stream and says "Ah, I'm done reading the name."

Add another fgets() call immediately after the scanf to read the rest of the line.

(By the by, you should always choose fgets() over plain ol' gets() because of security / stability issues.)

---

