---
title: "programming help!!!"
date: 2010-05-15
forum: Programming Talk
---

### Post by pirlo89 on 2010-05-15
hi,

i have a problem with a code that i wrote for an assignment. if it is possible that you guys could help me then its great. otherwise, please delete this thread admins.

basically the most annoying problem is with the sort function. it takes a link list and it sorts it out by using the "insertion sort" method. 

```


#include <iostream>
using namespace std;

// structure for the link list
struct Node {
    char data;
    Node* next;
    Node(char d, Node* n);
};

Node::Node(char d, Node* n)
{
    data = d;
    next = n;
}

// the function that builds the link list
Node* build(char* p)
{
    if((*p) == 0)
        return NULL;
    else
        return new Node((*p), build(p+1));
}


//the function that prints the link list
void print(Node* p)
{
    cout<<'<';
    while(p != NULL)
    {
        cout<< p->data;
        p = p->next;
        if(p != NULL)
            cout<<'-';
    }
    cout<<'>';
}


// the function that deletes the link list
void dispose(Node* p)
{
    if(p == NULL)
    {
        delete p;
    }
    else
    {
        Node* temp=p;
        p = p->next;
        delete temp;
        dispose(p);
    }
}

// the function that does the insertion sort in an ascending order
void sort(Node* &p)
{
    int i, j, length=0;
    char value;
    Node* temp = p;
    
    while(temp != NULL)
    {
        temp = temp->next;
        length++;
        }
    
    temp=p;
    
    for(i=1 ; i<length ; i++)
    {
        j=i;
        
        while(j>0 && p->data > p->next->data)
        {
            value = temp->next->data;
            temp->next->data = temp->data;
            temp->data = value;
            j--;
            }
        }
    }



// the main function
#include <iostream>
using namespace std;


int main(int argc, char* argv[])
{
    Node* p;
    p = build(argv[1]);
    print(p);
    
    p = build(argv[1]);
    print(p);
    
    sort(p);
    print(p);
    

    return 0;
}

```

---

### Post by cariboo on 2010-05-15
Programming questions should be asked in the Programming Talk sub-forum. Moved.

---

### Post by slavik on 2010-05-16
well, you provided the code. this is a homework problem.

please tell us what problem you have exactly (what isn't working or throwing an error), otherwise this will be closed with "we don't do homework for you" :)

---

### Post by pirlo89 on 2010-05-16
ok, the code is supposed to convert the string/strings into a link list. print the link list. sort the link list. print the link list again. The program is supposed to read data from the command line.

the code after some tries...

```


#include <iostream>
using namespace std;

// structure for the link list
struct Node {
    char data;
    Node* next;
    Node(char d, Node* n);
};

Node::Node(char d, Node* n)
{
    data = d;
    next = n;
}

// the function that builds the link list
Node* build(char* p)
{
    if((*p) == 0)
        return NULL;
    else
        return new Node((*p), build(p+1));
}


//the function that prints the link list
void print(Node* p)
{
    cout<<'<';
    while(p != NULL)
    {
        cout<< p->data;
        p = p->next;
        if(p != NULL)
            cout<<'-';
    }
    cout<<'>';
}


// the function that deletes the link list
void dispose(Node* p)
{
    if(p == NULL)
    {
        delete p;
    }
    else
    {
        Node* temp=p;
        p = p->next;
        delete temp;
        dispose(p);
    }
}

// the function that does the insertion sort in an ascending order
void sort(Node* &p)
{
    int i, j, length=0;
    char value;
    Node* temp = p;
    
    while(temp != NULL)
    {
        temp = temp->next;
        length++;
        }
    
    temp=p;
    
    for(i=1 ; i<length ; i++)
    {
        j=i;
        
        while(j>0 && p->data > p->next->data)
        {
            for(int x=0 ; x<j ; x++)
            {
                temp= temp->next;
                }
            value = temp->next->data;
            temp->next->data = temp->data;
            temp->data = value;
            j--;
            }
            temp=p;
        }
    }



// the main function
#include <iostream>
using namespace std;


int main(int argc, char* argv[])
{
    Node** p = new Node* [argc-1];

    for(int i=0; i<argc; i++)
    {
        p[i] = build(argv[i]);            
    }
            
    for(int i=0; i<argc; i++)
    {
        print(p[i]);
    }
    
    

    
    cout<<endl;

    return 0;
}

```
my exact problem is with the sort function (insertion sort). i understand the logic of it. i even know how to do it for arrays. but not for linked list.

---

### Post by slavik on 2010-05-16
why are you building the list recursively?

first thing you want to do is, make it build a linked list. next ... if you want a sorted list, why do you have a sort function? sorted linked lists sort data on insert (traverse existing list and put new node in proper place).

---

### Post by pirlo89 on 2010-05-16
i finally did it. now the only problem is when sending nothing. the program is supposed to print <>. but instead, it prints nothing. can anyone help :confused:


edit: i just forgot to dispose of the list, its complete now.

```


#include <iostream>
using namespace std;

// structure for the link list
struct Node {
    char data;
    Node* next;
    Node(char d, Node* n);
};

Node::Node(char d, Node* n)
{
    data = d;
    next = n;
}

// the function that builds the link list
Node* build(char* p)
{
    if((*p) == 0)
        return NULL;
    else
        return new Node((*p), build(p+1));
}


//the function that prints the link list
void print(Node* p)
{
    cout<<'<';
    while(p != NULL)
    {
        cout<< p->data;
        p = p->next;
        if(p != NULL)
            cout<<'-';
    }
    cout<<'>';
}


// the function that deletes the link list
void dispose(Node* p)
{
    if(p == NULL)
    {
        delete p;
    }
    else
    {
        Node* temp=p;
        p = p->next;
        delete temp;
        dispose(p);
    }
}

// the function that does the insertion sort in an ascending order
void sort(Node* &p)
{
    Node* temp1=p;
    Node* temp2=p;
    char val;
    int cnst = 0;
    
    while(temp1!=NULL && temp2!=NULL)
    {
        temp2 = p;
        for(int i=0; i<cnst; i++)
        {
            if(temp1->data < temp2->data)
            {
                val = temp1->data;
                temp1->data = temp2->data;
                temp2->data = val;
                }
            temp2 = temp2->next;
            }
        temp1 = temp1->next;
        cnst++;
        }
    }


// the main function
#include <iostream>
using namespace std;


int main(int argc, char* argv[])
{
    Node** p = new Node* [argc-1];

    for(int i=1; i<argc; i++)
    {
        p[i-1] = build(argv[i]);            
    }
            
    for(int i=0; i<(argc-1); i++)
    {
        print(p[i]);
    }
    
    for(int i=0; i<(argc-1); i++)
    {
        sort(p[i]);
    }
        
    for(int i=0; i<(argc-1); i++)
    {
        print(p[i]);
    }
    
    for(int i=0; i<(argc-1); i++)
    {
        dispose(p[i]);
    }

    
    cout<<endl;

    return 0;
}

```

---

### Post by pirlo89 on 2010-05-16
> **slavik said:**
> why are you building the list recursively?

well, why not?

i am going to create a list, then print, then sort, then print again. in that order.

---

### Post by pirlo89 on 2010-05-16
plz help, i need to submit in 5 hours. :(

---

