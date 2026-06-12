---
title: "Bombing Problem"
date: 2010-11-05
forum: Programming Talk
---

### Post by c2tarun on 2010-11-05
i found this problem in codechef NOV10 competition.
[http://www.codechef.com/NOV10/problems/BOMBING/](http://www.codechef.com/NOV10/problems/BOMBING/)


here is my program:

[PHP]

#include<stdio.h>
#include<string.h>
#include<stdlib.h>

// these two variables will store the initial and final house of the particular protection
int* initial;
int* fin;
static int count=0;  // will count the total number of protections

 // in case protection will applied this function will update initial and final variables
void pro(int u,int v) 
{
  int i;  // loop variable
  *(initial+count)=u;
  *(fin+count)=v;
  count++;
}

// this function will move the protection.
void mov(int u,int v)
{
  u--;
  *(initial+u)+=v;
  *(fin+u)+=v;
}


// this function will return the number of protections protecting the house x
int bomb(int x)
{
  int p=0,i;
  for(i=0;i<count;i++)
    {
      if(*(initial+i)<=x && *(fin+i)>=x)
    p++;
    }
  return p;
}


int main(void)
{
  long n;    // number of houses
  long m;   // number of lines to be entered, may be protection, move or bombing
  char* str=NULL;  // take the input
  char* temp;  // processing on input
  size_t sz=25;  // used in getline
  int u,v;  // variables used to extract info from text and pass into various functions
  int i;  // loop variable

  getline(&str,&sz,stdin);

// extracting first two integer i.e. number of houses and input lines
  temp=strtok(str," ");
  n=atoi(temp);
  temp=strtok(NULL,"\n");
  m=atoi(temp);

// allocating memory for number of input lines
  initial=(int*)malloc((m)*sizeof(int));
  fin=(int*)malloc((m)*sizeof(int));

// processing
  while(m--)
    {
      getline(&str,&sz,stdin);
      temp=strtok(str," ");

// if protection is applied in input line
      if(temp[0]=='P')
    {
      u=atoi(strtok(NULL," "));
      v=atoi(strtok(NULL,"\n"));
      pro(u,v);
    }
      else if(temp[0]=='B')  // if bombing is done in input line
    {
      u=atoi(strtok(NULL,"\n"));
      printf("%d\n",bomb(u));
    }
      else if(temp[0]=='M')  // if move is done in input line
    {
      u=atoi(strtok(NULL," "));
      temp=strtok(NULL,"\n");
      if(temp[0]=='-')
        {
          i=1;
          v=0;
          while(temp[i])
        v=v*10 + ((int)temp[i++] - 48);
          v*=-1;
        }

      else
        v=atoi(temp);
      mov(u,v);
    }
    }
  return 0;
}
[/PHP]i posted all the comments that may be helpful in understanding of the program.
my problem is i need to speed up this program without using too much memory.
can anyone please suggest me a way. please.

---

### Post by dwhitney67 on 2010-11-06
> **c2tarun said:**
> 
my problem is i need to speed up this program without using too much memory.
can anyone please suggest me a way. please.

Remove the getline() calls, and instead receive command line arguments.


P.S.  I would not be too concerned with "speed" if your program is going to be dependent on getting input from a user.

---

### Post by c2tarun on 2010-11-07
> **dwhitney67 said:**
> Remove the getline() calls, and instead receive command line arguments.


P.S.  I would not be too concerned with "speed" if your program is going to be dependent on getting input from a user.


actually in a way i m getting input from outside but in a very speedy manner.
there are huge test cases saved in text files.
at execution time i use

$ ./bombing < testcase1


this reduces the time for input. the problem is with program execution. the program is taking too long to print the output. i tried replacing all else if with switch case, but nothing happened.

---

### Post by Tony Flury on 2010-11-07
> **c2tarun said:**
> actually in a way i m getting input from outside but in a very speedy manner.
there are huge test cases saved in text files.
at execution time i use

$ ./bombing < testcase1


this reduces the time for input. the problem is with program execution. the program is taking too long to print the output. i tried replacing all else if with switch case, but nothing happened.

Why do you think the switch will be any quicker - it is likely (with a good compiler like gcc) to result in exactly the same machine code to be executed - comparisons and branches.

---

### Post by c2tarun on 2010-11-07
> **Tony Flury said:**
> Why do you think the switch will be any quicker - it is likely (with a good compiler like gcc) to result in exactly the same machine code to be executed - comparisons and branches.


sorry i just shot an arrow in the dark.
i was not knowing that switch will do no good.
but good thing is now i know that switch is as good as else if. :)
but my problem still persists.

---

### Post by dwhitney67 on 2010-11-07
It would be helpful to see what input you are providing the application.  It also would be nice to see a version of your application where you actually **free** each of the strings that is allocated and returned by getline().

From the man-page:
```

DESCRIPTION
       getline()  reads  an entire line from stream, storing the address of the buffer containing
       the text into *lineptr.  The buffer is null-terminated and includes the newline character,
       if one was found.

       If  *lineptr  is  NULL,  then getline() will allocate a buffer for storing the line, which
       should be freed by the user program.  (The value in *n is ignored.)

```

---

### Post by c2tarun on 2010-11-07
> **dwhitney67 said:**
> It would be helpful to see what input you are providing the application.  It also would be nice to see a version of your application where you actually **free** each of the strings that is allocated and returned by getline().

From the man-page:
```

DESCRIPTION
       getline()  reads  an entire line from stream, storing the address of the buffer containing
       the text into *lineptr.  The buffer is null-terminated and includes the newline character,
       if one was found.

       If  *lineptr  is  NULL,  then getline() will allocate a buffer for storing the line, which
       should be freed by the user program.  (The value in *n is ignored.)

```


actually the bigger test cases are with the website owners.
i have a pretty small one.
**Input:**
7 5
P 1 4
P 3 5
B 3
M 2 1
B 3

**Output:**
2


when i m posting the program there they check it with their own test case, they are giving error time limit exceeded...
1

---

### Post by Arndt on 2010-11-07
> **c2tarun said:**
> actually the bigger test cases are with the website owners.
i have a pretty small one.
**Input:**
7 5
P 1 4
P 3 5
B 3
M 2 1
B 3

**Output:**
2


when i m posting the program there they check it with their own test case, they are giving error time limit exceeded...
1

What time limit is that? Can you get them to give you their test cases and check how long it takes on your computer?

I would also ask for the output generated before the time limit was exceeded.

---

### Post by c2tarun on 2010-11-07
> **Arndt said:**
> What time limit is that? Can you get them to give you their test cases and check how long it takes on your computer?

I would also ask for the output generated before the time limit was exceeded.


friends, the website dont tell us anything, they just give us the question, the sample output and on submitting if program gives the desired output on there test case in the given time, they give that program is correct.  but in my case they r just saying that time limit exceeded.:confused:

---

### Post by Arndt on 2010-11-07
> **c2tarun said:**
> friends, the website dont tell us anything, they just give us the question, the sample output and on submitting if program gives the desired output on there test case in the given time, they give that program is correct.  but in my case they r just saying that time limit exceeded.:confused:

Do you know for sure that "time limit exceeded" doesn't also include the case where the test case fails?

Send in something trivial but wrong, that can't possibly cause time limit exceeded, and see what they report.

I haven't looked much at your code, but may there be cases where it enters an infinite loop?

---

### Post by johnl on 2010-11-07
The problem is with this:

```

int bomb(int x)
{
  int p=0,i;
  for(i=0;i<count;i++)
    {
      if(*(initial+i)<=x && *(fin+i)>=x)
    p++;
    }
  return p;
}

```

This is going to be too slow when there are 250,000 entries in the list to search through.

I would see if you could do something like this (psuedocode):

```

houses = array(num_of_houses)
pros   = array(max_protections)

fill(houses, 0)

func protect(start, end)
  pros.append({start, end})
  for i from start to end:
      houses[i]++

func move(index, offset)
  pro = pros[--index]
  // can you think of the logic to update
  // the houses array here ?
  // a simple (but not the most efficient one might be):
  for i from pro.start to pro.end:
      houses[i]--

  pro.start += offset
  pro.end   += offset

  for i from pro.start to pro.end:
      houses[i]++


// since we did all the work ahead of time, the bomb() function is simple:
func bomb(index)
    return houses[i]

```

---

### Post by c2tarun on 2010-11-07
> **johnl said:**
> The problem is with this:

```

int bomb(int x)
{
  int p=0,i;
  for(i=0;i<count;i++)
    {
      if(*(initial+i)<=x && *(fin+i)>=x)
    p++;
    }
  return p;
}

```This is going to be too slow when there are 250,000 entries in the list to search through.

I would see if you could do something like this (psuedocode):

```

houses = array(num_of_houses)
pros   = array(max_protections)

fill(houses, 0)

func protect(start, end)
  pros.append({start, end})
  for i from start to end:
      houses[i]++

func move(index, offset)
  pro = pros[--index]
  // can you think of the logic to update
  // the houses array here ?
  // a simple (but not the most efficient one might be):
  for i from pro.start to pro.end:
      houses[i]--

  pro.start += offset
  pro.end   += offset

  for i from pro.start to pro.end:
      houses[i]++


// since we did all the work ahead of time, the bomb() function is simple:
func bomb(index)
    return houses[i]

```


bro i completely agree with u..
my first submission to that website was the following one.

[PHP]
// http://www.codechef.com/NOV10/problems/BOMBING/

#include<stdio.h>
#include<stdlib.h>
#include<string.h>

struct test
{
  int initial,final;
  struct test* next;
};
typedef struct test test;

test* node=NULL;
test* start=NULL;
int* house;  // to store the number of protections on a house
static int count=0;  // to store total number of protections

void pro(int u,int v)
{
  int i;  // loop variable
  if(node==NULL)
    {
      node=(test*)malloc(sizeof(test));
      start=node;
    }
  else
    {
      node->next=(test*)malloc(sizeof(test));
      node=node->next;
    }
  node->initial=u;
  node->final=v;
  node->next=NULL;

  for(i=u;i<=v;i++)
    *(house+i)=*(house+i) + 1;
}

void mov(int u,int v)
{
  test* temp;
  int i;
  temp=start;
  for(i=2;i<=u;i++)
    temp=temp->next;
  if(v>0)
    {
      for(i=0;i<v;i++)
    {    
      *(house+i+temp->initial)-=1;
      *(house+i+temp->final+1)+=1;
    }
    }
  else
    {
      for(i=0;i>v;i--)
    {
      *(house+temp->initial-1+i)+=1;
      *(house+temp->final+i)-=1;
    }
    }  
  temp->initial=(temp->initial)+v;
  temp->final=(temp->final)+v;
}
  

int main(void)
{
  long n;  // number of houses
  long m;  // number of input lines
  char* str=NULL;  // string variable to take inputs
  char* temp;  // a temporary variable to store integer before conversion to integer
  size_t sz=25;
  int u,v;  // to store the houses under a protection
  int i;  // loop variable

  // enter the number of houses and lines
  getline(&str,&sz,stdin);

  temp=strtok(str," ");
  n=atoi(temp);
  temp=strtok(NULL,"\n");
  m=atoi(temp);
  house=(int*)malloc((n+1)*sizeof(int));

  while(m--)
    {
      getline(&str,&sz,stdin);
      temp=strtok(str," ");
      if(temp[0]=='P')
    {
      u=atoi(strtok(NULL," "));
      v=atoi(strtok(NULL,"\n"));
      pro(u,v);
    }
      else if(temp[0]=='B')
    {
      u=atoi(strtok(NULL,"\n"));
      printf("%d\n",*(house+u));

    }
      else if(temp[0]=='M')
    {
      u=atoi(strtok(NULL," "));
      temp=strtok(NULL,"\n");
      if(temp[0]=='-')
        {
          i=1;
          v=0;
          while(temp[i])
        v=v*10 + ((int)temp[i++] - 48);
          v*=-1;
        }
      else
        v=atoi(temp);
      mov(u,v);
    }
    }
  return 0;
}
[/PHP]

this implements your logic.
this is also not accepted.
anyway on 11 nov competetion will be over then they will let us to view the correct solution of there problem. i'll post the correct answer here.
thanx for help folks

---

### Post by StephenF on 2010-11-07
You are doing a linear search in the bomb function which is the slowest method although the easiest to code.

I'm currently investigating b-trees and hash tables as part of a solution.

Figure I create one b-tree for every different protection range and place the first protected house in the correct b-tree for it's corresponding protection range along with its index value in the protection index to uniquely identify it.

There would be a hash table to look up the correct tree based on it's protection range. This will determine if we need a new tree or use an existing one. 500000 buckets should be enough (worst case 50% fill). Will do the linear probing trick with wrap around.

The protection index would be a vector type (a C++ vector type workalike unless actually using C++) to grow the linearly indexed list of protection systems and it needs to store the corresponding tree head and the first protected house. This is used for insertion and moving of protection systems.

Finally another vector type storing pointers to the heads of all the trees to allow lookup during bombing.

The protection range covered by each tree will be stored in its head.

Code must fit in 50000 bytes. Hopefully.

---

### Post by StephenF on 2010-11-07
> **johnl said:**
> ```
houses = array(num_of_houses)
// since we did all the work ahead of time, the bomb() function is simple:
func bomb(index)
    return houses[i]

```

There are up to 10^9 houses. Do you really want to potentially allocate an array of almost 4GB? New computers only recently surpassed that size in absolute RAM terms. Somehow I doubt that amount can be allocated without swapping to disk which would completely kill the performance.

---

### Post by c2tarun on 2010-11-07
> **StephenF said:**
> You are doing a linear search in the bomb function which is the slowest method although the easiest to code.

I'm currently investigating b-trees and hash tables as part of a solution.

Figure I create one b-tree for every different protection range and place the first protected house in the correct b-tree for it's corresponding protection range along with its index value in the protection index to uniquely identify it.

There would be a hash table to look up the correct tree based on it's protection range. This will determine if we need a new tree or use an existing one. 500000 buckets should be enough (worst case 50% fill). Will do the linear probing trick with wrap around.

The protection index would be a vector type (a C++ vector type workalike unless actually using C++) to grow the linearly indexed list of protection systems and it needs to store the corresponding tree head and the first protected house. This is used for insertion and moving of protection systems.

Finally another vector type storing pointers to the heads of all the trees to allow lookup during bombing.

The protection range covered by each tree will be stored in its head.

Code must fit in 50000 bytes. Hopefully.


b-tree and hashing can search faster, but if only we have to search only one element from the whole heap.

** Case 1: not declaring the house array.** then we have to traverse through all the protections in order to check which protection is being applied to the given house and which is not. if we have to traverse the whole lot i think linear or b-tree or any other searching technique will make any difference.

**Case 2: declaring the house array.** if we declare the house array there is no need of using any search technique. ( but still if we use your searching techniques + declare the memory of house array, i think i can beat there time).

can u please just look at the code and tell me will this code give any segmentation fault at any particular input, i just contacted the website and they mailed me that i m getting SIGSEGV error. i googled it and found this error will come in case of Segmentation Fault. This SIGSEGV error is coming with the second code, first code is still giving Time Limit Expired error.

Thanx

---

### Post by StephenF on 2010-11-07
> **c2tarun said:**
> b-tree and hashing can search faster, but if only we have to search only one element from the whole heap.

So searching two elements makes the method slower? This I don't believe.
> 
** Case 1: not declaring the house array.** then we have to traverse through all the protections in order to check which protection is being applied to the given house and which is not. if we have to traverse the whole lot i think linear or b-tree or any other searching technique will make any difference.

You just need to traverse all the b-trees. Not that difficult although worst case you get 250000 of them due to all the protections being of different sizes. At least then you don't have to catch any bombs. :)

Lets say if one particular b-tree is containing all those protecting a range of 200 and the bomb is on house 4000 we need only search for the numbers 3800 to 4000 within this b-tree. Such searches take a worst case 32 steps per number but its probably possible to pull out the range in only one sweep.
> 
**Case 2: declaring the house array.** if we declare the house array there is no need of using any search technique. ( but still if we use your searching techniques + declare the memory of house array, i think i can beat there time).

Like I said earlier the upper limit for a house array is a ridiculous 4GB. How much RAM is in your computer? Simply relying on the test being kind when the problem specification says it could be anything but, is bad programming practise.

Edit: Still, it could be possible to hash the house numbers into inputs * 2 buckets (rounded up). That would give fast searching for bombing but leaves you with a major search problem if one protection system keeps being moved and has a range of fifty million houses.
> 
can u please just look at the code and tell me will this code give any segmentation fault at any particular input, i just contacted the website and they mailed me that i m getting SIGSEGV error. i googled it and found this error will come in case of Segmentation Fault. This SIGSEGV error is coming with the second code, first code is still giving Time Limit Expired error.

They are caused by dereferencing NULL pointers such as are returned by failed mallocs or just plain stuff that's uninitialised. Anyway I'm busy right now. I have written my vector stuff and nearly have the hash table done. Feeling confident about b-trees all of a sudden. 319 lines of code so far.

---

### Post by verma_par on 2010-11-09
hey tarun use segment trees to solve this question your logic is right, but it demands a special data structure.
hey guys : any hints on [http://www.codechef.com/NOV10/problems/BALANCED/](http://www.codechef.com/NOV10/problems/BALANCED/)

---

### Post by c2tarun on 2010-11-09
> **verma_par said:**
> hey tarun use segment trees to solve this question your logic is right, but it demands a special data structure.
hey guys : any hints on [http://www.codechef.com/NOV10/problems/BALANCED/](http://www.codechef.com/NOV10/problems/BALANCED/)

hey can u please enlighten me a bit about the special data structure, i m not getting what u are trying to say. sry

---

### Post by verma_par on 2010-11-09
[http://www.topcoder.com/tc?module=Static&d1=tutorials&d2=lowestCommonAncestor#Segment_Trees](http://www.topcoder.com/tc?module=Static&d1=tutorials&d2=lowestCommonAncestor#Segment_Trees)
read about it, perhaps you will be able to solve it after this.

any idea about the balanced walks, it think that's direct, no special data structure for that

---

### Post by c2tarun on 2010-11-11
[PHP]
#include <cstdio>
#include <cassert>
#include <cctype>
#include <algorithm>
using namespace std;
 
// a left-leaning red-black tree implementation
struct LLRB{
	int val, cnt;
	bool red;
	int children;
	struct LLRB *left, *right;
	LLRB(int v, int c): val(v), cnt(c), red(true), children(0), left(NULL), right(NULL){}
};
 
// various helper functions
int size(const LLRB *node){
	return node==NULL ? 0 : node->cnt+node->children;
}
 
bool is_red(const LLRB *node){
	return node==NULL ? false : node->red;
}
 
void rot_l(LLRB **node){
	LLRB *tmp=*node;
	*node=(*node)->right;
	tmp->right=(*node)->left;
	(*node)->left=tmp;
	tmp->children=size(tmp->left)+size(tmp->right);
	(*node)->children=size(tmp)+size((*node)->right);
	swap((*node)->red, (*node)->left->red);
}
 
void rot_r(LLRB **node){
	LLRB *tmp=*node;
	*node=(*node)->left;
	tmp->left=(*node)->right;
	(*node)->right=tmp;
	tmp->children=size(tmp->left)+size(tmp->right);
	(*node)->children=size((*node)->left)+size(tmp);
	swap((*node)->red, (*node)->right->red);
}
 
void balance(LLRB **node){
	if(is_red((*node)->left)){
		if(is_red((*node)->left->left))
			rot_r(node);
		if(is_red((*node)->right)){
			(*node)->red=true;
			(*node)->left->red=false;
			(*node)->right->red=false;
		}
	}else if(is_red((*node)->right)){
		rot_l(node);
	}
}
// the important functions
void insert(LLRB **node, int val, int cnt=1){
	while(*node){
		balance(node);
		if((*node)->val==val){
			(*node)->cnt+=cnt;
			return;
		}
		(*node)->children+=cnt;
		node=val<(*node)->val ? &(*node)->left : &(*node)->right;
	}
	*node=new LLRB(val, cnt);
}
 
int rank(const LLRB *node, int val){
	int result=0;
	while(node){
		if(val<node->val){
			node=node->left;
		}else{
			result+=size(node->left)+node->cnt;
			node=node->right;
		}
	}
	return result;
}
 
int defence[250000][2], cnt=0;
 
int main(){
	int n, m;
	LLRB *tree=NULL;
	scanf("%d%d", &n, &m);
	assert(0<n && n<=1e9);
	while(m--){
		char command;
		int op1, op2;
		scanf(" %c", &command);
		assert(command=='P' || command=='M' || command=='B');
		if(command=='P'){
			scanf("%d%d", &op1, &op2);
			assert(0<=op1 && op1<=op2 && op2<=n);
			op2++;
			insert(&tree, op1, 1);
			insert(&tree, op2, -1);
			defence[cnt][0]=op1;
			defence[cnt][1]=op2;
			cnt++;
		}else if(command=='M'){
			scanf("%d%d", &op1, &op2);
			assert(0<op1 && op1<=cnt);
			op1--;
			insert(&tree, defence[op1][0], -1);
			insert(&tree, defence[op1][1], 1);
			defence[op1][0]+=op2;
			defence[op1][1]+=op2;
			assert(0<=defence[op1][0] && defence[op1][1]<=n+1);
			insert(&tree, defence[op1][0], 1);
			insert(&tree, defence[op1][1], -1);
		}else if(command=='B'){
			scanf("%d", &op1);
			assert(0<=op1 && op1<=n);
			printf("%d\n", rank(tree, op1));
		}
	}
	return 0;
}[/PHP]

this is the correct solution.
i m marking this thread as solved.

---

