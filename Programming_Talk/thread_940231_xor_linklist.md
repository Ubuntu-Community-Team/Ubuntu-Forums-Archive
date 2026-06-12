---
title: "xor linklist"
date: 2008-10-06
forum: Programming Talk
---

### Post by adramalech on 2008-10-06
okay so know i am looking and what my seed is turns out to be my data of each node!!! so i went back through debugged like crazy and this is what i have now....

i have the list commented out at all times....the only thing it will do right now is input numbers!!

and will output the number being passed in...and then what the head is afterwards...
this is the source code revised again:
```

#include <stdio.h>
#include <stdlib.h>
#include "rndm.h"

#define MAX_NUMBERS 100

typedef struct _node{
        int data;
        unsigned long link;
} node;//end node

node *tmp, *head, *tail, *next, *prv, *cur;

void  insert(insertNum){
        printf("This is the random number passed in %d\n", insertNum);
        node *nekw = (node *)malloc(sizeof(node));
        nekw->data = insertNum;
        printf("this is the number inputed %d\n", nekw->data );
        cur = head;
        prv = NULL;
        while(cur != NULL && cur->data < insertNum){
                next = (node *)(cur->link ^ (unsigned long)prv);
                prv = cur;
                cur = next;
        }//end while loop
        if(prv == NULL){
                head = nekw;
        }//end if statement.
        else{
                nekw->link ^= (unsigned long) prv ^(unsigned long) cur;
                prv->link ^= (unsigned long) cur ^ (unsigned long) nekw;
                cur->link ^= (unsigned long) prv ^ (unsigned long) nekw;
        }//end else statement.
}//end insert.

void delete(int deleteNum){
        printf("I am in the delete function!\n");
        cur = head;
        printf("This is in cur before i start %2.1d\n", cur->data);
        prv = NULL;
        while(cur != NULL && (cur->data != deleteNum)){
                prv =(node *)(cur->link ^ (unsigned long)next);
                prv = cur;
                cur = next;
        }//end while loop
        if(cur != NULL && (cur->data == deleteNum)){
                printf("this is what was found %2.1d\n", cur->data);
                prv->link ^= (unsigned long) prv ^ (unsigned long) cur;
                next->link ^= (unsigned long) cur^ (unsigned long) next;
                free(cur);
        }//end if statement.
}//end delete.

 void list(int option){
        int cnt = 1;
        if(option == 1){
                cur = head;
                prv = NULL;
                printf("This is the list in acending order: \n");
                while(cnt <= MAX_NUMBERS){
                        printf("%3.1d", cur->data);
                        cnt++;
                        if(cnt % 10 == 0){
                                printf("\n");
                        }//end if statement
                        prv =(node *)(cur->link^(unsigned long)next);
                        prv = cur;
                        cur = next;
                }//end while loop
        }//end if
        else if(option == 2){
                cur = tail;
                next = NULL;
                printf("This is the list in decending order: \n");
                if(cnt % 10 == 0){
                        printf("\n");
                }//end if statement.
                while (cnt <= MAX_NUMBERS){
                        printf("%3.1d", prv->data);
                        cnt++;
                        if(cnt % 10 == 0){
                                printf("\n");
                        }//end if statement.
                        prv = (node *)(cur->link^(unsigned long) prv);
                        next = cur;
                        cur = prv;
                }//end while loop.
        }//end else if
}//end list.

int main(){
        head = NULL;
        tail = head;
        long inputZ;
        int num, option,cnt, beginning, end;
        int numDelete;
        printf("Please enter the seed: ");
        scanf("%l\n", &inputZ);
        init_seed(inputZ);

        printf("Please enter the range: ");
        scanf("%d%d\n", &beginning, &end);
        set_range(beginning, end);

        for(cnt=0; cnt <= MAX_NUMBERS; cnt++){
                insert(rndm());
        }//end for loop.
#if 0
        printf("For ascending press 1, or 2 for decending: ");
        scanf("%d\n", &num);
        list(num);

        numDelete = 7004;
        delete(numDelete);

        printf("For ascending press 1, or 2 for decending: ");
        scanf("%d\n", &num);
        list(num);
#endif
        return 0;
}//end main.


```

here is my output:
```

> gcc linkList.c rndm.o
>ls
a.out*  lab1/  lab2/  linkList.c  rndm.h  rndm.o
> a.out
Please enter the seed: 12345
Please enter the range: 1 9999
This is the random number passed in 3995
this is the number inputed 3995
This is the random number passed in 10463
this is the number inputed 10463
Segmentation fault
>


```
i don't understand what is going wrong....the only time the input should really brake down is the first one inserted and if a number inputed into a list of nodes is less than the first node then i have a problem....otherwise i should just be inserting nodes that have different numbers that are less than the next one!! but it seems to break down before i even insert a number!!!

---

### Post by dwhitney67 on 2008-10-06
Really bizarre... you are XORing addresses!  It is no wonder that your program is crashing.  It is highly probable that the addresses you yield when performing the XOR are outside the program space of your running application.  Setting your pointers to an address outside is not really the problem, but it will be an issue when you try to de-reference the address.  For example, this will not work unless you happen to be extremely lucky:
[PHP]
while(cur != NULL && cur->data < insertNum){
    next = (node *)(cur->link ^ (unsigned long)prv);
    prv = cur;
    cur = next;    // Ouch!  Where does cur point to now???
}
[/PHP]

What are you trying to accomplish?  Are you merely trying to create a link list with sorted numbered entries?  Something like:  5 -> 6 -> 8 -> 1023 -> 10001 -> 65343 -> NULL

---

### Post by adramalech on 2008-10-06
well it is an assignment for class....it will work but i need to have 3 cases i look for in the insert and delete...

if it isn't the first thing into the list do this....or if it is the first thing do this....or if it is less than the first thing in the list do this...

besides that it is really straight forward...

cur = next; is incrementing the current pointer to the next pointer...
> next = (node *)(cur->link ^ (unsigned long)prv);


as long as what you are accessing is actually in the list then you are good...my problem right now is how i evaulate the 3 cases for input...for if it is the lesser of values, if it is the first in the list, or if it is just another number that is being attached somewhere...

i am probably going to have to draw it out on paper again...my problem if anybody can tell is that somehow i am erroring on these lines with segmentation errors:

cur = head;
prv = NULL;

these are from the insert function...my problem is that if i comment both of them out using \\\ then they will still error so i don't know if it just me or if i should think if these are already null and that writing over something that is already set isn't correct??

maybe i should put these into another conditional evaluation to make sure that these aren't null before i start or else i won't be able to do much...

---

### Post by dwhitney67 on 2008-10-07
If you are doing a sorted linked list, then it is quite simple.  First I recommend that you define a Node structure.  For instance:
[php]
struct Node
{
    int           value;
    struct Node * next;
};
[/php]

Then when you insert a value, and there has to be a first one, check the pointer to the head of the list.  Initially head should point to zero.
[php]
struct Node * head = NULL;     // initial condition

void insert( int number )
{
  if ( head == NULL )
  {
    // define head for the first time
    //
    head = (struct Node *) malloc( sizeof(struct Node) );

    head->value = number;   // assign the number
    head->next  = NULL;     // next Node is NULL
  }
  else
  {
    // Search for the Node that has a value that is greater
    // than the number being inserted.  When this Node is found,
    // insert a new Node (with the number) just before it.
    //
    // For example, to insert 10 into this list:
    //    1 -> 2 -> 3 -> 20 -> NULL
    //
    // The list becomes:
    //    1 -> 2 -> 3 -> 10 -> 20 -> NULL


    // Since this is a class exercise, I will leave the implementation
    // of this section to you.  But in essence you need to
    // iterate through your list and if you find a Node with a
    // value greater than your number, then stop and insert a
    // new Node.  Else if the end of the list is reached, then
    // just insert the new Node at the very end.
  }
}
[/php]

---

### Post by Quikee on 2008-10-07
> **dwhitney67 said:**
> Really bizarre... you are XORing addresses!

Of course he is xor-ing addresses, this is how you can make a bi-directional linked list with the same memory requirements as a uni-directional linked list. 

stored number = previous address ^ next address

previous address ^ stored number = next address
next address ^ stored number = previous address

---

### Post by mike_g on 2008-10-07
> 
i am probably going to have to draw it out on paper again...my problem if anybody can tell is that somehow i am erroring on these lines with segmentation errors:

cur = head;
prv = NULL;

The assignment itself should not cause a segfault, so it should be something else in you insert function. First, your insertNum variable does not seem to be declared as a int. Also if you are inserting at the end of the list it looks as if you will break the list. As no node will link to newk.

```
[COLOR="RED"]void  insert(insertNum){[/COLOR]
        printf("This is the random number passed in %d\n", insertNum);
        node *nekw = (node *)malloc(sizeof(node));
        [COLOR="RED"]nekw->data = insertNum;[/COLOR]
        printf("this is the number inputed %d\n", nekw->data );
        cur = head;
        prv = NULL;
        while(cur != NULL && cur->data < insertNum){
                next = (node *)(cur->link ^ (unsigned long)prv);
                prv = cur;
                cur = next;
        }//end while loop
[COLOR="RED"]        if(prv == NULL){
                head = nekw;
        }//end if statement.[/COLOR]
        else{
                nekw->link ^= (unsigned long) prv ^(unsigned long) cur;
                prv->link ^= (unsigned long) cur ^ (unsigned long) nekw;
                cur->link ^= (unsigned long) prv ^ (unsigned long) nekw;
        }//end else statement.
}//end insert.
```
Oh and the address XORing thing is a nice little trick. I hadent heard of that before.

---

### Post by dwhitney67 on 2008-10-07
> **mike_g said:**
> ...
Oh and the address XORing thing is a nice little trick. I hadent heard of that before.

I hadn't either; it was news to me.  I guess if you spend most of your time developing desktop applications, it is not worth pursuing this approach.  I read the Wiki page concerning the [XOR linked list]("http://en.wikipedia.org/wiki/XOR_linked_list").

---

### Post by adramalech on 2008-10-07
okay well i fixed the parameter variable not being an int for the insert function...but it did the same thing because C will automatically place it as an integer if you don't say it to something else...

furthermore, the if(prv == NULL){ cur = head;}  is for the purpose of setting the first time a node is inserted when the list is blank it will go to head...but i forgot to put the 3 lines below it in the if statement!!! so it wouldn't increment the link!

the newk->data = insertNum is setting the new node i created with a size of the structure of the definition of a node with it's data field equaling the integer passed in!!!

---

### Post by adramalech on 2008-10-08
okay so i think i got the insert function down....but it is inserting memory allocations!!! because those numbers aren't even close to being in the 1 to 9999 range!

i think i might be passing by memory location??? i thought C passes by value!!!

it goes through my first case every time doesn't even try going through the others!!!

here is my ouput:

```

> cd CSC60
> gcc linkList.c rndm.o
> a.out
Please enter the seed: 123456
Please enter the range: 1 9999
this is the number inserted 39931
this is the data of head 39931
this is the number inserted 104625
this is the data of head 104625
this is the number inserted 36233
this is the data of head 36233
this is the number inserted 44149
this is the data of head 44149
this is the number inserted 7891
this is the data of head 7891
this is the number inserted 122210
this is the data of head 122210
this is the number inserted 35377
this is the data of head 35377
this is the number inserted 101254
this is the data of head 101254
this is the number inserted 38017
this is the data of head 38017
this is the number inserted 29102
this is the data of head 29102
this is the number inserted 77217
this is the data of head 77217
this is the number inserted 114125
this is the data of head 114125
this is the number inserted 78533
this is the data of head 78533
this is the number inserted 7201
this is the data of head 7201
this is the number inserted 118236
this is the data of head 118236
this is the number inserted 31285
this is the data of head 31285
this is the number inserted 98209
this is the data of head 98209
this is the number inserted 102561
this is the data of head 102561
this is the number inserted 27972
this is the data of head 27972
this is the number inserted 94344
this is the data of head 94344
this is the number inserted 85547
this is the data of head 85547
this is the number inserted 116748
this is the data of head 116748
this is the number inserted 88288
this is the data of head 88288
this is the number inserted 20224
this is the data of head 20224
this is the number inserted 116579
this is the data of head 116579
this is the number inserted 79398
this is the data of head 79398
this is the number inserted 107279
this is the data of head 107279
this is the number inserted 67179
this is the data of head 67179
this is the number inserted 48472
this is the data of head 48472
this is the number inserted 71278
this is the data of head 71278
this is the number inserted 45211
this is the data of head 45211
this is the number inserted 76139
this is the data of head 76139
this is the number inserted 31341
this is the data of head 31341
this is the number inserted 53153
this is the data of head 53153
this is the number inserted 112910
this is the data of head 112910
this is the number inserted 32772
this is the data of head 32772
this is the number inserted 34117
this is the data of head 34117
this is the number inserted 45641
this is the data of head 45641
this is the number inserted 29232
this is the data of head 29232
this is the number inserted 28596
this is the data of head 28596
this is the number inserted 83326
this is the data of head 83326
this is the number inserted 72950
this is the data of head 72950
this is the number inserted 12574
this is the data of head 12574
this is the number inserted 58169
this is the data of head 58169
this is the number inserted 91872
this is the data of head 91872
this is the number inserted 15916
this is the data of head 15916
this is the number inserted 62159
this is the data of head 62159
this is the number inserted 3045
this is the data of head 3045
this is the number inserted 28327
this is the data of head 28327
this is the number inserted 6043
this is the data of head 6043
this is the number inserted 51752
this is the data of head 51752
this is the number inserted 25053
this is the data of head 25053
this is the number inserted 50715
this is the data of head 50715
this is the number inserted 119898
this is the data of head 119898
this is the number inserted 67846
this is the data of head 67846
this is the number inserted 20697
this is the data of head 20697
this is the number inserted 42638
this is the data of head 42638
this is the number inserted 39936
this is the data of head 39936
this is the number inserted 66748
this is the data of head 66748
this is the number inserted 89742
this is the data of head 89742
this is the number inserted 9457
this is the data of head 9457
this is the number inserted 20340
this is the data of head 20340
this is the number inserted 88505
this is the data of head 88505
this is the number inserted 88967
this is the data of head 88967
this is the number inserted 75168
this is the data of head 75168
this is the number inserted 4294
this is the data of head 4294
this is the number inserted 24406
this is the data of head 24406
this is the number inserted 38265
this is the data of head 38265
this is the number inserted 10733
this is the data of head 10733
this is the number inserted 106617
this is the data of head 106617
this is the number inserted 60492
this is the data of head 60492
this is the number inserted 5448
this is the data of head 5448
this is the number inserted 49862
this is the data of head 49862
this is the number inserted 107570
this is the data of head 107570
this is the number inserted 25043
this is the data of head 25043
this is the number inserted 7732
this is the data of head 7732
this is the number inserted 33556
this is the data of head 33556
this is the number inserted 120585
this is the data of head 120585
this is the number inserted 11842
this is the data of head 11842
this is the number inserted 106301
this is the data of head 106301
this is the number inserted 51116
this is the data of head 51116
this is the number inserted 78403
this is the data of head 78403
this is the number inserted 60591
this is the data of head 60591
this is the number inserted 58978
this is the data of head 58978
this is the number inserted 119318
this is the data of head 119318
this is the number inserted 80126
this is the data of head 80126
this is the number inserted 6962
this is the data of head 6962
this is the number inserted 63993
this is the data of head 63993
this is the number inserted 79383
this is the data of head 79383
this is the number inserted 110669
this is the data of head 110669
this is the number inserted 19092
this is the data of head 19092
this is the number inserted 110373
this is the data of head 110373
this is the number inserted 95561
this is the data of head 95561
this is the number inserted 38271
this is the data of head 38271
this is the number inserted 98800
this is the data of head 98800
this is the number inserted 33324
this is the data of head 33324
this is the number inserted 49864
this is the data of head 49864
this is the number inserted 10661
this is the data of head 10661
this is the number inserted 8895
this is the data of head 8895
this is the number inserted 69536
this is the data of head 69536
this is the number inserted 27843
this is the data of head 27843
>

```

here is my source code... i think i only changed up some of the insert method!!

```

#include <stdio.h>
#include <stdlib.h>
#include "rndm.h"

#define MAX_NUMBERS 100

typedef struct _node{
        int data;
        unsigned long link;
} node;//end node

node *tmp, *head, *tail, *next, *prv, *cur;

void  insert(int insertNum){
        printf("this is the number inserted %d\n", insertNum);
        node *nekw = (node *)malloc(sizeof(node));
        nekw->data = insertNum;
        cur = head;
        prv = NULL;
        if(cur == NULL){
                cur = nekw;
                next = tail;
                printf("this is the data of head %d\n", cur->data);
        }//end if statement.

        else if((cur->data > nekw->data)&& (cur !=NULL)){
                tmp = cur;
                nekw->link = tmp->link;
                cur = nekw;
                tmp->link = cur->link ^ next->link;
                prv->link ^= (unsigned long) prv ^ (unsigned long) tmp;
                cur->link ^= (unsigned long) prv ^ (unsigned long) next;
                tmp = NULL;
                printf("this is the data of cur %d\n", &cur->data);
        }//end else if statement
        else{
                while(cur != NULL && (cur->data < insertNum)){
                        next = (node *)(cur->link ^ (unsigned long)prv);
                        prv = cur;
                        cur = next;
                }//end while loop

                nekw->link ^= (unsigned long) prv ^(unsigned long) cur;
                prv->link ^= (unsigned long) cur ^ (unsigned long) nekw;
                cur->link ^= (unsigned long) prv ^ (unsigned long) nekw;
        }//end else statement
}//end insert.

void delete(int deleteNum){
        cur = head;
        prv = NULL;
        while(cur != NULL && (cur->data != deleteNum)){
                prv =(node *)(cur->link ^ (unsigned long)next);
                prv = cur;
                cur = next;
        }//end while loop
        if(cur != NULL && (cur->data == deleteNum)){
                prv->link ^= (unsigned long) prv ^ (unsigned long) cur;
                next->link ^= (unsigned long) cur^ (unsigned long) next;
                free(cur);
        }//end if statement.
}//end delete.

 void list(int option){
        int cnt = 1;
        if(option == 1){
                cur = head;
                prv = NULL;
                printf("This is the list in acending order: \n");
                while(cnt <= MAX_NUMBERS){
                        printf("%3.1d", cur->data);
                        cnt++;
                        if(cnt % 10 == 0){
                                printf("\n");
                        }//end if statement
                        prv =(node *)(cur->link^(unsigned long)next);
                        prv = cur;
                        cur = next;
                }//end while loop
        }//end if
        else if(option == 2){
                cur = tail;
                next = NULL;
                printf("This is the list in decending order: \n");
                if(cnt % 10 == 0){
                        printf("\n");
                }//end if statement.
                while (cnt <= MAX_NUMBERS){
                        printf("%3.1d", prv->data);
                        cnt++;
                        if(cnt % 10 == 0){
                                printf("\n");
                        }//end if statement.
                        prv = (node *)(cur->link^(unsigned long) prv);
                        next = cur;
                        cur = prv;
                }//end while loop.
        }//end else if
}//end list.

int main(){
        head = NULL;
        tail = head;
        long inputZ;
        int cnt, beginning, end, num, numDelete;

        printf("Please enter the seed: ");
        scanf("%l\n", &inputZ);
        init_seed(inputZ);

        printf("Please enter the range: ");
        scanf("%d%d\n", &beginning, &end);
        set_range(beginning, end);

        for(cnt=0; cnt <= MAX_NUMBERS; cnt++){
                insert(rndm());
        }//end for loop.
#if 0
        printf("For ascending press 1, or 2 for decending: ");
        scanf("%d\n", &num);
        list(num);

        numDelete = 7004;
        delete(numDelete);

        printf("For ascending press 1, or 2 for decending: ");
        scanf("%d\n", &num);
        list(num);
#endif
        return 0;
}//end main.


```

---

### Post by dwhitney67 on 2008-10-08
It appears that you are passing the insertNum correctly.

If I had to guess, and that is all I can do now, I would say the problem lies within your rndm code.  Can you post that please?

Btw...

1.  You are iterating 101 times in your for-loop where you are inserting numbers.

2.  *nix provides a rand() C-library function that can be used to obtain random numbers.  The random number generator can be seeded with srand().  For example:
[php]
#include <stdlib.h>
#include <time.h>

int main()
{
  srand( time(0) );

  ...

  for ( int cnt = 0; cnt < MAX_NUMBERS; ++cnt )
  {
    insert( rand() % 9999 );
  }

  ...
}
[/php]

---

### Post by adramalech on 2008-10-08
ohh i figured out why my code was only evaluating for the first condition because i never set head equal to current at the end so the head will always be null!!!

furthermore, from the teacher i got the rndm.h file and a rndm.0 file....it has nothing to do with his code...because the same rndm.o and rndm.h my classmate uses gets him to get numbers...i think it has something to do with how i access the pointers or something causing it to print out memory locations!!!

---

### Post by dwhitney67 on 2008-10-08
This code looks fine:
[php]
void  insert(int insertNum){
        printf("this is the number inserted %d\n", insertNum);
        ...
}
[/php]

Thus if you are expecting (insertNum) values between 1 and 9999, then I once again suspect that there is a problem with rndm().

If memory serve me right, you are calling insert() such as:
[php]
        insert( rndm() );
[/php]

Maybe I am misinterpreting the rationale for setting the range of 1 and 9999?

---

### Post by adramalech on 2008-10-08
yes i am:

>   insert(rndm());


---

### Post by mike_g on 2008-10-08
Well theres a problem with rndm somewhere as its not giving you the correct results.

Have you tried compiling with -Wall? Your code throws up a load of warnings that you should try and fix.

I had a play around with your code a fixed a couple of things. Your list is still borked as it segfaults when you set the head. I'll leave that to you to have a go at fixing as I cant be doing all your homework for you ;)

```
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

#define MAX_NUMBERS 100

typedef struct _node{
        int data;
        unsigned long link;
} node;

node *tmp, *head, *tail, *next, *prv, *cur;

[COLOR="RED"]int rndm() /* Test function seems to work */
{
	return (rand()%9999)+1; 
}[/COLOR]

void  insert(int insertNum){
        printf("this is the number inserted %d\n", insertNum);
        node *nekw = (node *)malloc(sizeof(node));
        nekw->data = insertNum;
        [COLOR="RED"]cur = head; // <-- cur is set head here[/COLOR]
        prv = NULL;
		printf("%p\n", nekw); 
        if(cur == NULL){
				[COLOR="RED"]/* head = nekw; // <- so cur will always be NULL until you set the head */ [/COLOR] 
                cur = nekw;
                next = tail;
                printf("this is the data of head %d\n", cur->data);
        }
        else if((cur->data > nekw->data)[COLOR="RED"]/* redundant: && (cur !=NULL)*/[/COLOR]){
                tmp = cur;
                nekw->link = tmp->link;
                cur = nekw;
                tmp->link = cur->link ^ next->link;
                prv->link ^= (unsigned long) prv ^ (unsigned long) tmp;
                cur->link ^= (unsigned long) prv ^ (unsigned long) next;
                tmp = NULL;
                printf("this is the data of cur %d\n", [COLOR="RED"]/* dont want address of pointer: &*/[/COLOR]cur->data);
        }
        else{
                while(cur != NULL && (cur->data < insertNum)){
                        next = (node *)(cur->link ^ (unsigned long)prv);
                        prv = cur;
                        cur = next;
                }
                nekw->link ^= (unsigned long) prv ^(unsigned long) cur;
                prv->link ^= (unsigned long) cur ^ (unsigned long) nekw;
                cur->link ^= (unsigned long) prv ^ (unsigned long) nekw;
        }
}

int main(){
        head = NULL;
        tail = head;
        int cnt;
		srand(time(NULL));
        for(cnt=0; cnt <= MAX_NUMBERS; cnt++)
                insert(rndm());
        return 0;
}
```

---

### Post by adramalech on 2008-10-08
okay i know that i am using cur->data but i don't understand how to make it into the value of data at current node?? would i use like a & as if in the scanf for dereferencing pointers??

furthermore, what did you mean by redundant cur != null?? doesn't that mean i might want to look at my evaluations and make sure they aren't saying the same thing??

---

### Post by mike_g on 2008-10-08
> okay i know that i am using cur->data but i don't understand how to make it into the value of data at current node?? would i use like a & as if in the scanf for dereferencing pointers??
I'm not sure what you mean here. 'cur' is a pointer. 'data' is a variable you can set the variable by doing cur->data = 10 or something.

> furthermore, what did you mean by redundant cur != null?? doesn't that mean i might want to look at my evaluations and make sure they aren't saying the same thing??
Yeah, pretty much. in this code:
```
if(x == NULL)
  
else if(x != NULL)
```
There would be no need for the second evaluation, because you already know that x is not going to be NULL.

---

### Post by adramalech on 2008-10-11
okay so after a long night and no sleep i figured it all out...but i still have a problem with listing the numbers after i insert it...

```

#include <stdio.h>
#include <stdlib.h>

#define MAX_NUMBERS 100

typedef struct _node{
        int data;
        unsigned long link;
} node;//end node

node *head, *tail;

void  insert(int insertNum){
        node *nekw, *next, *prv, *cur;
        nekw = malloc(sizeof(node));
        cur = head;
        prv = NULL;
        nekw->data = insertNum;

        while((cur != NULL) && (cur->data < nekw->data)){
                next = (node *)(cur->link^(unsigned long)prv);
                prv = cur;
                cur = next;
        }//end while loop

        if(next == NULL){
                next = nekw;
                tail = next;
                printf("this is the next thing in the list %d\n", tail->data);
        }//end if statement
        else if(((cur != NULL) && (next != NULL))&& (cur->data > nekw->data)){
                nekw->link = (unsigned long) prv ^ (unsigned long)cur;
                next = (node *)(cur->link ^ (unsigned long)prv);
                cur->link = ((unsigned long)nekw ^ (unsigned long)next);
                head = nekw;
        }//end else if statement
        else{
                cur = nekw;
                head = cur;
                printf("this is head %d\n", head->data);
        }//end else statement.
}//end insert.

void list(){
        int cnt = 1;
        node *cur, *prv, *next;
        cur = head;
        prv = NULL;
        printf("This is the list in ascending order: \n");
      [COLOR="Red"]  printf("%2.1d", cur->data);//this will never print anything!!! even though cur->data = 1!!
[/COLOR]
        while((cur != NULL) && (++cnt < MAX_NUMBERS)){
               [COLOR="Red"] next = (node *)(cur->link^(unsigned long)prv);//this will always be null[/COLOR]
                prv = cur, cur = next;
               [COLOR="Red"] printf("%2.1d", cur->data);//this is where it will error[/COLOR]
                if(cnt % 10 == 0){
                        printf("\n");
                }//end if statement.
        }//end while loop
}//end list.

int main(){
        head = NULL;
        tail = head;
        int cnt;

        for(cnt = 1; cnt < MAX_NUMBERS; cnt++){
                insert(cnt);
        }//end for loop.

        list();
     
        return 0;
}//end main.

```

here is my ouput:  it won't go to the next thing in the list...next thing will always be null!!!  I checked my insert method over and over again...i found that i never set head the last time...so i made sure that tail and head are set perfect after every case...and still get the error...
```

This is the list in ascending order:
Segmentation fault

```

---

### Post by dwhitney67 on 2008-10-12
> **adramalech said:**
> 
...
I checked my insert method over and over again...i found that i never set head the last time...so i made sure that tail and head are set perfect after every case...and still get the error...
...

Apparently you did not check the insert() function sufficiently to ensure that it works properly.  It had its share of bugs in it.  I have rewritten your code such that it works.

I used the GNU99 standards for the code; not the 20 year old GNU89 standards that most people seem to use.  To compile the following code, use:
```
gcc -Wall -pedantic -std=gnu99 xor_list.c -o xor_list
```

[php]
#include <stdio.h>
#include <stdlib.h>
#include <time.h>


typedef enum { ASCENDING, DESCENDING } ListOrdering;


typedef struct Node
{
  int           data;
  unsigned long link;
} Node;


// global variable(s)
//
Node * head = 0;
Node * tail = 0;


void insert( int insertNum )
{
  Node * prev = 0;
  Node * cur  = head;
  Node * node = malloc( sizeof(Node) );

  node->data = insertNum;

  while ( (cur != 0) && (cur->data < node->data) )
  {
    Node * next = (Node *) (cur->link ^ (unsigned long)prev);
    prev = cur;
    cur  = next;
  }

  if ( head == 0 )
  {
    head = node;
    head->link = 0;
  }
  else if ( cur == 0 )
  {
    prev->link = prev->link ^ (unsigned long)node;
    node->link = (unsigned long)prev ^ (unsigned long)cur;

    tail = node;
  }
  else if ( cur->data >= node->data )
  {
    // If prev is zero (null), then our node becomes the new head of the list
    if ( prev == 0 )
    {
      head = node;
    }
    else
    {
      // else adjust the link of prev
      Node * prevPrev = (Node *) (prev->link ^ (unsigned long)cur);

      prev->link = (unsigned long)prevPrev ^ (unsigned long)node;
    }

    node->link = (unsigned long)prev ^ (unsigned long)cur;

    Node * next = (Node *) ((unsigned long)prev ^ cur->link);

    cur->link = (unsigned long)node ^ (unsigned long)next;
  }
}


void list( ListOrdering ordering )
{
  Node * cur  = (ordering == ASCENDING ? head : tail);
  Node * prev = 0;

  unsigned int cnt = 1;

  while ( cur != 0 )
  {
    printf( "%2.1d ", cur->data );

    Node * next = (Node *) (cur->link ^ (unsigned long)prev);

    prev = cur;
    cur  = next;

    if ( (++cnt % 10) == 0 ) printf( "\n" );
  }
  printf( "\n" );
}


int main( int argc, char **argv )
{
  const unsigned int MAX_NUMBERS = (argc > 1 ? atoi(argv[1]) : 5 );

  srand( time(0) );

  for ( unsigned int i = 0; i < MAX_NUMBERS; ++i )
  {
    insert( rand() % 100 );
  }

  list( ASCENDING );
  list( DESCENDING );
     
  return 0;
}
[/php]

P.S.  If you do not want your list to hold duplicate values, then remove the '=' sign from the following statement:
[php]  else if ( cur->data >= node->data ) [/php]

---

