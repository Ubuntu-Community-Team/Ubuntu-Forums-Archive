---
title: "Segmentation fault when running program"
date: 2012-04-16
forum: Programming Talk
---

### Post by solidster on 2012-04-16
Hi; guys here is my program typed in gedit i dnt know everything looks so perfect after i execute i get an error called "segmentation fault" PLZ HELP NEED IT URGENT PLZ :D 
The program is binary tree 
):P
Ive put the attachment plz solve it for :D

```
#include<iostream>
#include<cmath>
using namespace std;
struct node
{
  int ele[4];
  int child[4];
};
 
 class btree
 {
   public:
   node *tree[10][10];
   int count[10];
   int leaf;
   int path[10];
   btree();
   node*create();
   void insert(int);
   void main_ser(int);
   void display();
   void ins_node(node*,int);
   void ser(int);
   int ser_node(node*,int);
   int nodefull(node*);
   void split(node*);
 };

btree::btree()
{
   leaf=-1;
   for(int i=0;i<10;i++)
   {
     count[i]=-1;
     path[i]=-1;
   }
}

node*btree:: create()
{
   node *n;
   n=new node;
   for(int i=0;i<4;i++)
   { 
     n->ele[i]=-1;
     n->child[i]=-1;
   }
   return n;
}

void btree::insert(int key)
{
  int n,parent;
  node *first_node;
  if(leaf==-1)
  {
   first_node==create();
   tree[0][0]=first_node;
   leaf++;
   count[0]++;
   first_node->ele[0]=key;
  }
  else if(leaf==0)
  {
    if(nodefull(tree[0][0]))
    {
      path[leaf]=0;
      split(tree[0][0]);
      insert(key);
    }
   else
   ins_node(tree[0][0],key);
   }
   else 
   {
     ser(key);
     n=path[leaf];
     parent=path[leaf-1];
     if(nodefull(tree[leaf][n]))
     {
       split(tree[leaf][n]);
       insert(key);
     }
    else 
    ins_node(tree[leaf][n],key);
   }
 }
 void btree::main_ser(int key)
 {
    int flag=0,i;
    node *node1;
    ser(key);
    node1=tree[leaf][path[leaf]];
    for(i=0;node1->ele[i]!=-1;i++)
    if(node1->ele[i]==key)
    {
      flag=1;
      break;
    }
    cout<<"\n the path traversed is ";
    for(i=0;path[i]!=-1;i++)
    cout<<path[i]<<"->";
    if(flag)
    cout<<"\n element found";
    else
    cout<<"\n not found";
 }
   
void btree:: display()
{ 
   int i,j,k;
   for(i=0;i<=leaf;i++)
   { 
     cout<<"\n level -----"<<i<<"\n";
     for(j=0;j<=count[i];j++)
     {
       for(k=0;tree[i][j]->ele[k]!=-1;k++)
       cout<<" "<<tree[i][j]->ele[k];
       cout<<"\t";
     }
   }
}

void btree:: ser(int key)
{
   int i,j,temp;
   path[0]=0;
   if(leaf)
   {
     j=0;
     for(i=0;i<leaf;i++)
     { 
       temp=ser_node(tree[i][j],key);
       path[i+1]=temp;
       j=temp;
     }
   }
}

int btree:: ser_node(node *node1,int key)
{
  for(int i=0;i<4;i++)
  {
    if(key<=node1->ele[i])
    return node1->child[i];
    else if(node1->ele[i+1]==-1)
    return node1->child[i];
   }
}

int btree:: nodefull(node *node1)
{  
   if(node1->ele[3]!=-1)
   return 1;
   else 
   return 0;
}

void btree::ins_node(node *node1,int key)
{
  int flag=0,count=-1,i,j,x,y,t;
  node *newnode,*n1;
  for(i=0;i<4;i++)
  if(node1->ele[i]!=-1)
  ++count;
  i=0;
  while(!flag && node1->ele[i]!=-1)
  {
    if(node1->ele[i]>key)
    {
       flag=1;
       for(int j=count;j>=i;j--)
      node1->ele[j+1]=node1->ele[j];
      node1->ele[i]=key;
    }
   i++;
  }
  if(!flag)
  {
    node1->ele[count+1]=key;
    for(i=leaf-1;i>=0;i--) 
    {
     n1=tree[i][path[i]];
     for(t=0;n1->ele[t]!=-1;t++);
     n1->ele[t-1]=key;
    }
   }
 for(i=0;i<=count+1;i++)
 cout<<"\t\t"<<node1->ele[i];
 }
void btree:: split(node *oldnode)
{
  node *newnode,*parent,*n1,*n2;
  int i,j,k,n,t,x,y,pos;
  newnode=create(); 
  newnode->ele[0]=oldnode->ele[2];
  newnode->ele[1]=oldnode->ele[3];
  oldnode->ele[2]=-1;
  oldnode->ele[3]=-1;
  t=count[leaf];
  n=path[leaf];
  for(i=t,j=t+1;i>n;i--,j--)
  tree[leaf][j]=tree[leaf][i];
  tree[leaf][n+1]=newnode;
  count[leaf]++;
  x=leaf;
  if(count[leaf]+1==1)
  t=1;
  else
  t=log(count[leaf]+1)/log(2);
  if(t!=leaf)
  {
    ++leaf;
    count[leaf]=count[x];
    for(i=0;i<=count[leaf];i++)
    std::swap(tree[leaf][i],tree[x][i]);
  }
  for(i=leaf-1;i>=0;i--)
  count[i]=-1;
  for(i=t,j=i-1;i>0;i--,j--)
  {
   for(k=0;k<(count[i]+1)/2;k++)
   {  
     n1=tree[i][2*k];
     n2=tree[i][(2*k)+1];
     for(x=0;n1->ele[x]!=-1;x++);
     for(y=0;n2->ele[y]!=-1;y++);
     newnode=create();
     count[j]++;
     tree[j][count[j]]=newnode;
     newnode->ele[0]=n1->ele[x-1];
     newnode->child[0]=2*k;
     newnode->ele[1]=n2->ele[y-1];
     newnode->child[1]=(2*k)+1;
   }
  if(count[i]!=1&&count[i]%2==0)
  {
    n2=tree[i][count[i]];
    newnode->ele[2]=n2->ele[y-1];
    newnode->child[2]=count[i];
  }
  }
  }
int main()
{
  btree bt;
  int ch,key;
  while(1)
  {
     cout<<"\n\n\n MAIN MENU\n ---------------\n1.insert\n2.search\n3.display\n4.exit\n\nENter ur choice";
     cin>>ch;
     switch(ch)
     {
       case 1: cout<<"\n enter the element";
               cin>>key;
               bt.insert(key);
               break;
       case 2: cout<<"enter a key";
               cin>>key;
               bt.main_ser(key);
               break;
       case 3:bt.display();
              break;
       case 4: return 0;
      default:cout<<"\n enter the valid choice";
   }
  }
}
```

---

### Post by Barrucadu on 2012-04-16
Have you tried running it through valgrind? Here are some errors from it I get:

```
==28284== Memcheck, a memory error detector
==28284== Copyright (C) 2002-2011, and GNU GPL'd, by Julian Seward et al.
==28284== Using Valgrind-3.7.0 and LibVEX; rerun with -h for copyright info
==28284== Command: ./a.out
==28284== 



 MAIN MENU
 ---------------
1.insert
2.search
3.display
4.exit

ENter ur choice1

 enter the element5



 MAIN MENU
 ---------------
1.insert
2.search
3.display
4.exit

ENter ur choice3

 level -----0
==28284== Invalid read of size 4
==28284==    at 0x400C7D: btree::display() (in /home/barrucadu/tmp/a.out)
==28284==    by 0x400999: main (in /home/barrucadu/tmp/a.out)
==28284==  Address 0x0 is not stack'd, malloc'd or (recently) free'd
==28284== 
==28284== 
==28284== Process terminating with default action of signal 11 (SIGSEGV)
==28284==  Access not within mapped region at address 0x0
==28284==    at 0x400C7D: btree::display() (in /home/barrucadu/tmp/a.out)
==28284==    by 0x400999: main (in /home/barrucadu/tmp/a.out)
==28284==  If you believe this happened as a result of a stack
==28284==  overflow in your program's main thread (unlikely but
==28284==  possible), you can try to increase the size of the
==28284==  main thread stack using the --main-stacksize= flag.
==28284==  The main thread stack size used in this run was 8388608.
==28284== 
==28284== HEAP SUMMARY:
==28284==     in use at exit: 32 bytes in 1 blocks
==28284==   total heap usage: 1 allocs, 0 frees, 32 bytes allocated
==28284== 
==28284== 32 bytes in 1 blocks are definitely lost in loss record 1 of 1
==28284==    at 0x4C2A437: operator new(unsigned long) (in /usr/lib/valgrind/vgpreload_memcheck-amd64-linux.so)
==28284==    by 0x400BAD: btree::create() (in /home/barrucadu/tmp/a.out)
==28284==    by 0x401337: btree::insert(int) (in /home/barrucadu/tmp/a.out)
==28284==    by 0x400A03: main (in /home/barrucadu/tmp/a.out)
==28284== 
==28284== LEAK SUMMARY:
==28284==    definitely lost: 32 bytes in 1 blocks
==28284==    indirectly lost: 0 bytes in 0 blocks
==28284==      possibly lost: 0 bytes in 0 blocks
==28284==    still reachable: 0 bytes in 0 blocks
==28284==         suppressed: 0 bytes in 0 blocks
==28284== 
==28284== For counts of detected and suppressed errors, rerun with: -v
==28284== ERROR SUMMARY: 2 errors from 2 contexts (suppressed: 3 from 3)
zsh: segmentation fault  valgrind --tool=memcheck --leak-check=full --show-reachable=yes ./a.out

```

```
==28428== Memcheck, a memory error detector
==28428== Copyright (C) 2002-2011, and GNU GPL'd, by Julian Seward et al.
==28428== Using Valgrind-3.7.0 and LibVEX; rerun with -h for copyright info
==28428== Command: ./a.out
==28428== 



 MAIN MENU
 ---------------
1.insert
2.search
3.display
4.exit

ENter ur choice1

 enter the element57



 MAIN MENU
 ---------------
1.insert
2.search
3.display
4.exit

ENter ur choice2
enter a key9
==28428== Invalid read of size 4
==28428==    at 0x400DCB: btree::main_ser(int) (in /home/barrucadu/tmp/a.out)
==28428==    by 0x4009CB: main (in /home/barrucadu/tmp/a.out)
==28428==  Address 0x0 is not stack'd, malloc'd or (recently) free'd
==28428== 
==28428== 
==28428== Process terminating with default action of signal 11 (SIGSEGV)
==28428==  Access not within mapped region at address 0x0
==28428==    at 0x400DCB: btree::main_ser(int) (in /home/barrucadu/tmp/a.out)
==28428==    by 0x4009CB: main (in /home/barrucadu/tmp/a.out)
==28428==  If you believe this happened as a result of a stack
==28428==  overflow in your program's main thread (unlikely but
==28428==  possible), you can try to increase the size of the
==28428==  main thread stack using the --main-stacksize= flag.
==28428==  The main thread stack size used in this run was 8388608.
==28428== 
==28428== HEAP SUMMARY:
==28428==     in use at exit: 32 bytes in 1 blocks
==28428==   total heap usage: 1 allocs, 0 frees, 32 bytes allocated
==28428== 
==28428== 32 bytes in 1 blocks are definitely lost in loss record 1 of 1
==28428==    at 0x4C2A437: operator new(unsigned long) (in /usr/lib/valgrind/vgpreload_memcheck-amd64-linux.so)
==28428==    by 0x400BAD: btree::create() (in /home/barrucadu/tmp/a.out)
==28428==    by 0x401337: btree::insert(int) (in /home/barrucadu/tmp/a.out)
==28428==    by 0x400A03: main (in /home/barrucadu/tmp/a.out)
==28428== 
==28428== LEAK SUMMARY:
==28428==    definitely lost: 32 bytes in 1 blocks
==28428==    indirectly lost: 0 bytes in 0 blocks
==28428==      possibly lost: 0 bytes in 0 blocks
==28428==    still reachable: 0 bytes in 0 blocks
==28428==         suppressed: 0 bytes in 0 blocks
==28428== 
==28428== For counts of detected and suppressed errors, rerun with: -v
==28428== ERROR SUMMARY: 2 errors from 2 contexts (suppressed: 3 from 3)
zsh: segmentation fault  valgrind --tool=memcheck --leak-check=full --show-reachable=yes ./a.out

```

It looks like you're trying to dereference a null pointer.

---

### Post by Arndt on 2012-04-16
Have you tried the debugger?

---

### Post by jwbrase on 2012-04-16
It looks to me like you've got a fair number of places where you access elements of tree[][] that may not have been initialized.

---

### Post by dwhitney67 on 2012-04-16
> **solidster said:**
> Hi; guys here is my program typed in gedit i dnt know everything looks so perfect after i execute i get an error called "segmentation fault" PLZ HELP NEED IT URGENT PLZ :D 
The program is binary tree 
):P
Ive put the attachment plz solve it for :D


IT MAY BE URGENT FOR YOU, but not for the rest of us.

As for your code, look at the warnings it generates:
```

btree.cpp: In member function ‘void btree::insert(int)’:
btree.cpp:57:24: warning: value computed is not used [-Wunused-value]
btree.cpp:53:9: warning: variable ‘parent’ set but not used [-Wunused-but-set-variable]
btree.cpp: In member function ‘void btree::ins_node(node*, int)’:
btree.cpp:161:25: warning: unused variable ‘j’ [-Wunused-variable]
btree.cpp:161:27: warning: unused variable ‘x’ [-Wunused-variable]
btree.cpp:161:29: warning: unused variable ‘y’ [-Wunused-variable]
btree.cpp:162:9: warning: unused variable ‘newnode’ [-Wunused-variable]
btree.cpp: In member function ‘void btree::split(node*)’:
btree.cpp:193:18: warning: unused variable ‘parent’ [-Wunused-variable]
btree.cpp:194:21: warning: unused variable ‘pos’ [-Wunused-variable]
btree.cpp: In member function ‘int btree::ser_node(node*, int)’:
btree.cpp:149:1: warning: control reaches end of non-void function [-Wreturn-type]
btree.cpp: In member function ‘void btree::insert(int)’:
btree.cpp:58:25: warning: ‘first_node’ may be used uninitialized in this function [-Wuninitialized]

```

Please correct these.

I used the following command to generate these warnings:
```

g++ -Wall -pedantic btree.cpp

```
where btree.cpp is from the code you originally posted.

---

