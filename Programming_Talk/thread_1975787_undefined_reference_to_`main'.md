---
title: "undefined reference to `main'"
date: 2012-05-07
forum: Programming Talk
---

### Post by mikewbma on 2012-05-07
So I am apply for a job and they want to implement a kind of linked list.
I did the testing before i seperated the file in to the header and move the main to a
testing file.

However after I rearranged the content I get the
/usr/bin/ld: /usr/lib/debug/usr/lib/crt1.o(.debug_info): relocation 0 has invalid symbol index 11
/usr/bin/ld: /usr/lib/debug/usr/lib/crt1.o(.debug_info): relocation 1 has invalid symbol index 12
/usr/bin/ld: /usr/lib/debug/usr/lib/crt1.o(.debug_info): relocation 2 has invalid symbol index 2
/usr/bin/ld: /usr/lib/debug/usr/lib/crt1.o(.debug_info): relocation 3 has invalid symbol index 2
/usr/bin/ld: /usr/lib/debug/usr/lib/crt1.o(.debug_info): relocation 4 has invalid symbol index 11
/usr/bin/ld: /usr/lib/debug/usr/lib/crt1.o(.debug_info): relocation 5 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/crt1.o(.debug_info): relocation 6 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/crt1.o(.debug_info): relocation 7 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/crt1.o(.debug_info): relocation 8 has invalid symbol index 2
/usr/bin/ld: /usr/lib/debug/usr/lib/crt1.o(.debug_info): relocation 9 has invalid symbol index 2
/usr/bin/ld: /usr/lib/debug/usr/lib/crt1.o(.debug_info): relocation 10 has invalid symbol index 12
/usr/bin/ld: /usr/lib/debug/usr/lib/crt1.o(.debug_info): relocation 11 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/crt1.o(.debug_info): relocation 12 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/crt1.o(.debug_info): relocation 13 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/crt1.o(.debug_info): relocation 14 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/crt1.o(.debug_info): relocation 15 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/crt1.o(.debug_info): relocation 16 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/crt1.o(.debug_info): relocation 17 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/crt1.o(.debug_info): relocation 18 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/crt1.o(.debug_info): relocation 19 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/crt1.o(.debug_info): relocation 20 has invalid symbol index 20
/usr/lib/gcc/x86_64-linux-gnu/4.4.3/../../../../lib/crt1.o: In function `_start':
(.text+0x20): undefined reference to `main'
collect2: ld returned 1 exit status


Here is my code.
seq.c
```

#include "seq.h" 
#include <stdio.h> 
#include <stdlib.h> 
#include <string.h> 
 
void insert (linkedlist* list, int number, char* msg){     
    element* ele = malloc(sizeof(element)); 
    ele->number = number; 
    ele->text = msg; 
    if (list->size == 0){             
            list->head = ele; 
            list->size ++; 
            list->tail = ele; 
            ele->next = NULL; 
            ele->prev = NULL; 
    }else{ 
        element *temp = ((element*)(list->head)); 
        while(1){ 
                if (temp->number <= number){ 
                    if (temp == list->tail){ 
                        list->tail = ele; 
                        temp->next = ele; 
                        ele->prev = temp; 
                        list->size++; 
                        break; 
                    }else{                         
                        if ((((element*)(temp->next))->number) > number){ 
                            ((element*)(temp->next))->prev = ele; 
                            ele->next = temp->next; 
                            temp->next = ele; 
                            ele->prev = temp; 
                            list->size++; 
                            break; 
                        }                         
                    }                     
            }else{ 
                if (temp == list->head){ 
                    list->head = ele;                     
                }else{ 
                    (((element*)(temp->prev))->next) = ele; 
                    ele -> prev = (element*)(temp->prev); 
                }                 
                ele->next = temp; 
                temp->prev = ele; 
                list->size++; 
                break; 
            }             
            temp = ((element*)(temp->next)); 
        } 
    } 
} 
 
linkedlist* searchbynumber(linkedlist* list,int lowerbound,int upperbound){ 
    linkedlist *newlist = malloc(sizeof(linkedlist)); 
    element *temp = ((element*)(list->head)); 
    do{ 
        if((temp->number >= lowerbound)&&(temp->number <= upperbound)){ 
            insert(newlist,temp->number,temp->text); 
        } 
        temp = temp->next; 
    }while((temp->number <= upperbound)&&(temp != list->tail));     
     
    return newlist; 
} 
 
void printlinkedlist(linkedlist* list){ 
    element *temp = ((element*)(list->head)); 
    int counter = 0; 
    printf ("Size of this linked list is %d\n",list->size); 
    do{ 
        if (list->size == 0){ 
            printf("Empty linked list\n"); 
            break; 
        }else{             
            printf("Position %d number: %d message: %s\n",counter,temp->number,temp->text); 
            counter++; 
            temp = ((element*)(temp->next)); 
        }         
    }while(counter < list->size); 
} 
 
void deletebynumber(linkedlist* list,int lowerbound,int upperbound){ 
    element *temp = ((element*)(list->head)); 
    do{ 
        if ((temp->number >= lowerbound) && (temp->number <= upperbound)){ 
            ((element*)(temp->prev))->next = temp->next; 
            ((element*)(temp->next))->prev = temp->prev; 
        } 
        element *ko = temp; 
        temp = (element*)temp->next; 
        free(ko); 
    }while((temp->number <= upperbound)&&(temp != list->tail));     
} 
 
int isSubstring (char* subject, char* string){ 
    int count = 0; 
    int i; 
    for (i = 0; i < strlen(subject); i++){ 
        if(subject[i] == string[count]){ 
            count++; 
        } else { 
            count = 0; 
        } 
        if (count == strlen(string)) 
            return 1; 
    } 
    return 0; 
} 
 
linkedlist* searchbystring(linkedlist* list,char* string){ 
    linkedlist *newlist = malloc(sizeof(linkedlist)); 
    element *temp = ((element*)(list->head)); 
    do{ 
        if (isSubstring(temp->text,string)){ 
            insert(newlist,temp->number,temp->text); 
        } 
        temp = temp->next;         
    }while(temp != list->tail); 
    return newlist; 
} 
 
```

seq.h
```


typedef struct {
    
    void *prev;
    int number;
    char *text;
    void *next;
    
} element;

typedef struct {
    
    element *head;
    int size;
    element *tail;
    
} linkedlist;

void insert (linkedlist* list, int number, char* msg);
linkedlist* searchbynumber(linkedlist* list,int lowerbound,int upperbound);
void printlinkedlist(linkedlist* list);
void deletebynumber(linkedlist* list, int lowebound,int upperbound);
int isSubstring(char* subject, char* string);
linkedlist* searchbystring(linkedlist* list,char* string);

```

testseq.c
```

#include "seq.h"

int main(int argc,char* argv[]){
    linkedlist *newlist = malloc(sizeof(linkedlist));
    {
    element* ele1 = malloc(sizeof(element));
    ele1->prev = NULL;
    ele1->number = 1;
    ele1->text = "Sober";
    
    element* ele2 = malloc(sizeof(element));
    ele2->prev = ele1;
    ele2->number = 2;
    ele2->text = "Sober Men";
    
    element* ele3 = malloc(sizeof(element));
    ele3->prev = ele2;
    ele3->number = 3;
    ele3->text = "Sober Male";
    ele3->next = NULL;
    
    ele1->next = ele2;
    ele2->next = ele3;
    newlist->head = ele1;
    newlist->tail = ele3;
    newlist->size = 3;
    
    
    insert (newlist,-4,"bad");
    insert (newlist,-4,"bad");
    insert (newlist,-3,"minus3");
    insert (newlist,11,"eleven");
    insert (newlist,0,"egg");
    insert (newlist,13,"eleven");
    insert (newlist,120,"Pwned");
    insert (newlist,12,"Noob");
}
    
    
    linkedlist *slist = searchbystring(newlist,"oo");

    
    deletebynumber(newlist,0,10);
    
    printlinkedlist(slist);
    free(newlist);


    
    return 0;
}

```

please help me

---

### Post by 11jmb on 2012-05-07
please use square brackets around your code tags :)

Can you tell me what commands you used to compile these files? Or if you used a makefile, post that.

---

### Post by mikewbma on 2012-05-07
gcc -c seq.c -o seq.o
gcc -c testseq.c -o testseq.o
gcc testseq.o seq.o -o test

---

### Post by cgroza on 2012-05-07
> **mikewbma said:**
> gcc -c seq.c -o seq.o
gcc -c testseq.c -o testseq.o
gcc testseq.o seq.o -o test
Try:
```

gcc seq.c testseq.c -o test

```

---

### Post by 11jmb on 2012-05-07
> **cgroza said:**
> Try:
```

gcc seq.c testseq.c -o test

```


That should give the same result.


I think the problem may be that you need to include stdio and stdlib headers in your test source file, as NULL and malloc are called inside main

---

### Post by mikewbma on 2012-05-07
Thanks actually it was cause by a faulty safe testseq.c was 0 byte.

So you can ignore the header file?

but now i have this error poped up

testseq.c: In function &#8216;main&#8217;:
testseq.c:4: warning: incompatible implicit declaration of built-in function &#8216;malloc&#8217;
testseq.c:7: error: &#8216;NULL&#8217; undeclared (first use in this function)
testseq.c:7: error: (Each undeclared identifier is reported only once
testseq.c:7: error: for each function it appears in.)
testseq.c:46: warning: incompatible implicit declaration of built-in function &#8216;free&#8217;

I though NULL means the null pointer? how can you get the undeclared error?

---

### Post by 11jmb on 2012-05-07
NULL is a member of stdio.h, include that, and you should also include stdlib.h

---

### Post by mikewbma on 2012-05-08
Should I put the include in the seq.h or testseq.c.

I how does the inheritance work in C. I though if i just include it in the seq.c it should work since we are running seq.c and testseq.c together.

So in don't call malloc and NULL in the main but create a test function instead but then I still need in the main function to call the test function. 

Does that make it unnecessary for stdio.h and stdlib.h to be included in testseq.c

---

### Post by Bachstelze on 2012-05-08
Why are you using C to implement this if you don't even know how the language works? Unless your potential employer asked you to use C specifically, in wich case you should tell them that you don't know it. What are you going to do if they give you some more advanced work to do in C?

---

### Post by Tony Flury on 2012-05-08
> **mikewbma said:**
> Should I put the include in the seq.h or testseq.c.

I how does the inheritance work in C. I though if i just include it in the seq.c it should work since we are running seq.c and testseq.c together.

Including .h files is nothing to do with inheritance. #includes  are part of the pre-processor. If you use a definition from a .h in a source code file then you should #include that .h in your source code file. Effectively all that the "#include" does is insert the content of the ".h" file into your source code before it is compiled - there is no record kept in the .o file (unless you have debug turned on)of which .c file used which .h file.

You can include systems files in your application .h files - or include them into the source code ".c" files - I have to admit i am not sure which is recommended. When I wrote C - I used to include them in both - to be certain that I had the definitions I needed.

---

