---
title: "program to make graph in C"
date: 2010-11-30
forum: Programming Talk
---

### Post by jamesbon on 2010-11-30
I am making a program for having a graph in C.I am having some problem in making it please see my code and let me know what is the problem.How can I improve it.It is not a home work problem.
Following file is graph.c
```

#include "declarations.h"
graph root = NULL;

int main()
{
    cgraph();
}

void cgraph(void)
{
    int n, choice, dir, count;

    choice = 1;
    count = 1;
    graph priv, temp;

    printf("Printf we are making a graph the first is root node\n");
    while (choice == 1) {
        count++;
        if (count == 1) {
            printf("This is going to be root node \n");
            scanf("%d", &n);
            root = cnode(n);
            count--;
            priv = root;
        }        //ending if
        else {
            printf ("Enter direction you want to go LEFT 1 RIGHT 2 TOP 3 DOWN 4\n");
            scanf("%d", &dir);
            printf("Enter the data  for graph node\n");
            scanf("%d", &n);
            temp = cnode(n);
            if (dir == 1) {
                priv->LEFT = temp;
            }
            if (dir == 2) {
                priv->RIGHT = temp;
            }
            if (dir == 3) {
                priv->TOP = temp;
            }
            if (dir == 4) {
                priv->DOWN = temp;
            }
            priv = temp;
        }        //ending else
        printf ("Enter 1 to continue adding nodes to graph any thing else would take you out\n");
        scanf("%d", &choice);
    }            //ending while
}                //ending main

graph cnode(int data)
{
    graph temp = (graph) malloc(sizeof(graph));

    temp->data = data;
    temp->LEFT = NULL;
    temp->RIGHT = NULL;
    temp->TOP = NULL;
    temp->DOWN = NULL;
    temp->color = -1;
    return temp;
}

qnode travel_graph(graph rh)
{
 qnode qt;
 if(rh->LEFT)
 {
 qt= cque(rh);
 }
 if(rh->RIGHT)
 {
 qt=cque(rh);
 }
 if(rh->TOP)
 {
 qt=cque(rh);
 }
 if(rh->DOWN)
 {
 qt=cque(rh);
 }
return qt;
}


``` I add a node
A->B
I will not be able to do 
C
^
|
A->B

---

### Post by Zugzwang on 2010-11-30
> **jamesbon said:**
> I am making a program for having a graph in C.I am having some problem in making it please see my code and let me know what is the problem.How can I improve it.It is not a home work problem.
Following file is graph.c
[...]
Following file is declarations.h
[...]
Following file is que.c
[...]
following file is stack.c
[...]
I would suggest you help me to improve my code that will help you do your assignment.
[...]


Would you please explain what you mean by "I would suggest you help me to improve my code that will help you do your assignment." - I don't get it.

---

### Post by jamesbon on 2010-12-01
> **Zugzwang said:**
> Would you please explain what you mean by "I would suggest you help me to improve my code that will help you do your assignment." - I don't get it.

I am not getting the logic to make nodes in graph.When I was writing the program according to my logic if I have to add one node to a node then it will do.But if one the same node I want to add one more node that wont happen.

 For example my code would add a  node from A to B 

 A->B 
but if I want to add one more 
```

 A->B
 |
 v
 C
```
from A to C that would not happen.

---

### Post by Arndt on 2010-12-01
I image he wanted you to explain the sentence "I would suggest you help me to improve my code that will help you do your assignment", especially the words "I", "you" and "assignment". I know I do.

---

### Post by jamesbon on 2010-12-01
...

---

### Post by Arndt on 2010-12-01
> **jamesbon said:**
> ...

Something is to follow, apparently. We're waiting eagerly.

---

### Post by worksofcraft on 2010-12-01
> **Arndt said:**
> I image he wanted you to explain the sentence "I would suggest you help me to improve my code that will help you do your assignment", especially the words "I", "you" and "assignment". I know I do.

It is against forum poilcy to do people's assignments for them. We also don't do assignments for people who post them on behalf of others so that they can claim it isn't *their* homework.

IMHO the OP should refer to his/her own [previous thread on the subject]("http://ubuntuforums.org/showthread.php?t=1634359&highlight=graph")

---

### Post by jamesbon on 2010-12-02
How do I explain or what proof do I give that this is not any home work problem or any one elses problem.I am trying to improve my programming skills by implementing some thing given in books very well.Home works have deadlines to meet.This is 3rd consecutive week I am discussing it on a forum and God knows how much time more it will take.
I recently made a device driver and jumped to network programming.Started working on kernel sort of things.Many a times I got stuck at simple problems so I decided to improve my C programming skills first.I remember I read a book of Algorithms by Coreman a long time back. So I  thought of making a graph as it would be a good exercise as I had made Binary tree from that and did some traversals.When I started making it then I realized it is not easy to make a graph forget rest of the algorithms on graph.The book says about matrix way of representing the graphs and also linked list way to make graph.
I decided to make it via linked list.
The entire purpose of doing this is to be able to improve my programming skills.
I made the stack que for the same program where I will test the functions for BFS DFS in graph.But I am not clear with nodes adding to a graph.
Cant you people see my rest of the threads where I ask kernel sort of things where most of you who are saying it to be a homework problem are not able to even understand the question forget the reply thing.In last thread **dwhitney67** told it to be a homework problem I had to argue it is not .Every one here is strong head they do not want to listen.Why would some one ask their home work problem here.It would be damn easy to copy paste from some of their friend.I would assume that if some one is asking a question then he might not have the time to wait for the assignment to be solved on a forum he would better off by doing a copy paste than waiting on some forums for weeks after weeks to understand it.

---

### Post by Some Penguin on 2010-12-02
If it really takes you weeks to work on this problem, you're not really working, period.

---

### Post by trent.josephsen on 2010-12-03
The time spent writing your rant could have been better spent clarifying what exactly your problem is.  If it were phrased more like "I don't understand the behavior of this program; can you explain it to me" and less like "I have some problem with this code; will you read my mind and fix it", then you might get better answers.

Seriously, it's almost as if somebody gave you a code listing you didn't understand... and rather than trying to understand it yourself, you posted on an Internet forum asking for somebody to understand it for you.  Regardless of whether it's really a homework problem, your *modus operandi* is flawed.  If you want better answers, [**ask better questions**](http://www.catb.org/~esr/faqs/smart-questions.html).

---

### Post by jamesbon on 2010-12-03
> **trent.josephsen said:**
> 
Seriously, it's almost as if somebody gave you a code listing you didn't understand...
I am not asking any one for code.You try to make a graph yourself I can bet you wont be able to do so.

The thing which I want to make is when I run my program ./a.out then the user should be able to make a graph on any random sort of data that he might enter and connect the edges.
The first thing that came to my mind was to create many linked list and then depending upon which of the elements are connected I make pointers point from different linked list to those elements.But that is not a good logic because in this case I am already aware of how a graph looks like on paper.In this case what I am trying to implement a program which takes a given data set as an input (which would be quite random)
and then starts joining those edges.
You call it rant or what ever at least I am trying to learn and better than you that I do ask rather than keeping quite and assuming that I know most of you will not be able to create a make a graph in C using linked lists and pointers.
I checked there is a Boost graph library in C++ but I do not want to use it.
I want to make in C.
Before posting non sense just try to implement yourself and then you will understand what I asked.If you do not know what to work then do not reply.
This forum is full of non sensiscal people who do not understand basic things but will give lecture and show attitude (as if they understand which they do not)rather than giving some sensible answer when some one tries to understand.
You better read a How to on answering question rather than giving non sense replies.

---

### Post by Arndt on 2010-12-03
> **jamesbon said:**
> I am not asking any one for code.You try to make a graph yourself I can bet you wont be able to do so.


Hehe, sorry, that method won't work.

Please explain post number 5 to me - before that I will not make any attempts to understand your question.

---

### Post by lisati on 2010-12-03
Just a note to those who have tried to understand the OP's question (perhaps English is not his first language): "assignment" doesn't necessarily refer to homework, it can also refer to the process of assigning a value to a variable.

---

### Post by worksofcraft on 2010-12-03
sigh
well 007, you seem to have cut most of your original post out so now we can't really see what is wrong anyway... however

I spot you have
[php]
   count = 1;
...
    while (choice == 1) {
        count++; // so first time round it is gunna be 2
        if (count == 1) { // how you gunna get a 1 in here then?
... I mean you have no root node for a start
[/php]

then I spot you do
[php]
    graph temp = (graph) malloc(sizeof(graph));
... so graph is a kind of pointer and you are mallocing memory
for the size of a pointer... that isn't going to be big enough to store your struct that has atleast 4 pointers and an int in it...
[/php]

Even if you provide the declarations does it actually compile?

---

### Post by saulgoode on 2010-12-03
> **jamesbon said:**
> ```
        else {
            printf ("Enter direction you want to go LEFT 1 RIGHT 2 TOP 3 DOWN 4\n");
            scanf("%d", &dir);
            printf("Enter the data  for graph node\n");
            scanf("%d", &n);
            temp = cnode(n);
            if (dir == 1) {
                priv->LEFT = temp;
            }
            if (dir == 2) {
                priv->RIGHT = temp;
            }
            if (dir == 3) {
                priv->TOP = temp;
            }
            if (dir == 4) {
                priv->DOWN = temp;
            }
            priv = temp;
        }        //ending else
```

Test to see if a target node already exists before creating a new one. Also, when you create a target node, make sure that it links back to the source node. 

```
        else {
            printf ("Enter direction you want to go LEFT 1 RIGHT 2 TOP 3 DOWN 4\n");
            scanf("%d", &dir);
            printf("Enter the data  for graph node\n");
            scanf("%d", &n);
            temp = priv; /* stay on current node if input not 1-4 */
            if (!priv->LEFT && (dir == 1)) {
                temp = cnode(n);
                priv->LEFT = temp;
                temp->RIGHT = priv;
            }
            if (!priv->RIGHT && (dir == 2)) {
                temp = cnode(n);
                priv->RIGHT = temp;
                temp->LEFT = priv;
            }
            if (!priv->TOP && (dir == 3)) {
                temp = cnode(n);
                priv->TOP = temp;
                temp->DOWN = priv;
            }
            if (!priv->DOWN && (dir == 4)) {
                temp = cnode(n);
                priv->DOWN = temp;
                temp->UP = priv;
            }
            priv = temp;
        }        //ending else
```

As general advice, I would recommend you employ more descriptive function and variable names -- especially if you will be sharing your code with others and expecting feedback. Barring that, provide some comments about your cryptically named functions and variables. What does 'cnode()' do? What is 'temp'? What is 'priv'? 

Perhaps if you didn't expect people to guess about such things, it would not take weeks and weeks to resolve problems.

---

### Post by jamesbon on 2010-12-03
> **saulgoode said:**
> Test to see if a target node already exists  before creating a new one. Also, when you create a target node, make  sure that it links back to the source node. 

```
        else {
            printf ("Enter direction you want to go LEFT 1 RIGHT 2 TOP 3 DOWN 4\n");
            scanf("%d", &dir);
            printf("Enter the data  for graph node\n");
            scanf("%d", &n);
            temp = priv; /* stay on current node if input not 1-4 */
            if (!priv->LEFT && (dir == 1)) {
                temp = cnode(n);
                priv->LEFT = temp;
                temp->RIGHT = priv;
            }
            if (!priv->RIGHT && (dir == 2)) {
                temp = cnode(n);
                priv->RIGHT = temp;
                temp->LEFT = priv;
            }
            if (!priv->TOP && (dir == 3)) {
                temp = cnode(n);
                priv->TOP = temp;
                temp->DOWN = priv;
            }
            if (!priv->DOWN && (dir == 4)) {
                temp = cnode(n);
                priv->DOWN = temp;
                temp->UP = priv;
            }
            priv = temp;
        }        //ending else
```As general advice, I would  recommend you employ more descriptive function and variable names --  especially if you will be sharing your code with others and expecting  feedback. Barring that, provide some comments about your cryptically  named functions and variables. What does 'cnode()' do? What is 'temp'?  What is 'priv'? 

Perhaps if you didn't expect people to guess about such things, it would not take weeks and weeks to resolve problems.

Ok priv is a variable I created to store the value of previous node so that when I create a new node I have a pointer to previous node.
cnode is a function I wrote to create a node for graph.(It just does malloc for my struct)
I had assumed the degree of vertices to be 4 but this may not be the case since a graph can have many many vertices with same connections.
Imagine on a world map if I am making a program to connect different flights from source to destinations and if I were to make a graph for them then there can be n number of possibilities.

> **worksofcraft said:**
> sigh
well 007, you seem to have cut most of your original post out so now we can't really see what is wrong anyway... however

I spot you have
[php]
   count = 1;
...
    while (choice == 1) {
        count++; // so first time round it is gunna be 2
        if (count == 1) { // how you gunna get a 1 in here then?
... I mean you have no root node for a start
[/php]then I spot you do
[php]
    graph temp = (graph) malloc(sizeof(graph));
... so graph is a kind of pointer and you are mallocing memory
for the size of a pointer... that isn't going to be big enough to store your struct that has atleast 4 pointers and an int in it...
[/php]Even if you provide the declarations does it actually compile?
Ya what you understood is very very correct.
I initially had this logic in my mind that I first create a rood node that is why I had created a count variable (just to make sure if it is the first node of my graph).
Later on on a paper and pen I figured it is not going to work this way.
I feel it should be a recursive function.
The steps 
a) create a node
b) ask user  no of child nodes he wants this node to have
c) enter data for nod
d) call function again to have child node

but then this logic I thought has a problem that I am not able to connect those child nodes some where.To the remaining vertices (who might look connected on paper)

Then I thought of another approach which is to make an array of pointers.
Each of these pointers is going to point to start of a link list as if it were an adjacency matrix and then I make some checks which can conncect the individual edges.
I came across a very interesting link here on Carnighe Mellon Universities site
[http://www.cs.cmu.edu/~biorobotics/software/tslam_v1.0/HTML/SOURCE/GRAPH-FUNCS/graph.c.html]("http://www.cs.cmu.edu/%7Ebiorobotics/software/tslam_v1.0/HTML/SOURCE/GRAPH-FUNCS/graph.c.html")


I do not want to do what these people above have done.

---

### Post by jamesbon on 2010-12-03
> **Arndt said:**
> Hehe, sorry, that method won't work.

What is so funny in that?
> **Arndt said:**
> 
Please explain post number 5 to me - before that I will not make any attempts to understand your question.

Read this thread onus is my nick name
[http://forum.codecall.net/c-c/34462-creating-pie-graph-using-c-language.html#post283097]("http://forum.codecall.net/c-c/34462-creating-pie-graph-using-c-language.html")
A guy here is trying to do make a pie graph.I  do not know what a pie graph is but thinking that he might be trying to make a graph which would convert to a some pie thing I thought he would first make  graph so   I asked him to improve my code (since I am trying to make a graph)
so that would benefit him as he would be able to understand how a graph is programmed.
I had posted the same message here and while I was modifying here was a reply.
My attempt is very genuine attempt to make a graph in C and it is not a homework problem.
It has been 3 weeks that itself shows that I am trying to make it on my own but I am not getting the correct logic for it.
I am not asking for code I just need suggestion for logic as if I were to write a recursive function as above then what 
can be the possible thing that I can do.
Or if any one else has a better approach.
Check this message of mine
[http://ubuntuforums.org/showthread.php?t=1634201](http://ubuntuforums.org/showthread.php?t=1634201)
in past 3 months I have tried to improve a lot of programming skills of mine.
I daily read the Linux Kernel code (after my office finishes where I do not do CS job neither programming a donkeys work) and try to understand various type of logics implemented in it.Specially the PCI core architecture related board specific codes which I have started understanding to some extent.
Many a times you people see very simple C syntax questions of mine of this forum which I encounter while reading kernel code.
So based on your suggestions I read Kernighan Ritchie after that some one suggested I need to improve my programming 
skills.So I decided to work upon a simple but not very simple problem this graph thing is in continuation with these efforts.
Any of the questions which I post are not home work problem in some thread if I ask kernely thing you people say to improve programming skill and if in some thread I actually start working on that suggestion then even a guy like **dwhiteny67**  say it is a home work problem what do I do?
I do not really understand that how do I tell I am trying to improve my programming skills and not doing home work problems.

---

### Post by saulgoode on 2010-12-03
> **jamesbon said:**
> I had assumed the degree of vertices to be 4 but this may not be the case since a graph can have many many vertices with same connections.
Imagine on a world map if I am making a program to connect different flights from source to destinations and if I were to make a graph for them then there can be n number of possibilities.
The only change then would be to maintain the node's connections as a linked list (rather than the four pointer fields you currently have). When you add a connection from the current node ('*priv*') to a new destination ('*temp*'), you would add the pointer to *priv*'s list of connections, but also add a connection (back to *priv*) to *temp*'s list of connections.

---

### Post by jamesbon on 2010-12-03
> **saulgoode said:**
> The only change then would be to maintain the node's connections as a linked list (rather than the four pointer fields you currently have). When you add a connection from the current node ('*priv*') to a new destination ('*temp*'), you would add the pointer to *priv*'s list of connections, but also add a connection (back to *priv*) to *temp*'s list of connections.
This is  a good suggestion a macro in Linux Kernel to make Link list does similar thing that you suggested.
[http://manpages.ubuntu.com/manpages/gutsy/man3/list.3abz.html](http://manpages.ubuntu.com/manpages/gutsy/man3/list.3abz.html)
It can contains a link list by which we can reach parent node immediately instead of traversing through the entire list.
I wonder why I did not had this idea earlier.Great but let us not divert I just gave an example of a real world problem.
Are you suggesting to maintain a link list of edges in my case?

---

### Post by worksofcraft on 2010-12-03
> **jamesbon said:**
> ...
I initially had this logic in my mind that I first create a rood node that is why I had created a count variable (just to make sure if it is the first node of my graph).
Later on on a paper and pen I figured it is not going to work this way...


You are correct to first do it on paper and consider how the user is going to be able to enter the nodes and edges. This is the basis of actually designing software.

So how about the user dialog goes something like this
(In the following C = computer U = user)

C: How many nodes would you like?
U: 10
C: Specify an edge by entering two node numbers or 0 to terminate
U: 5 2
C: Specify an edge by entering two node numbers or 0 to terminate
U: 7 2
C: Specify an edge by entering two node numbers or 0 to terminate
U: 1 7
C: Specify an edge by entering two node numbers or 0 to terminate
U: 2 3
... etcetera
C: Specify an edge by entering two node numbers or 0 to terminate
U: 0


so it looks something like this:
```

      5
      |
1--7--2--3

```

Note: Don't expect to be able to draw every graph on a rectangular grid and without paths crossing... Laying out computer circuit boards is far from a trivial problem and that's basically what you would be trying to solve if you wanted to draw the thing that has been entered.

What were you hoping to do with your graph?

---

### Post by saulgoode on 2010-12-03
> **jamesbon said:**
> Are you suggesting to maintain a link list of edges in my case?
I am suggesting that *each node * maintains its own list of connected nodes. If you also maintain a list of all nodes* then it is not necessary to maintain a separate list of all edges because that is just the union of all of the nodes' individual connection lists.



* When programming in C, the typical way of maintaining this list of all nodes would be to have each node structure contain a field pointing to the next node (rather than maintaining a separate list of all nodes).

---

### Post by Some Penguin on 2010-12-03
> **worksofcraft said:**
> You are correct to first do it on paper and consider how the user is going to be able to enter the nodes and edges. This is the basis of actually designing software.

So how about the user dialog goes something like this
(In the following C = computer U = user)

C: How many nodes would you like?
U: 10
C: Specify an edge by entering two node numbers or 0 to terminate
U: 5 2
C: Specify an edge by entering two node numbers or 0 to terminate
U: 7 2
C: Specify an edge by entering two node numbers or 0 to terminate
U: 1 7
C: Specify an edge by entering two node numbers or 0 to terminate
U: 2 3
... etcetera
C: Specify an edge by entering two node numbers or 0 to terminate
U: 0


Fairly standard approach.  For an undirected graph where the only question is "edge there or not there" -- no weights or anything like that -- it is exactly problem as storing an upper (or lower, it doesn't matter) triangular matrix whose values are either 0 or 1.  If the graph is sparse, then it is pretty efficient for most purposes to use an adjacency list representation; for dense graphs in terms of edge : vertex ratio, simply storing half a matrix makes more sense.  And using "node id : node id" representations trivially avoids nonsense like most of the this thread.

One could of course used named nodes and maps; this costs some overhead (string indices being slower to use than integer indices, generally) but may be nicer to use.

---

### Post by jamesbon on 2010-12-03
> **saulgoode said:**
> 
* When programming in C, the typical way of maintaining this list of all nodes would be to have each node structure contain a field pointing to the next node (rather than maintaining a separate list of all nodes).
Yea this is how link list and stack ,que etc I had implemented.> **saulgoode said:**
> I am suggesting that *each node * maintains its own list of connected nodes. 
Ok you mean to say some thing like
```

struct node {
               ...
                ...
               ...
           struct node a[10];
}
```
Assuming that I can connect one node to maximum 10 more nodes.
Is this what you say then this is what I have already done.
My problem is the function part how do I create graph.
Not the data structure part.

---

### Post by jamesbon on 2010-12-03
> **worksofcraft said:**
> 

Note: Don't expect to be able to draw every graph on a rectangular grid and without paths crossing... Laying out computer circuit boards is far from a trivial problem and that's basically what you would be trying to solve if you wanted to draw the thing that has been entered.

Yea exactly this is what I am trying to say. 
> **worksofcraft said:**
> 
What were you hoping to do with your graph?

I have made simple programs using stacks,que's link lists,include tree also in this.
But I never implemented a graph in C even though I understand all the algorithms very well.
When I started working on it then I realized it is not as easy as it looks in books.


So I want to brush up my basics by this (by not reading algorithms but actually implementing them).

---

### Post by nvteighen on 2010-12-03
I'd go for an intersection matrix (I don't remember the formal term for this). Look, for a graph like this:

```

A----B
|\
| \
|  \
|   \
C----D

```

You can use this representation, where 1 means the nodes are connected and 0 means no connection.

```

  A B C D
  =======
A|0 1 1 1
B|1 0 0 0
C|1 0 0 1
D|1 0 1 0

```

The matrix is symmetrical because we haven't established the direction in which connection is done. We're just representing whether nodes are or not connected. An asymmetrical matrix (I leave the exercise to you) can be used to add directionality to node relationships, such that if A -> B, A connects to B but B doesn't to A.

As you see, there you have your graph compressed into a very simple data structure.

What I want you to see is that you've been modelling your graph from the "tree diagram" logic, which, although it isn't incorrect, it isn't the simplest way to program because it's of a lower conceptual level than the matrix approach, which abstracts the graph as what it really is: a set of relations. Your approach will only be able to take a subset of graphs that can be shown as a tree diagram, with "upper" and "lower" levels... but a circular graph doesn't have that.

The matrix approach has the "downside" that it requires you to write a middle layer to convert the matrix in the "visual graph" the user wants to see and navigate. Rethink the navigation issue; I suggest you forget spacial categories and focus on node relations for navigation.

If you want example code, well, fortunately I asked a very similar question a couple of years ago. Search it at these forums and you may find both a C and a Python implementation I wrote; it's a bit restricted (integers only and the root is set to be the smalles number in the graph) and it's probably not my best code, but it worked.

---

### Post by saulgoode on 2010-12-03
> **jamesbon said:**
> ```

struct node {
               ...
                ...
               ...
           struct node a[10];
}
```
Assuming that I can connect one node to maximum 10 more nodes.
Is this what you say then this is what I have already done.
Close enough. Personally, I would use a pointer to linked list rather than an array. I'd also make the struct not a node, but a "connection"; so that it could have its own associated data that may be entirely different from that of a node (distance, last used, frequency, etc).

> **jamesbon said:**
> My problem is the function part how do I create graph.
Not the data structure part.
If the goal is to have a user interact with your program and from this interaction your program generates the graph, I would suggest starting by deciding what to do when the user asks to "visit" a node. 

[INDENT]Does the node you wish to visit exist? If not, then do you want to create it?

Is there already a direct connection from the current node to the target node? If not, then do you want to create it (or maybe you'd rather search for an indirect connection)? If there already is a connection, do you want an additional connection or is just having the one satisfactory? [/INDENT]

The steps that your program takes to address those questions should effectively create your graph.

---

### Post by jamesbon on 2010-12-03
> **nvteighen said:**
> 
The matrix approach has the "downside" that it requires you to write a middle layer to convert the matrix in the "visual graph" the user wants to see and navigate. Rethink the navigation issue; I suggest you forget spacial categories and focus on node relations for navigation.

I had thought of this thing that you said.But the problem I see is directions I wont be having in this approach.Or it would work like a middle layer as you said.


> **saulgoode said:**
> 
Does the node you wish to visit exist? If not, then do you want to create it?

If the goal is to have a user interact with your program and from this interaction your program generates the graph, I would suggest starting by deciding what to do when the user asks to "visit" a node. 

Yes you got it.This is what I was trying to put it in my words.
When I wanted to implement this thing I did not know what is the thing I was trying to achieve but now I am clear.
The only over head in this case being I have to call some function which each time would travel the entire graph to detect if a node exists or not.
For small graph that will be ok but if the number of nodes is as large as 10000 the function call would be an over head.
This should work.

---

### Post by Vaphell on 2010-12-03
so store the nodes in some kind of balanced binary tree which for 10000 nodes would require 14 operations to access nodes in the worst case scenario.

---

### Post by worksofcraft on 2010-12-03
> **nvteighen said:**
> I'd go for an intersection matrix (I don't remember the formal term for this). Look, for a graph like this:

```

A----B
|\
| \
|  \
|   \
C----D

```

You can use this representation, where 1 means the nodes are connected and 0 means no connection.

```

  A B C D
  =======
A|0 1 1 1
B|1 0 0 0
C|1 0 0 1
D|1 0 1 0

```

The matrix is symmetrical because we haven't established the direction in which connection is done. We're just representing whether nodes are or not connected. An asymmetrical matrix (I leave the exercise to you) can be used to add directionality to node relationships, such that if A -> B, A connects to B but B doesn't to A.

As you see, there you have your graph compressed into a very simple data structure.

What I want you to see is that you've been modelling your graph from the "tree diagram" logic, which, although it isn't incorrect, it isn't the simplest way to program because it's of a lower conceptual level than the matrix approach, which abstracts the graph as what it really is: a set of relations. Your approach will only be able to take a subset of graphs that can be shown as a tree diagram, with "upper" and "lower" levels... but a circular graph doesn't have that.

The matrix approach has the "downside" that it requires you to write a middle layer to convert the matrix in the "visual graph" the user wants to see and navigate. Rethink the navigation issue; I suggest you forget spacial categories and focus on node relations for navigation.

If you want example code, well, fortunately I asked a very similar question a couple of years ago. Search it at these forums and you may find both a C and a Python implementation I wrote; it's a bit restricted (integers only and the root is set to be the smalles number in the graph) and it's probably not my best code, but it worked.

Yes, this is a very neat way of studying general graph theory.
I think it is one of the ways the boost library graphs operate.

It is however not easy to dynamically add and remove nodes in such a system because the dimensions of your matrix will keep changing. It creates complications like if you use indexes to iterate in the matrix: They all change when you delete a node.

This is why I asked the OP was his intended application is. I get the impression that ultimately the OP, jamesbond isn't really interested in graph theories, but more in having a dynamic set of interlinked data structures... which one can model with a graph.

---

### Post by nvteighen on 2010-12-03
> **worksofcraft said:**
> Yes, this is a very neat way of studying general graph theory.
I think it is one of the ways the boost library graphs operate.

It is however not easy to dynamically add and remove nodes in such a system because the dimensions of your matrix will keep changing. It creates complications like if you use indexes to iterate in the matrix: They all change when you delete a node.

This is why I asked the OP was his intended application is. I get the impression that ultimately the OP, jamesbond isn't really interested in graph theories, but more in having a dynamic set of interlinked data structures... which one can model with a graph.

Hm... yeah, I am aware of that issue. And of course, without further details, we can't help a lot.

---

### Post by jamesbon on 2011-03-26
> **worksofcraft said:**
> 
 I get the impression that ultimately the OP, jamesbond isn't really interested in graph theories, but more in having a dynamic set of interlinked data structures... which one can model with a graph.
Ok after 7 months of posting the problem originally I started with it again.You understood right I am more interested to have a dynamic set of interlinked data structures.But the purpose is to study graph theories also.
> **worksofcraft said:**
> 
This is why I asked the OP was his intended application is.
There is no application as such I will at max be travelling in this interlinked data structure.By simple techniques like Breadth First Search or Depth First Search.How ever I am more interested as how can I maintain an interlinked list of data structures which can be represented like a graph.This graph can go on increasing and decreasing also randomly depending upon how the user who interacts with problem uses it to do so.

---

