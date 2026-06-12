---
title: "weird Allocation/Deallocation error  in C code"
date: 2010-06-13
forum: Programming Talk
---

### Post by Abhijit Bose on 2010-06-13
A simple code to find a convex hull after reading a file storing the input points.

A.In ubuntu 10.04 using latest gcc...
the code runs fine with free() of pop() commented out
if not commented out 
crashes at LOC B in code - gives error "*** glibc detected *** ./ConvexHull: free(): invalid next size (fast): 0x0000000001e52390 ***"

B.In windows 7 using Dev-cpp 5 running gcc mingw
crashes at LOC A in code - 
windows says "program has stopped working : checking for solution" at malloc() at the first call to push().
I found the location of error using printf() debug codes and gdb backtrace.

Code follows
focus your attention to main(), upper_Hull(),lower_Hull() and Stack functions.
rest are all cool!

[PHP]
#include <stdio.h> 
#include <stdlib.h> 
#include "QuickSort.h" 
#include "Stack.h" 
 
struct data{ 
    double x; 
    double y; 
}; 
 
struct node{ 
    ElementS data; 
    PtrToNode next; 
}; 
 
typedef struct data Point2D; 
typedef struct data Vector2D; 
 
int compare(ElementA p1, ElementA p2); 
int right_turn(Vector2D v1, Vector2D v2); 
Array init_Points(FILE *input, int size); 
void sort_Arr(Array arr, int size); 
Stack upper_Hull(Array arr,int size); 
Stack lower_Hull(Array arr,int size); 
void read_out_Hull(Stack upperHull,Stack lowerHull,FILE *output); 
void print_Stack_to_File(Stack s, FILE *output); 
 
main(){ 
    int size; 
    Array arr; 
 
    FILE *input = fopen("hullMap.txt","r"); 
    if(!input){ 
        printf("Error while opening file.\n"); 
    exit(1); 
    } 
    fscanf(input,"%d",&size); 
    arr = init_Points(input,size); 
    fclose(input); 
 
    printf("Initialization done!\n"); 
 
    FILE *output = fopen("hullPoints.txt","w"); 
    if(!output){ 
        printf("Error while creating file.\n"); 
        exit(1); 
    } 
 
    sort_Arr(arr,size); 
    printf("Sorting done!\n"); 
 
    Stack s1 = upper_Hull(arr,size); 
    printf("Upper hull calculated.\n"); 
 
    Stack s2 = lower_Hull(arr,size); 
    printf("Lower hull calculated.\n"); 
 
    read_out_Hull(s1,s2,output); 
    printf("Convex hull calculated.\n"); 
    fclose(output); 
} 
 
 
Stack upper_Hull(Array arr,int size){ 
    int i = 2; 
    Vector2D v1, v2; 
    Point2D p1, p2, p3; 
    Stack upperHull = init_s(); 
    push(arr[0],&upperHull); 
    p2 = arr[1]; 
     
    while(i<size){ 
        printf("Checking upper hull for point %d..\n",i - 1); 
        p3 =arr[i++]; 
        while(!empty_s(upperHull)){ 
            p1 = pop(&upperHull); 
            v1.x = p2.x - p1.x;     
            v1.y = p2.y - p1.y; 
            v2.x = p3.x - p2.x; 
            v2.y = p3.y - p2.y; 
            if(right_turn(v1,v2)){ 
            push(p1,&upperHull); 
                break; 
            } 
            p2 = p1; 
        } 
        push(p2,&upperHull); 
        p2 = p3; 
    } 
    push(p3,&upperHull); 
    return upperHull;     
} 
 
Stack lower_Hull(Array arr,int size){ 
    int i = size-3; 
    Vector2D v1, v2; 
    Point2D p1, p2, p3; 
    Stack lowerHull = init_s(); 
    push(arr[size-1],&lowerHull); 
    p2 = arr[size-2]; 
 
    while(i>=0){ 
        p3 =arr[i--]; 
        printf("Checking lower hull for point %d..\n",i+1); 
        while(!empty_s(lowerHull)){ 
            p1 = pop(&lowerHull); 
            v1.x = p2.x - p1.x;     
            v1.y = p2.y - p1.y; 
            v2.x = p3.x - p2.x; 
            v2.y = p3.y - p2.y; 
            if(right_turn(v1,v2)){ 
            push(p1,&lowerHull); 
                break; 
            } 
            p2 = p1; 
        } 
        push(p2,&lowerHull); 
        p2 = p3; 
    } 
    push(p3,&lowerHull); 
    return lowerHull;     
} 
 
 
Stack init_s(){ 
    return NULL; 
} 
     
int empty_s(Stack head){ 
    return head==NULL; 
} 
 
void push(ElementS data,Stack *head){ 
//LOC A
    PtrToNode target = (PtrToNode)malloc(sizeof(Node)); 
    if(!target){ 
        printf("Allocation error!\n"); 
        exit(1); 
    } 
    target->data = data;     
    target->next = *head;             
    *head = target;       
} 
 
ElementS pop(Stack *head){ 
    PtrToNode cur = *head; 
    ElementS data; 
    if(!empty_s(*head)){ 
        *head = (*head)->next; 
        data = cur->data; 
//LOC B
        free(cur); 
    } 
    return data;         
} 
         
 
Array init_Points(FILE *input,int size){ 
    Array arr = (ElementA *)malloc(sizeof(ElementA)*size); 
     
    int i; 
     
    for(i=0; i<size; i++) 
        fscanf(input,"%lf %lf",&arr[i].x,&arr[i].y); 
 
    return arr;     
} 
    
int right_turn(Vector2D v1, Vector2D v2){ 
    return (v1.x*v2.y -v2.x*v1.y >= 0)?0:1;      
} 
 
void sort_Arr(Array arr, int size){ 
    quick_sort(arr,0,size); 
} 
  
void quick_sort(Array arr,int left,int right){ 
    int i,j; 
    ElementA pivot,temp; 
    if(right-left<CUTOFF) 
        insertion_sort(arr,left,right); 
    else{    
        i=left,j=right-1;      
        pivot=set_Pivot_change(arr,left,right); 
     
        while(1){ 
            while(compare(arr[++i],pivot)==-1);//checking from after left val...assured to be less than pivot 
            while(compare(arr[--j],pivot)==1);//checking from before val left of pivot at right-1, right val 
                              //                                     assured to be greater   
                              //"trail off" condition not possible, set_Pivot_change() 
                              //eliminates possibility by ordering left,center and right ElementA 
                              //and stopping loop at elements equal to pivot 
            if(i<j) 
                SWAP(temp,arr[i],arr[j]); 
            else 
                break;        
        } 
        SWAP(temp,arr[i],arr[right-1]); 
        quick_sort(arr,left,i-1); 
        quick_sort(arr,i+1,right);      
    } 
} 
  
ElementA set_Pivot_change(Array arr,int left,int right){ 
    ElementA temp; 
    int center=(left+right)/2; 
 
    if(compare(arr[left],arr[center])==1) 
        SWAP(temp,arr[left],arr[center]); 
    if(compare(arr[center],arr[right])==1) 
        SWAP(temp,arr[center],arr[right]); 
    if(compare(arr[left],arr[center])==1)  
        SWAP(temp,arr[left],arr[center]);//arranging in order left val<=center val<=right val 
 
    SWAP(temp,arr[center],arr[right-1]);  //taking pivot out of the way 
    return arr[right-1];       //returning pivot 
} 
 
void insertion_sort(Array arr,int left,int right){ 
    int i=0,j=0; 
    ElementA temp; 
    for(i=left+1;i<=right;i++){ 
        temp=arr[i]; 
        for(j=i;j>left&&(compare(temp,arr[j-1])==-1);j--) 
            arr[j]=arr[j-1]; 
        arr[j]=temp; 
    }  
}      
 
int compare(ElementA p1,ElementA p2){ 
    if(p1.x<p2.x || (p1.x==p2.x && p1.y<p2.y)) 
        return -1; 
    else if (p1.x>p2.x || (p1.x==p2.x && p1.y>p2.y)) 
        return 1; 
    else return 0; 
} 

void read_out_Hull(Stack upperHull,Stack lowerHull,FILE *output){ 
    print_Stack_to_File(upperHull,output); 
    pop(&lowerHull); 
    Point2D top; 
    while(1){ 
        top = pop(&lowerHull); 
        if(empty_s(lowerHull)) 
            break; 
        fprintf(output,"%lf %lf\n",top.x,top.y);         
    } 
} 
 
void print_Stack_to_File(Stack s, FILE *output){ 
    if(empty_s(s)) 
        return;     
    Point2D top = pop(&s); 
    print_Stack_to_File(s,output); 
    fprintf(output,"%lf %lf\n",top.x,top.y); 
} 


[/PHP]WEIRD : PROGRAM RUNS CORRECTLY IN UBUNTU WITH FREE() COMMENTED OUT!

googled it. read faq. found nothing!
i signed up in this forum for this. please help :\

ps. error at first occurrence of push and pop only. i checked with additional printf s which i have deleted for clarity.

---

### Post by MadCow108 on 2010-06-13
you have some heap corruption error. Ubuntu by default compiles with an allocator resistant to small corruption (of by one errors etc.).
it can be controlled with the MALLOC_CHECK_ environment variable.
0 is off (normal allocator), 1 warns, 2 aborts
(disabling the runtime check is no solution it just hides the bug)

to find it use valgrind. It should be able to pinpoint the place of corruption.

Or set MALLOC_CHECK_ to 2 and use a debugger, with a little luck it aborts at the right spot.

---

### Post by Abhijit Bose on 2010-06-14
Thanks. That makes sense! But can you tell how to use valgrind, or set MALLOC_CHECK_ value? Am totally new to ubuntu!

Ps.

I missed out on the stack.h & quicksort.h.

[php]
 typedef struct data ElementS; 

#ifndef _Stack_H 

#define _Stack_H 

        struct node; 

        typedef struct node Node; 

        typedef Node *PtrToNode; 

        typedef PtrToNode Stack; 



        Stack init_s();//initialize a stack 

        int empty_s(Stack head);//check whether stack is empty 

        void push(ElementS data,Stack *head);//insert on top of stack 

        ElementS pop(Stack *head);//delete and return top of stack 

#endif 

[/php][php]
 typedef struct data ElementA; 

#ifndef CUTOFF 

#define CUTOFF 10 

#endif 



#ifndef SWAP 

#define SWAP(temp,A,B) (temp)=(A),(A)=(B),(B)=(temp) 

#endif 



#ifndef _QuickSort_H 

#define _QuickSort_H 

    typedef ElementA *Array; 

    void quick_sort(Array arr,int left,int right);       //recursive funtion to divide the array 

    ElementA set_Pivot_change(Array arr,int left,int right);          //chooses pivot, sets sentinels on two ends 

    void insertion_sort(Array arr,int left,int right);         //runs insertion sort when array size is less than CUTOFF     

#endif
[/php]

---

### Post by MadCow108 on 2010-06-14
install:
sudo apt-get install valgrind
and then compile your app with debugging info (gcc -g ...) and:
valgrind ./program-name

your problem is likely caused by invalid read/write errors.

A bug I can see is in set_Pivot_change line 210:
if(compare(arr[center],arr[right])==1)
where right == size on the first recursion level
this is one to high, the last index is size - 1.

---

### Post by Abhijit Bose on 2010-06-14
==2874== Invalid read of size 8
==2874==    at 0x40113C: set_Pivot_change (ConvexHull.c:211)
==2874==    by 0x400EDF: quick_sort (ConvexHull.c:185)
==2874==    by 0x400E7E: sort_Arr (ConvexHull.c:175)
==2874==    by 0x40086C: main (ConvexHull.c:49)
==2874==  Address 0x51b03f0 is 0 bytes after a block of size 304 alloc'd
==2874==    at 0x4C284A8: malloc (vg_replace_malloc.c:236)
==2874==    by 0x400D91: init_Points (ConvexHull.c:157)
==2874==    by 0x40080D: main (ConvexHull.c:38)


As you can see, that WAS the problem! 
Replaced quick_sort(arr,size) with quick_sort(arr,size-1) and that's it!
Thanks a lot! I do not know how to return that favor :-)

ps. If you dun mind, can you elaborate what the valgrind output posted above means. Just so that i can use it better in the future!
Thanks a lot for your time :-)

---

### Post by MadCow108 on 2010-06-14
valgrind here says there was a read (of 8 bytes data) on memory which was not explicitly allocated by your program before.
the lines under this is the stack trace leading to the error.

then follows information the distance of your read to a block of memory which was allocated by your process and where this block was allocated in your code.

the 0 bytes after... often indicate that you overrun your memory exactly by one unit.
In other cases (e.g. invalid pointers) this information may be less useful.

for more information see the valgrind manual:
[http://valgrind.org/docs/manual/manual-core.html](http://valgrind.org/docs/manual/manual-core.html)
it is a very useful program with many features, most notably the memory leak checker.

---

### Post by Abhijit Bose on 2010-06-14
thanks :)
that would be it for now!

---

