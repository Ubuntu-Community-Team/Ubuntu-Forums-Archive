---
title: "C and pointers"
date: 2009-04-04
forum: Programming Talk
---

### Post by StOoZ on 2009-04-04
Hi,
I just wonder , why I get weird characters when using 'studentReturn' , and good output when using the 'first' pointer.

the problem is in the lines : 

[PHP]       studentReturn.first = (List*) malloc ( sizeof(List) );
       studentReturn.first->head = first;
       studentReturn.grade = ConvArrayToDec( grade , counter );[/PHP]


The Code is :
[PHP]#include<stdio.h>
#include<stdlib.h>
#include<ctype.h>
#include<math.h>

/************* structs***********************/
typedef struct list_node {

    char* dataPtr;
    struct list_node* next;

}ListNode;

typedef struct list {

    ListNode* head;
    ListNode* tail;

}List;

typedef struct student {

    List* first;
    int grade;

} Student;


/********************************************/

/* just to ease the creation of the linked list.           */
/* this funtion creates a linked list from the stdin stream*/
List createScrabledList();
/* Prints the contents of a List */
void PrintList( List );
/* unscrable the list */
Student unScrable( List );
/* converts array of digits to a decimal number */
int ConvArrayToDec( int* , int );

void main() {

    List lst;
    Student std;

    lst = createScrabledList();
    printf("the scrambled list is :\n");
    PrintList( lst );
    printf("\n");
    fflush(stdout);
    std = unScrable( lst );

    while ( std.first->head != NULL ) {

        printf("%s" , std.first->head->dataPtr );
        std.first->head = std.first->head->next;

    }
    printf("\nthe grade is %d", std.grade );

}



List createScrabledList() {

    List* pList = (List*) malloc( sizeof(List) );
    ListNode* node = NULL;

    int ch;

    while (  ( ch = getchar() ) != '\n' ) {

        if ( NULL == node ) {
            node = (ListNode*) malloc( sizeof(ListNode) );
            node->dataPtr = (char*) malloc( sizeof(char) );
            node->dataPtr[0] = ch;
            pList->head = node;
        } else {
            node->next = (ListNode*) malloc( sizeof(ListNode) );
            node = node->next;
            node->dataPtr = (char*) malloc( sizeof(char) );
            node->dataPtr[0] = ch;

        }
    }

    node->next = NULL;

    return *pList;

}


void PrintList( List lst ) {

    while ( lst.head != NULL ) {

        printf("%s", lst.head->dataPtr );
        lst.head = lst.head->next;

    }

}

int ConvArrayToDec( int* arr , int sz ) {
    
    int num = 0 , i;
    int numSqrt;
    numSqrt = pow( 10 , sz - 1 );
    
    for ( i = 0 ; i < sz ; i++ ) {
        
        num += ( arr[i] * numSqrt );
        numSqrt /= 10;
        
    }
    return num;
}


Student unScrable( List lst ) {

    int grade[3] = {-1,-1,-1}; // assuming the avg can be 100.
    int counter = 0;
    ListNode* pTemp = NULL;
    ListNode* pToFreeNode = NULL;
    ListNode* first = lst.head;
    Student studentReturn = { NULL , 0 };

    

    while ( lst.head != NULL ) {

       if ( isdigit(lst.head->dataPtr[0]) != 0 ) {

            pTemp = lst.head;
            while ( isdigit(pTemp->dataPtr[0]) != 0 ) {

                pToFreeNode = pTemp;
                grade[counter++] = (pTemp->dataPtr[0] - '0') ;
                pTemp = pTemp->next;
                free(pToFreeNode); // erasing the no-longer needed node.
                  
            }
            *(lst.head) = *pTemp;
        }

      lst.head = lst.head->next;
    }

    // for debugging
/*
    while ( first != NULL ) {

        printf("%s" , first->dataPtr );
        first = first->next;


    }
*/
       studentReturn.first = (List*) malloc ( sizeof(List) );
       studentReturn.first->head = first;
       studentReturn.grade = ConvArrayToDec( grade , counter );
    return studentReturn;
}[/PHP]


when I use the commented code (under debugging) , all seems fine , the numbers are omitted and only the text appears , when I use it with the studentReturn structure , it doesnt work well , weired characters are displayed instead of the numbers that should not be displayed.

thanks!

---

### Post by Arndt on 2009-04-04
> **StOoZ said:**
> Hi,
I just wonder , why I get weird characters when using 'studentReturn' , and good output when using the 'first' pointer.

the problem is in the lines : 

[PHP]       studentReturn.first = (List*) malloc ( sizeof(List) );
       studentReturn.first->head = first;
       studentReturn.grade = ConvArrayToDec( grade , counter );[/PHP]


when I use the commented code (under debugging) , all seems fine , the numbers are omitted and only the text appears , when I use it with the studentReturn structure , it doesnt work well , weired characters are displayed instead of the numbers that should not be displayed.

thanks!

I haven't studied the code closely, and what I'm remarking on may not be the cause of the bug, but I find it odd to pass a whole structure by value, in for example the unScrable function:

```
Student unScrable( List lst ) { 
```

I would use a declaration like this:

```
Student *unScrable( List *lst ) { 
```

(and change the body and callers accordingly, of course).

---

### Post by StOoZ on 2009-04-04
I know , but this is what I was asked to do according to the question's rules.

this is not the cause of the problem.
im still trying to figure out what can cause this problem.

thanks anyway.

---

### Post by nvteighen on 2009-04-04
It segfaults for me at line 140.

I really don't understand what the hell (excuse me) are you trying to accomplish. Could you please explain us what your program is meant to do?

---

### Post by Can+~ on 2009-04-04
There are many weird things about this code, for instance


```
List[COLOR="DarkRed"]*****[/COLOR] createScrabledList() {

    List* pList = (List*) malloc( sizeof(List) );
    ListNode* node = NULL;

    int ch;

    while (  ( ch = getchar() ) != '\n' ) {

        if ( NULL == node ) {
            node = (ListNode*) malloc( sizeof(ListNode) );
[B]            node->dataPtr = (char*) malloc( sizeof(char) );
            node->dataPtr[0] = ch;[/B]
            pList->head = node;
        } else {
            node->next = (ListNode*) malloc( sizeof(ListNode) );
            node = node->next;
[B]            node->dataPtr = (char*) malloc( sizeof(char) );
            node->dataPtr[0] = ch;[/B]

        }
    }

    node->next = NULL;
    [COLOR="DarkRed"]**plist->tail = node;**[/COLOR]

    return [COLOR="SeaGreen"]*[/COLOR]pList;

}
```

Why are you malloc'ing a character? You could use a plain [FONT="Courier New"][COLOR=#1E90FF]**char**[/COLOR][/FONT] and stored the value there. (In bold)

You never updated the [FONT="Courier New"]*tail[/FONT] of the base list (Added on red).

And the function is returning a [FONT="Courier New"]list*[/FONT] instead of a [FONT="Courier New"]list[/FONT] (Added on red) (Deleted on Green).

Function unScrabble and ConvArrayToDec are really hard to get what's going in there without any comments (and without any clear objective).

---

### Post by lloyd_b on 2009-04-04
Another point that is probably part of the problem:```
void PrintList( List lst ) {

    while ( lst.head != NULL ) {

        **printf("%s", lst.head->dataPtr );**
        lst.head = lst.head->next;

    }

}
```lst.head->dataPtr points to a single character, but the "%s" format expects a zero terminated character string.

Lloyd B.

---

### Post by majamba on 2009-04-04
just use cpp and classes

unless this is c program required by your instructor i wondering why are you returning a value structure just passed as a pointer and change it.

not really familar with c,  i have to look your code and see

[http://www.ehow.com/how_2056292_create-linked-list-c.html](http://www.ehow.com/how_2056292_create-linked-list-c.html)

---

### Post by nvteighen on 2009-04-05
> **majamba said:**
> just use cpp and classes

unless this is c program required by your instructor i wondering why are you returning a value structure just passed as a pointer and change it.

not really familar with c,  i have to look your code and see

[http://www.ehow.com/how_2056292_create-linked-list-c.html](http://www.ehow.com/how_2056292_create-linked-list-c.html)
Not necessarily: you can use C for OOP... the issue is that the program doesn't make any sense.

---

