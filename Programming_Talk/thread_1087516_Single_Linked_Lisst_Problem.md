---
title: "Single Linked Lisst Problem"
date: 2009-03-05
forum: Programming Talk
---

### Post by detorresrc on 2009-03-05
Hi,
Can you help me how to fix this. here;s the error and the code
tnx

rommel@rommel-desktop:~/Testing$ g++ single_link_list.cpp
single_link_list.cpp: In function ‘int main()’:
single_link_list.cpp:19: error: expected type-specifier before ‘link’
single_link_list.cpp:19: error: cannot convert ‘int*’ to ‘link*’ in assignment
single_link_list.cpp:19: error: expected `;' before ‘link’
rommel@rommel-desktop:~/Testing$ vim single_link_list.cpp

[PHP]
#include<iostream>
#include<stdio.h>
#include<stdlib.h>

using namespace std;

struct link {
   char c;
   struct link *next;
};

int main(){
   char c;
   struct link *first = NULL;
   struct link *current=NULL;
   struct link *ptr=NULL;

   while (cin >> c ) {
     ptr = new link;
      if (ptr == NULL) {
       cout << " Insufficient memory\n";
         exit(1);
      }
      ptr->c = c;
      ptr->next = NULL;
      if (first == NULL)
         first = current = ptr;
      else
         current->next = ptr;
      current = ptr;
   }

   ptr = first;
   while (ptr != NULL) {
     cout << ptr->c;
      ptr = ptr->next;
   }
   cout << endl;
   return 0;
}

[/PHP]



error:

---

### Post by tneva82 on 2009-03-05
Not sure wether it works(how is the text inputting even supposed to be stopped?-) but atleast this way I got it to compile:

```
#include<iostream>
#include<stdio.h>
#include<stdlib.h>

using namespace std;

typedef struct link {
   char c;
   link *next;
} mylink;

int main() {
   char c;
   mylink *first;
   mylink *current;
   mylink *ptr;

   while (cin >> c ) {
     ptr = new mylink;
      if (ptr == NULL) {
       cout << " Insufficient memory\n";
         exit(1);
      }
      ptr->c = c;
      ptr->next = NULL;
      if (first == NULL)
         first = current = ptr;
      else
         current->next = ptr;
      current = ptr;
   }

   ptr = first;
   while (ptr != NULL) {
     cout << ptr->c;
      ptr = ptr->next;
   }
   cout << endl;
   return 0;
}  
```

---

### Post by detorresrc on 2009-03-05
ok ill copy your code tneva, tnx for your time. :D

---

### Post by sujoy on 2009-03-05
well since you are using C++, why not write a class for the linked list instead of using good old structs ?

---

### Post by tneva82 on 2009-03-05
> **detorresrc said:**
> ok ill copy your code tneva, tnx for your time. :D

Don't cheer yet. I added some form of break from loop(if c is 'e') and bang segmentation errors at cout << ptr->c;

Wether that's due to my modifications or is there problem with your list logic I'm not sure.

---

