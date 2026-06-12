---
title: "how to define a structure node in graph in a c program"
date: 2010-10-26
forum: Programming Talk
---

### Post by jamesbon on 2010-10-26
I wanted to implement a graph.By graph I mean to say that I am writing programs for BFS,DFS and other such stuff and want to see them in action.

For this I started writing a program.The first entry point is to define a graph.
I took a pen and paper and made a graph.
Now to be able to code this in C.I defined a structure but I am finding problem in defining this structure.
I looked into Google and came across incidence list and adjacency list representation
[http://en.wikipedia.org/wiki/Incidence_list](http://en.wikipedia.org/wiki/Incidence_list)
after understanding that I am not able to understand how do I define my structure that would be a node in graph.

Here is what my graph looks like
> 
 |-----------31
 |               |
 |    2---4---6---8
 |    |
 --- 5--13-------|
      |              19
 |---12---27-----|
 |    |      |
 -----       |
              28 
This is the above graph the numbers would be what I will give as input but I am not able to understand how do I define a structure for the same.

 
27 is connected to 28
12 has an edge to itself
31 is connected to 6 and not 2 as you see in question
The formating of above graph in forum is not coming clearly so when I save in quotes the changes get lost.
Ok here is a pictorial representation[IMG]http://www.flickr.com/photos/55167530@N02/5119750360/[/IMG]
[]("http://www.flickr.com/photos/55167530@N02/5119750360/")
[IMG]http://farm5.static.flickr.com/4038/5119750360_299b45d9aa.jpg[/IMG]
[IMG]http://www.flickr.com/photos/55167530@N02/5119750360/sizes/m/in/photostream/[/IMG]

---

### Post by TiBaal89 on 2010-10-26
Try using the "code" tags, they will preserve the formatting of your graph...

All you need is a struct which contains a pointer to another struct of that type.  For instance, if your graph were a binary tree, you might have pointers for the left and right children, and for the parent.  The root would have a null parent pointer, leaves would have null children pointers, etc.

For an arbitrary graph, where the nodes may be of any degree, you'd need to keep an array (or some such thing) of pointers to other node objects.  That can be tricker.  If you're really new to this, I'd suggest implementing a binary tree to get a hang of what's going on.  Generalizing it to an arbitrary graph would not be hard if you had working tree code.

Of course throw an int or something in the struct to act as the 'key.'

---

### Post by worksofcraft on 2010-10-27
Hum... well off the top of my head here is a C++ version for your graph, I'll leave you to convert it to C though ;)

[php]
// compile: g++ bfsdfs.cpp
// run: ./a.out
#include <vector>
#include <list>
#include <stdio.h>
using namespace std;

// a node has a value (identifier) and
// contains a bunch of pointers to more nodes
struct node: vector<node *> {
	int iValue;
	// when creating a node add pointers to all it's parents
	node(int iD, node *pParent = NULL, node *pParent2 = NULL): iValue(iD) {
		if (pParent) pParent->push_back(this);
		if (pParent2) pParent2->push_back(this);
	}
};

// depth first: recursively descend into each child node
void dfs(node &rNode) {
	printf("dfs: node=%d\n", rNode.iValue);
	for (int i=0; i < rNode.size(); i++) dfs(*rNode[i]);
}

// breadth first: append all the child nodes to the end of the list
// and process it in order
struct node_list: list<node *> {
	// we do need a node to start with
	node_list(node &rStartNode) {
		push_back(&rStartNode);
	};

	void bfs() {
		if (empty()) return; // reached end of list
		// process the one at the head of the list
		node & rNode = *front();
		printf("bfs: node=%d\n", rNode.iValue);
		// append all it's kids to the list
		for (int i = 0; i < rNode.size(); i++) push_back(rNode[i]);
		pop_front(); // remove the one we just did
		bfs(); // tail recursion to iterate
	}
};

int main(int argc, char *argv[]) {
	// these are the nodes that "007" gave us
	node sNode1(1);
	node sNode31(31, &sNode1);
	node sNode5(5, &sNode1);
	node sNode2(2, &sNode5);
	node sNode4(4, &sNode2);
	node sNode6(6, &sNode4, &sNode31);
	node sNode8(8, &sNode6);
	node sNode13(13, &sNode5);
	node sNode12(12, &sNode5);
	node sNode27(27, &sNode12);
	node sNode19(19, &sNode13, &sNode27);
	node sNode28(28, &sNode27);

	printf("depth first starting at node %d\n", sNode1.iValue);
	dfs(sNode1);

	printf("breadth first starting at node %d\n", sNode1.iValue);
	node_list sL(sNode1);
	sL.bfs();

	return !printf("exits normally\n");
}
[/php]

p.s. oh well I fixed that bfs anyway even if you don't need it ;)

---

### Post by jamesbon on 2010-10-27
> **TiBaal89 said:**
> 
For an arbitrary graph, where the nodes may be of any degree, you'd need to keep an array (or some such thing) of pointers to other node objects.  That can be tricker. 

Of course throw an int or something in the struct to act as the 'key.'
I made a binary tree in same forum I had asked questions which you can see from my profile I have made binary tree.This hint of your of an array sounds convincing.
```


 |--------------31
 |                  |
 |       2---4---6---8
 |       |
 --- 5--13-------|
      |               19
 |---12---27-----|
 |     |      |
 -----        28 

```
Well inside the code tags also it does not preserve information.

---

### Post by spjackson on 2010-10-27
While it is a C++ library, not C, you might consider looking at the Boost Graph Library [http://www.boost.org/doc/libs/1_44_0/libs/graph/doc/table_of_contents.html](http://www.boost.org/doc/libs/1_44_0/libs/graph/doc/table_of_contents.html) , or at least the documentation for the library.

Some things you need to consider in your design which you have not mentioned so far include:
Is the graph directed?
Is it cyclic or acyclic?

---

### Post by jamesbon on 2010-10-27
Well graphs can be of any time.Since I am in learning phase so not clear what to ask.

---

### Post by worksofcraft on 2010-10-27
> **spjackson said:**
> 
Some things you need to consider in your design which you have not mentioned so far include:
Is the graph directed?
Is it cyclic or acyclic?

I was just wondering if the distinction between *Breadth* and *Depth* search make any sense in a graph that is not directed?

In cyclic graphs James would have to decide whether he wants to avoid multiple visits to each node when they are in multiple paths. Like node 19 in his example.

---

### Post by TiBaal89 on 2010-10-27
> **worksofcraft said:**
> I was just wondering if the distinction between *Breadth* and *Depth* search make any sense in a graph that is not directed?

Yes, definitely... in BFS, you 'visit' every neighbor of a node before proceeding whereas in DFS you continue traversing to new nodes every time (i.e. go to the first neighbor you see).

There are examples of non-directed graph traversals using DFS on the wiki page:  [http://en.wikipedia.org/wiki/Depth-first_search](http://en.wikipedia.org/wiki/Depth-first_search)

---

### Post by worksofcraft on 2010-10-27
> **TiBaal89 said:**
> Yes, definitely... in BFS, you 'visit' every neighbor of a node before proceeding whereas in DFS you continue traversing to new nodes every time (i.e. go to the first neighbor you see).

There are examples of non-directed graph traversals using DFS on the wiki page:  [http://en.wikipedia.org/wiki/Depth-first_search](http://en.wikipedia.org/wiki/Depth-first_search)

Hum... yes that's a good article. There is also an example of both bfs and dfs in post #3 of this thread ;)

If one removes parent/child relationship... i.e. the **directionality** from the graph then I wonder which way is breadth and which way is depth? In your words, what constitutes a "neighbor" ?

For instance in the graph that James gave us, removing directionality of the graph...

Would 27 be a neighbor of 13 because they are both reachable directly from 19. Is 27 a neighbor of 5 because they are both reachable from 12? ... and if both the above were true then by inference does that make 5 and 13 neighbors of each other because they are both neighbors of 27? :confused:

p.s. oh and I see I had left out the link between 31 and 6... meh added that now... can you tell which way I made it go from this breadth first visiting sequence?
```


breadth first starting at node 1
bfs: node=1
bfs: node=31
bfs: node=5
bfs: node=6
bfs: node=2
bfs: node=13
bfs: node=12
bfs: node=8
bfs: node=4
bfs: node=19
bfs: node=27
bfs: node=6
bfs: node=19
bfs: node=28
bfs: node=8

```

---

### Post by TiBaal89 on 2010-10-27
I have to admit I did not review your C++ code... I surf forums between classes and whatnot and gave it the general TLDR treatment. :P

My definition of neighbor... if there exists an edge (x,y) then nodes x and y are neighbors.  Maybe the word 'adjacent' would be better.  

Does that make more sense?  The differences between BFS and DFS are many, directionality aside...

---

### Post by spjackson on 2010-10-27
> **worksofcraft said:**
> I was just wondering if the distinction between *Breadth* and *Depth* search make any sense in a graph that is not directed?

In cyclic graphs James would have to decide whether he wants to avoid multiple visits to each node when they are in multiple paths. Like node 19 in his example.
I was just looking for some precision; to me the unqualified term graph means an undirected simple graph. Indeed, BFS and DFS are not appropriate strategies for all types of graph, but I thought that perhaps jamesbon might be considering wider categories of graph in "BFS,DFS and other such stuff". What is that other stuff? Scope impacts on design.

---

### Post by worksofcraft on 2010-10-27
> **TiBaal89 said:**
> 
My definition of neighbor... if there exists an edge (x,y) then nodes x and y are neighbors.  Maybe the word 'adjacent' would be better.  

Does that make more sense?

No, not really. So in that case an "edge" would be a connection between them?

**Depth-first** to me means descending a hierarchy from *parent* to *child* (recursively) before moving on to a node's *siblings*. While **breadth-first** means queueing all the children of the current node to be processed AFTER all it's siblings have been visited.

Neither of those interpretations can work if there isn't a parent/child relation-ship between nodes i.o.w: Without direction I can't see what would distinguish between parent child or sibling. :confused:

Things always become much clearer when one attempts an actual implementation.

---

### Post by TiBaal89 on 2010-10-27
Honestly I don't see the hangup here... say you have an adjacency list for an undirected graph.  In a BFS you discover every adjacent edge before picking one to traverse to.  In DFS you take the first node off the adjacency list and traverse to it, continue as deep as you can, and come back to discover the others later.   

As for an implementation - from CLRS, chapter 22 section 3 (emphasis added):

> The following pseudocode is the basic depth-first-search algorithm. **The input graph G may be undirected or directed.** The variable time is a global variable that we use for timestamping.

```

DFS(G)
1  for each vertex u &#8712; V [G]
2       do color[u] &#8592; WHITE
3          &#960;[u] &#8592; NIL
4  time &#8592; 0
5  for each vertex u &#8712; V [G]
6       do if color[u] = WHITE
7             then DFS-VISIT(u)

DFS-VISIT(u)
1  color[u] &#8592; GRAY     &#9657;White vertex u has just been discovered.
2  time &#8592; time +1
3  d[u] time
4  for each v &#8712; Adj[u]  &#9657;Explore edge(u, v).
5       do if color[v] = WHITE
6             then &#960;[v] &#8592; u
7                         DFS-VISIT(v)
8  color[u] BLACK      &#9657; Blacken u; it is finished.
9  f [u] &#9657; time &#8592; time +1


```

---

### Post by worksofcraft on 2010-10-27
> **TiBaal89 said:**
> Honestly I don't see the hangup here... say you have an adjacency list for an undirected graph.  In a BFS you discover every adjacent edge before picking one to traverse to.  In DFS you take the first node off the adjacency list and traverse to it, continue as deep as you can, and come back to discover the others later.   

As for an implementation - from CLRS, chapter 22 section 3 (emphasis added):



```

DFS(G)
1  for each vertex u &#8712; V [G]
2       do color[u] &#8592; WHITE
3          &#960;[u] &#8592; NIL
4  time &#8592; 0
5  for each vertex u &#8712; V [G]
6       do if color[u] = WHITE
7             then DFS-VISIT(u)

DFS-VISIT(u)
1  color[u] &#8592; GRAY     &#9657;White vertex u has just been discovered.
2  time &#8592; time +1
3  d[u] time
4  for each v &#8712; Adj[u]  &#9657;Explore edge(u, v).
5       do if color[v] = WHITE
6             then &#960;[v] &#8592; u
7                         DFS-VISIT(v)
8  color[u] BLACK      &#9657; Blacken u; it is finished.
9  f [u] &#9657; time &#8592; time +1


```

I thought the graph was to be represented by nodes that have properties. I understood that the nodes would have connections between them and that we were interested in the two fundamental strategies of iterating the graph that they thus create.

Personally I really can't relate to [academia's terminology]("http://en.wikipedia.org/wiki/Adjacency_list") of "edges" and "adjacency" or to schemes of coloring them black, white or gray. TBH I CBA with it either.

---

### Post by spjackson on 2010-10-28
> **worksofcraft said:**
> No, not really. So in that case an "edge" would be a connection between them?

**Depth-first** to me means descending a hierarchy from *parent* to *child* (recursively) before moving on to a node's *siblings*. While **breadth-first** means queueing all the children of the current node to be processed AFTER all it's siblings have been visited.

Neither of those interpretations can work if there isn't a parent/child relation-ship between nodes i.o.w: Without direction I can't see what would distinguish between parent child or sibling. :confused:

Things always become much clearer when one attempts an actual implementation.
A graph is typically not a hierarchy; a subset of all possible graphs are hierarchies, for example trees are graphs. The Travelling Salesman Problem [http://en.wikipedia.org/wiki/Traveling_salesman_problem](http://en.wikipedia.org/wiki/Traveling_salesman_problem) is essentially an undirected cyclic weighted **graph**.
> 
I thought the graph was to be represented by nodes that have properties.  I understood that the nodes would have connections between them and  that we were interested in the two fundamental strategies of iterating  the graph that they thus create.
Edges may have properties too. Why two strategies? jamesbon's use of "BFS,DFS and other such stuff" in the original post sounds like greater than two strategies to me.
> 
Personally I really can't relate to [academia's terminology]("http://en.wikipedia.org/wiki/Adjacency_list") of "edges" and "adjacency" or to schemes of coloring them black, white or gray. TBH I CBA with it either.     
Ah well, if by graph you mean something other than the mathematical concept of graph, then it's no wonder that we are talking at cross-purposes.

---

### Post by worksofcraft on 2010-10-28
> **spjackson said:**
> 
Ah well, if by graph you mean something other than the mathematical concept of graph, then it's no wonder that we are talking at cross-purposes.

Well just like you, everyone else on these forums knows all about the general mathematical concepts of graphs also it is obvious what "other such stuff" means, so all we really needed was somone to google the right web pages.

OTOH, to me it seems that a distinction between "Depth First" and "Breadth First" makes no sense in the wider context where a graph has no directions. This is why I asked for clarification. I even went to the trouble of explaining with the concrete example as given by the OP after having produced my own practical and original implementation and demonstration of the two algorithms that were requested.

---

### Post by nvteighen on 2010-10-28
This thread reminds of this: 

[QUOTE=Sir Francis Bacon, "Novum Organum", I, LIX]
Quum autem intellectus acutior, aut observatio diligentior, eas lineas transferre velit, ut illae sint magis secundum naturam; verba obstrepunt. Unde fit, ut magnae et solennes disputationes hominum doctorum saepe in controversias circa verba et nomina desinant; a quibus (ex more et prudentia mathematicorum) incipere consultius foret, easque per definitiones in ordinem redigere.
[/QUOTE]

Rough and quick translation by me:
"And when a sharper inteligence, or a more precise observation, pretends to transfer those lines(*) so they become more according to nature, words rebel against us. For this it happens that the great and solemn debates by loremasters usually degrade into controversies about words and names. From these (as it is the custom and prudence of Mathematics) it would be wiser to start, and to follow in order by those definitions".

(*) The "lines" are the "lines" you "draw" when creating concepts in order to separate stuff that's different and join stuff that's equal.

---

### Post by worksofcraft on 2010-10-28
> **nvteighen said:**
> This thread reminds of this:

edit:

Indeed it doesn't matter if you call connected nodes "children" or "neighbors" or "adjacent". It also doesn't matter if you call the connections edges.

What does matter is that to navigate an undirected graph you actually have to assign an **artificial** direction. In the pseudo code, that is done by "coloring" the ones that you visited thus preventing the reverse direction. That algorithm is no more "general purpose" than to assign directions based on topology... such as left to right in preference to top to bottom.

The problem was originally stated in terms of identified nodes, but the indicated references discuss graphs as sets of edges (connexions). No doubt the two are completely interchangeable... but like I said I CBA to do the conversion.

---

